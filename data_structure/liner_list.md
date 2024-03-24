# **Liner List**
***
## 一. 顺序表
### 1. 顺序表定义
(1) 线性表是具有**相同**数据类型的n个**数据元素**的有限序列。\
(2) 顺序表：用**顺序存储**的方式实现线性表顺序存储。把逻辑上相邻的元素存储在**物理位置也相邻**的存储单元中。
****
### 2. 顺序表的实现
#### a. 静态分配
```
// 代码示例
#include <stdio.h>

#define MaxSize 10
typedef struct {
    int data[MaxSize]; // 用静态数组存放数据元素
    int length;        // 顺序表当前长度
}SeqList;

void InitList(SeqList &L){
    for(int i=0; i<MaxSize; i++){
        L.data[i] = 0; //若没有设置元素默认值，内存中可能会遗留“脏数据”
    }
    L.length = 0;
}

int main(){
    Seqlist L;
    InitList(L);
    // 后续操作
    return 0；
}
```

#### b.动态分配
```
//代码示例
#include <stdio.h>
#define InitSize 10

typedef struct{
    int *data;
    int MaxSize;
    int length;
}SeqList

void InitList(SeqList &L){
    L.data = (int *)malloc(InitSize * sizeof(int));
    L.length = 0;
    L.MaxSize =InitSize;
}

void IncreaseSize(SeqList &L, int len){
    int *p = L.data;
    L.data = (int *)malloc((L.MaxSize + len) * sizeof(int));
    for(int i = 0; i < L.length; i++){
        L.data[i] = p[i];
    }
    L.MaxSize = L.MaxSize + len;
    free(p);
}

int main(){
    SeqList L;
    InitList(L);
    // 往表中插入元素
    IncreaseSize(L, 5);
}
```

### 3. 顺序表的特点
(1) 随机访问；\
(2) 存储密度高；\
(3) 拓展容量不方便；\
(4) 插入、删除操作不方便，需要移动大量元素；

### 4.顺序表的插入
```
// 方法一 简易方法
void ListInsert(SeqList &L, int i, int e){
    for (int j = L.length; j>=i; j--){
        L.data[j] = L.data[j - 1];
    }
    L.data[i - 1] = e;
    L.length++;
}

// 方法二
bool ListInsert(SeqList &L, int i, int e){
    if(i < 1 || i > L.length + 1){
        return false；
    }
    if(L.length > MaxSize){
        return false;
    }
    for (int j = L.length; j>=i; j--){
        L.data[j] = L.data[j - 1];
    }
    L.data[i - 1] = e;
    L.length++;
    return true;

}
```
**时间复杂度：O(n)**

### 5. 顺序表的删除
```
// 代码示例

bool ListDelete(SeqList &L, int i, int &e){
    if(i < 1 || i > L.length){
        return false;
    }
    for(int j = i; j < L.length; j++){
        L.data[j - 1] = L.data[j];
    }
    L.length--;
    return true;
}
```
**时间复杂度：O(n)**

### 6. 顺序表的查找
#### a. 按位查找
```
ElemType GetElem(SeqList L, int i){
    return L.data[i - 1]
}
```
**按位查找时间复杂度：O(1)**

#### b. 按值查找
```
int LocalElem(SeqList L, ElemType e){
    for (int i = 0;i < L.length; i++){
        if (L.data[i] == e){
            return i + 1;
        }
    }
    return 0;

}
```

**按值查找时间复杂度：O(n)**

### 7.结构体比较
 C语言中，结构体的比较不能直接用 == 


## 二. 单链表

### 1. 单链表的定义 
每个节点除了存放数据元素之外，还有存储指向下一个节点的指针

### 2. 单链表的实现
```
struct LNode{
    ElemType data;
    struct LNode *next;
}

// 增加一个新的结点，在内存中申请一个结点所需的空间，并用指针p指向这个结点
struct LNode *p = (struct LNode *)malloc(sizeof(struct LNode));

// typedef <数据类型> <别名>
typedef struct LNode LNode;
typedef struct LNode *LinkList;
```

#### a.头插法建立单链表
```
LinkList List_HeadInsert(LinkList &L){
    LNode *s;
    int x;
    L  = (LinkList)malloc(sizeof(LNode)); // 创建头结点
    L -> next = NULL;
    scanf("%d", &x);
    while(x != 999){                      // 输入999表示结束
        s = (LNode*)malloc(sizeof(LNode));
        s->data = x;
        s->next = L->next;
        L->next = s;
        scanf("%d", &x);
    }
    return L;

} 
```
#### b. 带头结点的单链表
