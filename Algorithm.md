## 第2章：线性表

#### P17：顺序表

###### 1，删除顺序表中最小值（假设唯一），并返回被删元素的值。空出的位置由最后一个元素填补，若顺序表为空则报错

```C
int find_min(int *a, int size)
{
    int i,pos,min=MAX_INT;
    if(a == NULL || size == 0)
    {
        printf("error!\n");
        return 0;
    }
    for(i=0;i<size;i++)
    {
        if(min > a[i])
        {
            min = a[i];
            pos = i;
        }
    }
    a[pos] = a[size - 1];
	return min;
}
```

###### 2，将顺序表L的所有元素逆置，要求空间复杂度为O(1)

```C
void reverse(int *L, int size)
{
    int temp,i,mid;
    if(size%2 == 0)
		mid = size/2 - 1;
    else
        mid = size/2;
    for(i=0;i<=mid;i++)
    {
        temp = L[i];
        L[i] = L[size - i - 1];
    }
}
```

###### 3，长为n的顺序表L，删除线性表中所有值为x的元素，要求时间复杂度O(n)，空间复杂度O(1)

从头扫描数组，设置一个步长`step`，表示某个非`x`元素要往前移动的步数。`step`每碰到一次`x`就自增

```C
void delete_x(int *L, int n)
{
    int i,step=0;
    for(i=0;i<n;i++)
    {
        if(a[i] == x)
        {
            step++;
            continue;
        }
        a[i - step] = a[i];
    }
}
```

###### 4，从有序的顺序表中删除在给定值s和t之间的所有元素(s<t)，若s和t不合理，或者顺序表为空则报错

```C
void delete_order_st(int *a, int n, int s, int t)
{
    int i,start,end,step;
    if(s >= t || a == NULL || n == 0)
    {
        printf("error!\n");
        return;
    }
    for(i=0;i<n;i++)
    {
        if(a[i] > s)
        {
            start = i;
        }
        if(a[i] >= t)
        {
            end = i;
            step = end - start;
            break;
        }
    }
    for(i=end+1;i<n;i++)
    {
        a[i - step] = a[i];
    }
}
```

###### 5，从顺序表中删除在给定值s和t之间的所有元素(s<t)，若s和t不合理，或者顺序表为空则报错

同第3题

```C
void delete_disorder_st(int *a, int n, int s, int t)
{
    int i,step=0;
    if(s >= t || a == NULL || n == 0)
    {
        printf("error!\n");
        return;
    }
    for(i=0;i<n;i++)
    {
        if(a[i]>s && a[i]<t)
        {
            step++;
            continue;
        }
        a[i - step] = a[i];
    }
}
```

###### 6，从有序的顺序表中删除所有重复的元素

```C
void delete_overlap(int *a, int n)
{
    int i,step=0;
    for(i=0;i<n;i++)
    {
        if(a[i] == a[i+1])
        {
            step++;
            continue;
        }
        a[i - step] = a[i];
    }
}
```

###### 7，合并两个有序顺序表

假设为升序

```C
void combine_order(int *a, int size_a, int *b, int size_b)
{
    int i=0,j=0;
    int *result = (int *)malloc(sizeof(int) * (i+j));
    while(i<size_a && j<size_b)
    {
        if(i == size_a)
        {
            for(;j<size_b;j++)
            {
                result[i+j] = b[j];
            }
            break;
        }
        if(j == size_b)
        {
            for(;i<size_a;i++)
            {
                result[i+j] = a[i];
            }
            break;
        }
        if(a[i]<b[j])
        {
            result[i+j] = a[i];
            i++;
        }
        else
        {
            result[i+j] = b[j];
            j++;
        }
    }
}
```

###### 8，将一维数组A[m+n]中的$a_1-a_m$，$b_1-b_n$交换位置

先将`A[m+n]`逆置，再将前`n`个元素和后`m`个元素逆置

$ab\to a^{-1}b\to a^{-1}b^{-1}\to (a^{-1}b^{-1})^{-1}\to ba$

###### 9，线性表升序，设计一个算法在最小时间内查找数值为x的元素，若找到则将其与后继元素交换；否则将其插入到表中适当位置

折半查找

######  11，等长（长度为L）的两个升序序列A和B，求总的中位数

类似于归并，求第$L$个数的大小

答案：分治法，各求中位数然后各丢弃一半

```C
int find_mid(int *A, int *B, int L)
{
    int i,left=0,right=0,result;
    for(i=0;i<L;i++)
    {
        if(A[left]<B[right])
        {
            left++;
            result = A[left];
        }
        else
        {
            right++;
            result = B[right];
        }
    }
    return result;
}
```

###### 13，给定长度为n的数组，求该数组中未出现的正整数

空间换时间，定义数组`B[n]`记录`A`中`1-n`的数字出现的情况

#### P37：链表

###### 1，设计递归算法，删除不带头结点的单链表L的所有值为x的结点

```C
LinkNode* fun(LinkNode *a, int x)
{
    if(a == NULL)
    {
        return NULL;
    }
    else if(a->data == x)
    {
        return fun(a->next, x);
    }
    else
    {
        a -> next = fun(a->next, x);
        return a;
    }
}
int main(void)
{
    head = fun(head, x);
}
```

###### 2，删除带头结点的单链表L的所有值为x的结点

```C
void delete_x(LinkList L, int x)
{
    LinkNode *cur_node = L -> next;
    LinkNode *pre_node = L;
    while(cur_node != NULL)
    {
        if(cur_node->data != x)
        {
            pre_node = cur_node;
            cur_node = cur_node -> next;
        }
        else
        {
            pre_node -> next = cur_node -> next;
            free(cur_node);
            cur_node = pre_node -> next;
        }
    }
}
```

###### 3，L为带头结点的单链表，从尾到头输出每个结点的值

用递归的方式

```C
void print_reverse(Linklist L)
{
    if(L->next == NULL)
    {
        output(L->data);
        return;
    }
    else
    {
        print_reverse(L->next);
        output(L->data);
        return;
    }
}
```

###### 4，L为带头结点的单链表，删除一个最小值结点（最小值唯一）

```C
void delete_min(Linklist L)
{
    Linknode *cur_pre = L;
    Linknode *cur = L -> next;
    Linknode *min = cur;
    Linknode *min_pre = cur_pre;
    while(cur != NULL)
    {
        if(min->data > cur->data)
        {
            min = cur;
            min_pre = cur_pre;
        }
        cur_pre = cur;
        cur = cur -> next;
    }
    min_pre -> next = min -> next;
    free(min);
}
```

###### 5，将带头结点的链表就地逆置

将头结点去掉，然后使用尾插法构造链表

###### 6，排序带头结点的单链表L使其升序

使用冒泡排序

```C
void sort_list(Linklist L)
{
    if(L->next == NULL || L->next->next == NULL)
    {
        return;
    }
    int i,j,temp,lenth=0;
    Linknode *cur = L;
    Linknode *pre = L -> next;
    while(cur->next != NULL)
    {
        lenth++;
        cur = cur -> next;
    }
    for(i=0;i<lenth;i++)
    {
        pre = L -> next;
        cur = pre -> next;
        for(j=0;j<lenth-i;j++)
        {
            if(pre->data > cur->data)
            {
                temp = cur -> data;
                cur->data = pre->data;
                pre->data = temp;
            }
            pre = pre -> next;
            cur = cur -> next;
        }
    }
}
```

###### 7，删除链表中特定范围的结点

略

###### 8，寻找两个链表的公共结点

两个链表若有公共结点，则一定是“Y”字型

###### 9，按升序输出链表

按照题6先排序后输出

###### 10，将一个带头结点的链表分解为两个，按照奇偶分开



#### P142 二叉树

###### 8，二叉树链式存储，计算其双分支结点个数

广度优先，检查左右孩子是否都不为空

```C
int TwoBranch(BiTree T)
{
    BiTNode x;
    int count = 0;
    InitQueue(&Q);
    if(T==NULL)
        return 0;
    EnQueue(&Q, T);
    while(!QueueEmpty(Q))
    {
        DeQueue(&Q, &x);
        count++;
        if((x->lchild==NULL) || (x->rchild==NULL))
            count--;
        if(x->lchild!=NULL)
            EnQueue(&Q, x->lchild);
        if(x->rchild!=NULL)
            EnQueue(&Q, x->rchild);
    }
    return count;
}
```

法二，递归

```C
if(b == NULL)
    f(b) = 0;
if((b->lchild!=NULL) && (b->rchild!=NULL))
    f(b) = f(b->lchild) + f(b->rchild) + 1;
else
    f(b) = f(b->lchild) + f(b->rchild);
```

###### 9，二叉树链式存储，将所有结点的左右子树交换

递归

```C
BiTree Exchange(BiTree T)
{
    if(T == NULL)
        return NULL;
    BiTree temp;
    temp = Exchange(T -> rchild);
    T -> rchild = Exchange(T -> lchild);
    T -> lchild = temp;
    return T;
}
void main(void)
{
    Exchange(T);
}
```

###### 10，求先序遍历序列第k个结点的值

先序遍历非递归实现

```C
void VisitK(BiTree T, int k)
{
    BiTree p = T;
    int count = 0;
    InitStack(&S);
    while((p != NULL) || StackEmpty(S))
    {
        if(p != NULL)
        {
            count++;
            if(count == k)
                return p->data;
            Push(&S, p);
            p = p -> lchild;
        }
        else
        {
            Pop(&S, p);
            p = p -> rchild;
        }
    }
}
```

法二，递归实现

```C
int count = 0;
void Visitk2(BiTree T)
{
    if(T == NULL)
    	return;
    else
    {
        count++;
        if(count == k)
        {
            return T->data;
        }
        Visitk2(T->lchild);
        Visitk2(T->rchild);
    }
}
```

###### 11，删去值为x的结点的子树，并释放对应空间

递归

```C
void DeleteX(BiTree T, int x)
{
    if(T == NULL)
        return;
    if(T -> data == x)
    {
        free(T);
        return;
    }
    else
    {
        DeleteX(T->lchild);
        DeleteX(T->rchild);
    }
}
```

###### 12，输出值为x的结点的所有祖先，假设值为x的结点不多于一个

深度优先搜索

非递归后序遍历，当访问到`x`时，栈中所有结点都是它的祖先

###### 13，给定根结点和两个结点的指针p和q，寻找其最近的公共祖先r

同12题，非递归后序遍历得到两个栈，然后同步出栈，直到出栈元素相同即为`r`

###### 14，求非空二叉树b的宽度

```C
struct Queuenode
{
    int depth;
    BiTree node;
}
int width(BiTree b)
{
    InitQueue(&Q);
    int num[N+1] = {0}, max_width = -1;
    QueueNode temp,cur;
    temp.node = b;
    temp.depth = 1;
    num[1] = 1;
    EnQueue(&Q, temp);
    while(!QueueEmpty(Q))
    {
        DeQueue(&Q, &temp);
        if(temp.node->lchild != NULL)
        {
            cur.node = temp.node->lchild;
            cur.depth = temp.depth + 1;
            num[cur.depth]++;
            EnQueue(&Q, cur);
        }
        if(temp.node->rchild != NULL)
        {
            cur.node = temp.node->rchild;
            cur.depth = temp.depth + 1;
            num[cur.depth]++;
            EnQueue(&Q, cur);
        }
    }
    for(int i=0;i<N+1;i++)
    {
        if(max_width < num[i])
        {
            max_width = num[i];
        }
    }
    return max_width;
}
```

###### 16，将二叉树的叶结点从左到右连成单链表

中序遍历即可

###### 17，判断两棵树是否相似，相似定义为T1和T2都是空树或者只有一个根结点，或者T1和T2的左子树相似且右子树相似

递归判断

```C
bool isSimilar(BiTree T1, BiTree T2)
{
    bool result = false;
    if((T1==NULL)&&(T2==NULL))
    	result = true;
    if((T1->lchild==NULL&&T1->rchild==NULL) && (T2->lchild==NULL&&T2->rchild==NULL))
        result = true;
    else
        result = isSimilar(T1->lchild, T2->lchild) && isSimilar(T1->rchild, T2->rchild);
    return result;
}
```

#### P167，树和森林

###### 5，求孩子兄弟表示法存储的森林的叶子结点总数

遍历整棵树，左孩子为空符合条件

```C
int Count(BiTree T)
{
    if(T == NULL)
        return 0;
    int result = 0;
    InitQueue(&Q);
    BiTree p;
    EnQueue(&Q, T);
    while(!QueueEmpty(Q))
    {
        DeQueue(&Q, p);
        if(p->lchild == NULL)
        	result++;
        else
            EnQueue(&Q, p->lchild);
        if(p->rchild != NULL)
            EnQueue(&Q, p->rchild);
    }
    return result;
}
```

###### 6，用递归法求孩子兄弟表示法的数的深度

```C
if(p == NULL)
    f(p) = 0;
else if(p->left == NULL)
    f(p) = 1;
else
    f(p) = max{f(p->left)+1, f(p->left->right)};
```

###### 7，根据层次序列构造孩子兄弟树

递归实现

```C
void GenTree(Queue &Q, BiTree T)
{
    BiTree p;
    DeQueue(&Q, p);
    if(p.dgree == 0)
    {
        T = p;
        return;
    }
    else
    {
        GenTree(&Q, T->lchild);
        for(int i=1;i<p.dgree;i++)
        {
            GenTree(&Q, T->rchild);
        }
    }
}
```

#### P185，二叉排序树

###### 6，判断给定二叉树是否为排序二叉树

递归判断

```C
bool isSorted(BiTree T)
{
    if(T == NULL)
        return true;
    if((T->lchild==NULL) && (T->rchild==NULL))
        return true;
    bool result = true;
    if((T->lchild!=NULL) && (T->data < T->lchild->data))
        result = false;
    if((T->rchild!=NULL) && (T->data > T->rchild->data))
        result = false;
    return result;
}
```

###### 7，求出指定结点在二叉排序树中的层次

在搜索过程中，只会向下搜索，因此计算对比次数即可

```C
int Level(BiTree T, int x)
{
    BiTree p = T;
    int level = 1;
    while(p->data != x)
    {
        level++;
        if(x < p->data)
            p = p->left;
        else
            p = p->right;
    }
    return level;
}
```

###### 8，判断二叉树是否平衡

递归判断，计算左右子树的高度

```C
bool flag = true;
int Height(BiTree T)
{
    if((T==NULL) || (!flag))
        return 0;
    int result = 1;
    int left = Height(T->lchild);
    int right = Height(T->rchild);
    int diff = left - right;
    if((diff>1) || (diff<-1))
    {
        flag = false;
        return 0;
    }
    if(left > right)
        result += left;
    else
        result += right;
    return result;
}
```

###### 9，求给定二叉排序树的最大最小关键字

一直向左向右搜索即可

```C
struct Answer
{
    int max;
    int min;
}
struct Answer FindMaxMin(BiTree T)
{
    BiTree left=T,right=T;
    struct Answer ans;
    ans.max = T->data;
    ans.min = T->data;
    while((left->lchild!=NULL) || (right->rchild!=NULL))
    {
		if(left->lchild!=NULL)
        {
            left = left -> lchild;
            ans.min = left -> data;
        }
        if(right->rchild!=NULL)
        {
            right = right -> rchild;
            ans.max = right -> data;
        }
    }
    return ans;
}
```

###### 10，从大到小输出二叉排序树不小于k的所有值

注意到二叉排序树的中序遍历即为从小到大的输出，使用两个栈来实现。假设栈不空。

```C
void Printk(BiTree T)
{
    BiTree p = T;
    InitStack(&S1);
    InitStack(&S2);
    Push(&S1, p);
    while(p||!StackEmpty(S1))
    {
        if(p)
        {
            Push(&S1, p);
            p = p -> lchild;
        }
        else
        {
            Pop(&S1, p);
            Push(&S2, p);
            if(Top(S2)->data > k)
                break;
            p = p -> rchild;
        }
    }
    while(!StackEmpty(S2))
    {
        Pop(&S2, p);
        Visit(p);
    }
}
```

###### 12，递归实现，在n个结点的排序二叉树查找第k小的元素。二叉排序树的结点有count域，保存以它为根的子树结点个数。要求复杂度$O(\log_2n)$

#### P211，图

###### 4，从图的邻接表表示转换成矩阵表示

不妨设为有向带权图

```C
void Convert(ALGraph src, MGraph *dst)
{
    dst -> vexnum = src.vexnum;
    dst -> arcnum = src.arcnum;
    struct ArcNode *p;
    for(int i=0;i<src.vexnum;i++)
    {
        dst -> Vex[i] = src.vertices[i].data;
        p = src.vertices[i].first;
        while(p != NULL)
        {
            dst -> Edge[i][p->adjvex] = p -> info;
            p = p -> next
        }
    }
}
```



