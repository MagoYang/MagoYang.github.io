# MagoYang.github.io
Mycode~博客

1.//字符串连接函数 strcat
//原型strcat(char[],const char[])
#include <stdio.h>
#include <assert.h>
//void my_strcat(char strdest[], const char strsrc[]);
char * my_strcat(char *strdest, const char *strsrc)
{
	assert(strdest);
	assert(strsrc);
	char *ret = strdest;
	while (*strdest)
	{
		strdest++;
	}
	while (*strdest++ = *strsrc++)
	{
		;         //为了保证循环的继续 必须有！
	}
	return ret;
}
int main()
{
	char dest[20] = "this is ";
	char src[] = "my_strcat";
	my_strcat(dest, src);
	printf("%s\n", dest);   //%s 输出一个字符串
	system("pause");
	return 0;

}


2.//strstr函数   思路：在字符串s1中查找s2的第一次出现的位置，否则返回null
//原型 ： char *strstr(char *str1, const char *str2);
# include <stdio.h>
//#include <string.h>
char * my_strstr(char *s1, const char *s2)  
{  
    int n=0;  
    if (*s2)  
    {  
        while (*s1)  
        {  
			if (*(s1 + n) == *(s2 + n))
			{
				if (*(s2 + n + 1) == null)
				{
					return (char *)s1;
				}
			   n++;
			}
           /* for (n=0; *(s1 + n) == *(s2 + n); n++)  
            {  

                if (*(s2 + n + 1)==null)  
                    return (char *)s1;  
            }  */
            s1++;    //只要第n次不相等时，就进行s1++，直到满足条件时开始执行下一条语句
        }  
        return null;  
    }  
    else  
        return (char *)s1;
}

int main()
{
	char*str1 = "1233456";
	char* str2 = "345";
	char*s=my_strstr(str1, str2);
	printf("%s\n", s);
	system("pause");
	return 0;
}


3.模拟实现strcmp 
				/*C/C++函数，比较两个字符串.设这两个字符串为str1，str2，若str1 == str2，则返回零；若str1>str2，则返回正数；
				若str1<str2，则返回负数。*/
4.模拟实现memcpy  c和c++使用的内存拷贝函数，
                memcpy函数的功能是从源src所指的内存地址的起始位置开始拷贝n个字节到目标dest所指的内存地址的起始位置中。
//5.模拟实现memmove


#include <stdio.h>
#include <assert.h>
int  my_strcmp(const char* str1,const char* str2) //字符串比较函数
{
	//assert(str1);
	//assert(str2);
	const char *s1 = str1;
	const char *s2 = str2;
	while (*s1||*s2 )

	{
		if (*s2 == '\0' || *s1 > *s2)
		{
			return 1;
		}
		else if (*s1 == '\0' || *s1 < *s2)
		{
			return -1;
		}
		else
		{
			return 0;
		}
		s1++;
		s2++;
	}
		return 0;  // 是在两个字符串都为空时返回值 0
}

void* my_memcpy( void * dest,void *src,size_t n)//不相干内存
{
	assert(dest);
	assert(src);
	char * ret = dest;
	char *pdest = (char *)dest;
	char *psrc = (char *)src;
	while (n-- > 0)
	{
		*pdest++ = *psrc++;
	}
	return ret;
}

void* my_memmove(void *dest,const void *src,size_t n)//相干不相干内存都可
{
	assert(dest);
	assert(src);
	char *pdest = (char *)dest;
	char *psrc = (char *)src;
	char *ret = dest;
	if ((src < dest) && (pdest < psrc + n))   //内存重复时
	{
		pdest =  pdest + n - 1;
		psrc =  psrc + n - 1;
		while (n-->0)   
		{
			*pdest = *psrc;
			pdest--;
			psrc--;
			//--pdest;  //都可以
			//--psrc;
		}


	}
	else
	{
		while (n-- > 0)
		{
			*pdest++ = *psrc++;
		}
	}
		
	return ret;
}
void Test1()
{
	char *str1 = "12345";
	char *str2 = "456";
	char *tmp = my_strcmp(str1, str2);
	printf("%d\n", tmp);
}
void Test2()
{
	char * str1 = "abcdefg";
	char arr[20];
	memset(arr, 0, sizeof(arr));     //将内存设置初始化为0
	char* tmp = my_memcpy(arr, str1, 5);
	printf("%s\n", tmp);
}
void Test3()
{
	char str[] = "123456789";
	my_memmove(str + 4, str + 3, 3);
	puts(str);

}
int main()
{
	//Test1();
	//Test2();
	Test3();
	system("pause");
	return 0;
}

7.冒泡排序  方法：1.数组 2.指针
# include  <stdio.h>
//# define N  10
void bubbleSort(int arr[], int size)
{
	int i = 0;
	int j = 0;
	for (i = 0; i < size - 1;i++)
	for (j = 0; j < size - 1 - i; j++)
	{
		if (arr[j]>arr[j + 1])
		{
			int tmp = arr[j];
			arr[j] = arr[j + 1];
			arr[j + 1] = tmp;
		}
	}
}
	

int main()
{
	int i=0;
	int arr[] = { 9,8,7,6,5,4,3,2,1,0 };
	int size = sizeof(arr) / sizeof(arr[0]);
	 bubbleSort(arr,size);
	 for (i = 0; i < size; i++)
	 {
		 printf(" %d ", arr[i]);
	 }
	system("pause");
	return 0;
}

8.# include  <stdio.h>
//# define N  10
void bubbleSort(int* p, int size)
{
	int i = 0;
	int j = 0;
	for (i = 0; i < size - 1; i++)
	for (j = 0; j < size - 1 - i; j++)
	{
		if (*(p+j)>*(p+j+1))
		{
			int tmp = *(p + j);
			*(p + j) = *(p + j + 1);
			*(p + j + 1) = tmp;
		}
	}
}


int main()
{
	int i = 0;
	int arr[] = { 9, 8, 7, 6, 5, 4, 3, 2, 1, 0 };
	int size = sizeof(arr) / sizeof(arr[0]);
	int *p = arr;                 //数组名指数组的起始位置
	bubbleSort( p, size);
	for (i = 0; i < size; i++)
	{
		printf(" %d ", *(p+i));
	}
	system("pause");
	return 0;
} 
9.实现一个函数，可以左旋字符串中的k个字符。
AABCD左旋一个字符得到ABCDA
AABCD左旋两个字符得到BCDAA
# include <stdio.h>
# include <assert.h>
# include <string.h>
char * LeftHand(char *str1, char * str2, int k)  //开辟一个新空间str2，先存入k+1后的部分，再存k之前的部分
{
	assert(str1);
	assert(str2);
	char*ret = str2;
	char * s1 = str1 + k;  //  从k+1的位置开始将其后面部分存入str2；
	while (*s1)
	{
		*str2++ = *s1++;
	}
	s1 = str1;    //存完后将指针s1调至str1开始，逆转存剩余部分
	while (k)
	{
		*str2++ = *s1++;
		k--;
	}
	*str2 = '\0';//将str2的末尾给字符‘\0’
	return ret;
}

10.模拟实现strchr和strrchr
# include <stdio.h>
 char *my_strchr(const char *str, char ch)
{
	if (*str)
	{
		while (*str != '\0'&&*str != ch)
		{
			++str;      //str++;
		}
		return *str == ch ? str : null;
	}
	else
		return null;

}
int  my_strchr(const char *str, int ch)
{
	int count = 1;
	if (*str)
	{
		while (*str != '\0'&&*str != ch)
		{
			++str; //str++;
			++count;//count++;
		}
		return *str == ch ? count : null;
	}
	else
		return null;

}
char* my_strrchr(const char *str, char ch)
{
	const char *ptr = null;
	
	while (*str != ch)
	{
		++str;
		if (*str == ch&&*str!='\0')
		{
			ptr = str;
			++str;
		}
		else if (*str == '\0')
		{
			return  ptr;
		}
	}
	
}

test1()
{
	char arr[] = "welcome to this world!";
	int ret = my_strchr(arr, 'o');
	printf("ret=%d", ret);
}
test2()
{
	char arr[] = "welcome to this world!";
	char* ret = my_strrchr(arr, 'o');
	printf("ret=%s", ret);
}
int main()
{
	//test1();
	test2();
	system("pause");
	return 0;
}

11.模拟实现strrstr
# include <stdio.h>
char *my_strrstr(const char *s1, const char *s2)
{
	char *last = NULL;
	char *current = NULL;
	if (*s2)  //只有在s2不为空时才查找，若s2为空，返回NULL
	{
		current = strstr(s1, s2);  //查找s2在s1中第一次出现的位置
		while (current != NULL)
		{
			last = current;
			current = strstr(last + 1, s2);
		}
	}
	return last;
}
int main()
{
	char *str1 = "abcdefabcdef";
	char *str2 = "bcd";
	char * ret = my_strrstr(str1, str2);
	printf("ret=%s", ret);
	system("pause");
	return 0;
}


12.c实现单链表

#include <stdio.h>
#include <stdlib.h>
#include <assert.h>
typedef int DataType;
typedef struct SListNode     /* 定义单链表结点类型 */
{
	DataType  data;

	struct SListNode *next;
}SListNode;
//////////有关操作：///////////////////////////////////////
void InitList();/*初始化线性表*/
SListNode *CreateNode(DataType x);/*新建结点*/
void PrintList(SListNode*&pHead); /*打印链表*/
SListNode * Find(SListNode*& pHead, DataType x);
void PushBack(SListNode*& pHead, DataType x);
void Popback(SListNode*& pHead);
void PushFront(SListNode*& pHead, DataType x);
void PopFront(SListNode * & pHead);
void Insert(SListNode * pos, DataType x);/*插入节点*/
void Erase(SListNode * pos); /*删除节点*/

void InitList()
{
	SListNode* pHead;
	pHead = (SListNode*)malloc(sizeof(SListNode));
	if (pHead == NULL)
	{
		printf("申请空间失败\n");
	}
	pHead->next = NULL;
}

void PrintList(SListNode* &pHead)
{
	SListNode* cur = pHead;
	while (cur)
	{
		printf("%d->", cur->data);
		cur = cur->next;
	}
	printf("NULL\n");
}
SListNode *CreateNode(DataType x)

{

	SListNode *tmp = (SListNode *)malloc(sizeof(SListNode));
	tmp->data = x;
	tmp->next = NULL;
	return tmp;
}
void PushBack(SListNode* & pHead, DataType x)//1.空 2.非空
{
	if (pHead == NULL)
	{
		pHead = CreateNode(x);
	}
	else
	{
		SListNode* tail = pHead;
		while (tail->next != NULL)
		{
			tail = tail->next;
		}
		tail->next = CreateNode(x);
	}

}
void Popback(SListNode*& pHead)//1.空2.一个节点3.多个节点
{
	if (pHead==NULL)
	{
	return;
	}
	else if (pHead->next == NULL)
	{
		free(pHead);
		pHead = NULL;
	}
	else
	{
		SListNode* tail = pHead;
		SListNode* prev = NULL;
		while (tail->next)
		{
			prev = tail;
			tail = tail->next;
		}
		prev->next=NULL;
		free(tail);
	}
}


void PushFront(SListNode*& pHead, DataType x) //1.空2.非空
{
	if (pHead == NULL)
	{
		pHead = CreateNode(x);
	}
	else
	{
		SListNode*tmp = CreateNode(x);
		tmp->next = pHead;
		pHead = tmp;
	}
}


void PopFront(SListNode * & pHead)  //1.空2.一个节点3.多个节点
{
	if (pHead == NULL)
	{
		return;
	}
	else if (pHead->next = NULL)
	{
		free(pHead);
		pHead = NULL;
	}
	else
	{
		SListNode*tmp = pHead;
		pHead = tmp->next;
		free(tmp);
	}
}


SListNode * Find(SListNode*& pHead, DataType x)  //1.在其中2.不在其中
{
	SListNode*cur = pHead;
	while (cur)
	{
		/*if (cur->data != x)
		{
			cur = cur->next;
		}
		return cur;  */   //错的！！！！！！！！
		if (cur->data == x)
		{
			return cur;
		}
		cur = cur->next;


	}
	return NULL;
}
void Insert(SListNode * pos, DataType x)  //非空
{
	assert(pos);
	SListNode* tmp = CreateNode(x);
	tmp->next = pos->next;
	pos->next = tmp;
}

void Erase(SListNode *& pHead,SListNode * pos)
{
	assert(pos); 
	assert(pHead);
	
	if (pHead == pos)
	{
		pHead = pHead->next;
		free(pos);

	}
	else
	{

		SListNode * prev = pHead;
		while (prev->next != pos)
		{
			prev = prev->next;
		}
		prev->next = pos->next;
		free(pos);
	}

}
13.单链表有关题目
///////////1.删除一个无头单链表的非尾节点////////////////
void DelNoTailNode(SListNode * pos)
{
	assert(pos);
	assert(pos->next);
	SListNode* del = pos->next;
	SListNode* next = del->next;
	pos->data = del->data;
	pos->next = next;
	free(del);
}

///////////2.在无头单链表的非头结点前面插入一个节点///////
void InsertNFNode(SListNode* pos,DataType x)
{
	assert(pos);
	SListNode* tmp = CreateNode(x);
	tmp->next = pos->next;
	pos->next = tmp;
	DataType curdata = pos->data;
	pos->data = tmp->data;
	tmp->data = curdata;

}

////////////3.查找单链表的中间节点，要求只遍历一遍////////////
SListNode* FindMidNode(SListNode*& pHead)
{
	SListNode *slow = pHead;
	SListNode*fast = pHead;
	while (fast&&fast->next)
	{
		slow = slow->next;
		fast = fast->next->next;
	}
	return  slow;
}

//////////////4.查找单链表的倒数第k个节点，要求只遍历一次////////
SListNode * FindKNode(SListNode *&pHead,int k)
{
	SListNode* slow = pHead;
	SListNode* fast = pHead;
	while (fast&& k--)
	{
		fast = fast->next;
		if (fast == NULL)
		{
			return NULL;
		}
	}
	while(fast)
	{
		slow = slow->next;
		fast = fast->next;
	}
	return slow;
}

////////////////5.从尾到头打印单链表////////////////////////
void PrintTTHList(SListNode *& pHead)
{
	if (pHead == NULL)
	{
		return ;
	}
	else
	{
		PrintTTHList(pHead->next);
		printf("%d-", pHead->data);
		
	}
}

/////////////////6.逆置单链表/////////////////////////////////
SListNode* Reverse(SListNode *&pHead)
{
	SListNode* cur = pHead;
	SListNode* newhead = NULL;
	while (cur)
	{
		SListNode* tmp = cur;
		cur = cur->next;
		tmp->next = newhead;
		newhead = tmp;
	}
	return newhead;
}

void Test1()
{
	SListNode*SList = NULL;
	PushBack(SList, 1);
	PushBack(SList, 2);
	PushBack(SList, 3);
	PushBack(SList, 4);

	PrintList(SList);

	PushFront(SList, 5);
	PushFront(SList, 6);
	PushFront(SList, 7);
	PushFront(SList, 8);
	PushFront(SList, 9);

	PrintList(SList);

	PopFront(SList);
	PopFront(SList);
	PopFront(SList);
	PopFront(SList);
	PopFront(SList);

	PrintList(SList);

	Popback(SList);
	Popback(SList);
	Popback(SList);
	Popback(SList);
	Popback(SList);
	PrintList(SList);
}
void Test2()
{
	SListNode*SList = NULL;
	PushBack(SList, 1);
	PushBack(SList, 2);
	PushBack(SList, 3);
	PushBack(SList, 4);

	PrintList(SList);

	SListNode*pos = Find(SList, 1);
	Insert(pos, 50);
	PrintList(SList);

	pos = Find(SList, 3);
	Insert(pos, 60);
	PrintList(SList);

	pos = Find(SList, 4);
	Insert(pos, 70);
	PrintList(SList);

	pos = Find(SList, 4);
	Erase(SList, pos);
	PrintList(SList);

	pos = Find(SList, 1);
	Erase(SList, pos);
	PrintList(SList);
}
void Test3()
{
	SListNode*SList = NULL;
	PushBack(SList, 1);
	PushBack(SList, 2);
	PushBack(SList, 3);
	PushBack(SList, 4);

	PrintList(SList);

	SListNode*pos = SList; //Find(SList, 2);
	DelNoTailNode(pos);
	PrintList(SList);

	pos = Find(SList, 2);
	InsertNFNode(pos, 20);
	PrintList(SList);
}

void Test4()
{
	SListNode*SList = NULL;
	PushBack(SList, 1);
	PushBack(SList, 2);
	PushBack(SList, 3);
	PushBack(SList, 4);
	PrintList(SList);
	//PrintTTHList(SList);

	SList=Reverse(SList);
	PrintList(SList);

	
	//SListNode*pos = FindMidNode(SList);
	//printf("%d\n", pos->data);
	/*SListNode*pos = FindKNode(SList, 1);
	printf("%d\n", pos->data);
	pos = FindKNode(SList, 9);
	printf("%d\n", pos->data);*/
}

int main()
{
    //InitList();
	//Test1();
	//Test2();
	//Test3();
	Test4();
	system("pause");
	return 0;
}
	

14.通讯录
# include <stdio.h>
# include <string.h>
enum {EXIT,ADD,DEL,MODIFY,FIX,SHOW,CLEAR,SORT};
typedef struct People
{
	char name[20];
	char sex[2];
	int age;
	int tel[11];
	char idd[40];
}Peo;

typedef struct Contact
{
	Peo dhb[1000];
	int count;
}Con, *pcon;
void init(pcon ppcon);
void add(pcon ppcon);
void del(pcon ppcon);
void modify(pcon ppcon);
void fix(pcon ppcon);
void show(pcon ppcon);
void clear(pcon ppcon);
void sort(pcon ppcon);
int search(pcon con, char *pname)
{
	for (int i = 0; i < con->count; i++)
	{
     if (strcmp(con->dhb[i].name, pname) == 0)
	  {
		return i;
	  }
	}
	return -1;
}
void init(pcon ppcon)    // 初始化
{
	ppcon->count = 0;
}
void add(pcon ppcon)
{

	printf("请输入姓名：");
	scanf("%s", ppcon->dhb[ppcon->count].name);
	printf("请输入性别："); 
	scanf("%s", ppcon->dhb[ppcon->count].sex);
	printf("请输入年龄：");
	scanf("%d", &ppcon->dhb[ppcon->count].age);//&
	printf("请输入电话：");
	scanf("%s", ppcon->dhb[ppcon->count].tel);
	printf("请输入地址：");
	scanf("%s", ppcon->dhb[ppcon->count].idd);
	ppcon->count++;
	printf("添加联系人成功ok！\n");
}
void del(pcon ppcon)
{
	int ret;
	int n;
	char name[20];
	printf("请输入要删除人的姓名：");

	scanf("%s", name);
	ret = search(ppcon, name);
	if (ret != -1)
	{
		printf("此联系人存在\n");
		printf("是否确定要删除此联系人\n");
		printf("是请按1，否请按0\n");
		scanf("%d", &n);
		if (n == 1)
		{
			for (int i =ret; i < ppcon->count; i++)
			{
				ppcon->dhb[i] = ppcon->dhb[i + 1];
			}
			printf("删除成功");
			ppcon->count--;
		}
		else if (n == 0)
			printf("删除失败");
	}
}
void modify(pcon ppcon)
{
	char name[20];
	printf("请输入要查找的人的姓名：");
	scanf("%s", name);
	int ret = search(ppcon, name);
	if (ret != -1)
	{
		printf("此联系人存在\n");
		printf("%s", ppcon->dhb[ret].name);
		printf("%s", ppcon->dhb[ret].sex);
		printf("%d", ppcon->dhb[ret].age);
		printf("%s", ppcon->dhb[ret].tel);
		printf("%s", ppcon->dhb[ret].idd);
	}
	else
	{
		printf("此联系人不存在\n");
	}
}
void fix(pcon ppcon)
{
	char name[20];
	printf("请输入要修改的人的姓名：");
	scanf("%s", name);
	int ret = search(ppcon, name);
	if (ret != -1)
	{
		printf("此联系人存在\n");
		printf("姓名修改成：");
		scanf("%s", ppcon->dhb[ret].name);
		printf("性别修改成：");
		scanf("%s", ppcon->dhb[ret].sex);
		printf("年龄修改成：");
		scanf("%d", &ppcon->dhb[ret].age);
		printf("电话修改成：");
		scanf("%s", ppcon->dhb[ret].tel);
		printf("地址修改成：");
		scanf("%s", ppcon->dhb[ret].idd);
		printf("修改成功\n");
	}
	else
		printf("此人不存在\n");

}
void show(pcon ppcon)

{
	printf("输出所有人信息：");
	for (int i = 0; i < ppcon->count; i++)
	{
		printf("%s\n", ppcon->dhb[i].name);
		printf("%s\n", ppcon->dhb[i].sex);
		printf("%d\n", ppcon->dhb[i].age);//此处不许用再取地址，因为ppcon->dhb[i].age已经是int型的数字，加上&则是取12的地址了
		printf("%s\n", ppcon->dhb[i].tel);
		printf("%s\n", ppcon->dhb[i].idd);
	}
	printf("\n");
}
void clear(pcon ppcon)
{
	printf("清空所有联系人：");
	/*for (int i = 0; i < p->count; i++)
	{
		p->dhb[i] = p->dhb[i + 1];
	}*/
	ppcon->count = 0;

}
void sort(pcon ppcon)
{
	for (int i = 0; i < ppcon->count - 1; i++)
	{
			for (int j = 0; j < ppcon->count - 1 - i; j++)
		{
				if (strcmp(ppcon->dhb[j].name, ppcon->dhb[j + 1].name)>0)
			{
				Peo tmp;
				tmp = ppcon->dhb[j];
				ppcon->dhb[j] = ppcon->dhb[j + 1];
				ppcon->dhb[j + 1] = tmp;
			}
		}
	
	}
	show(&ppcon);
}
void menu()

{
	printf("****      menu     ****\n");
	printf("****1.add  2.delete****\n");
	printf("****3.modify 4.fix   ****\n");
	printf("****5.show 6.clear ****\n");
	printf("****7.sort 0.exit  ****\n");
}
void test()
{
	Con con;
	init(&con);
	int input = 1;
	
	while (input)
	{
		menu();
		printf("请选择操作选项：");
		scanf("%d", &input);
		switch (input)
		{
		case ADD:add(&con); break;
		case DEL:del(&con); break;
		case MODIFY:modify(&con); break;
		case FIX:fix(&con); break;
		case SHOW:show(&con); break;
		case CLEAR:clear(&con); break;
		case SORT:sort(&con); break;
		case EXIT:exit(1); break;
		}
	}
}
int main()
{
	test();
	system("pause");
	return 0;
}
15.Queue 队列
#define _CRT_SECURE_NO_WARNINGS 1
//用链表实现队列
# include <assert.h>
# include <iostream>
using namespace std;

template <class T>
struct Node
{
	T _data;            //指针存储域
	Node<T>* _next;     //结点指针域，指向下一个节点
	Node(const T&x)    //有参构造函数
		:_data(x)   //冒号之后及大括号之间叫初始化列表：开辟空间并同时初始化变量
		, _next(NULL)
	{}
};
template <class T>  //须有，否则编译不通过
class Queue
{
public:
	Queue()          
		:_head(NULL)
		, _tail(NULL)
		, _size(0)

	{}
	~Queue()              
	{}
public:
	void Push(const T& x)
	{
		if (_head == NULL)
		{
			_head = _tail = new Node<T>(x);
		}
		else
		{
			_tail->_next = new Node<T>(x);
			_tail = _tail->_next;
		}
		++_size;

	}
	void Pop()    //只是从头pop节点，因为队列是尾进头出；
	{
		assert(_head);
		if (_head == _tail)
		{
			delete _head;
			_head = _tail = NULL;
		}
		else
		{
			Node<T>* _del = _head;
			_head = _head->_next;
			delete _del;
		}
		--_size;
	}
	bool Empty()
	{
		if (1)
			return _head == NULL;
	}
	T& Front()
	{
		assert(_head);
		return _head->_data;
	}
	T& Back()
	{
		assert(_tail);
		return _tail->_data;
	}
	size_t Size()
	{
		return _size;
	}
protected:
	Node<T> * _head;
	Node<T> * _tail;
	size_t _size;
};


void TestQueue()
{
	Queue<int> q1;
	q1.Push(1);
	q1.Push(2);
	q1.Push(3);
	q1.Push(4);
	while (!q1.Empty())
	{
		//cout << q1.Back() << " ";     //此处不能用back，否则违反了队列的特性
		cout << q1.Front() << " ";
		q1.Pop();
	}

}

int main()
{
	TestQueue();
	system("pause");
	return 0;
}
16.Stack  栈
//用数组实现栈
# include <iostream>
using namespace std;
template <class T>
class Stack
{
public:
	Stack()
		: a(NULL)
		,top(0)
		, capacity(0)
	{}
	~Stack()
	{
		if (a)
		{
			delete[] a;   //撤销数组的空间
		}
	}
public:
	void Push(const T& x)
	{
		Checkcapacity();
		a[top++] = x;


	}
	void Pop()
	{
		if (top>0)
			--top;


	}
	bool Empty()
	{
		if (top == 0)
			return true;
		else
			return false;
	}
	size_t Size()//当前栈中元素的个数
	{
		return top;
	}
	T& Top()
	{
		return a[top - 1];
	}

protected:
	T* a=NULL;       // 数组a
	size_t top;    //栈顶位置
	size_t capacity;
protected:
	void Checkcapacity()
	{
		if (a == 0)
		{
			capacity = 1;  //这里一定要用一个非零数字，否则执行else时空间开辟不出来，与后面加的3的效果一样
			a = new T[capacity];
			return;
		}
		if (top == capacity)
		{
			size_t i = 0;
			capacity = 2 * capacity +3;
			T*tmp = new T[capacity];
			for (i = 0; i < top; ++i)   //++i   i++
			{
				tmp[i] = a[i];
			}
			delete[] a;
			a = tmp;

		}
	}
};

int main()
{
	Stack<int> s1;
	/*for (int j = 0; j < 10; j++)
	{
		s1.Push(j);
	}*/
	//cout << s1.Push(j) << "--";
	s1.Push(1);
	s1.Push(2);
	s1.Push(3);
	s1.Push(4);
	//cout << s1.Push() << endl;
	while (!s1.Empty())
	{
		cout << s1.Top() << "- ";
		s1.Pop();
	}
	system("pause");
	return 0;
}


17.Generalized  广义表
#define _CRT_SECURE_NO_WARNINGS 1
# include <iostream>
using namespace std;
# include <assert.h>
enum Type        //类型
{
	HEAD,VALUE,SUB    //分别为头结点，原子值，子表节点类型
};
struct GeneralizedNode     
{
	Type _type;  //类型
	GeneralizedNode* _next;   //指向同一层的下一个节点
	union
	{
		int _value;    //节点的值
		GeneralizedNode*_subLink;   //指向子表的指针
	};
	GeneralizedNode(Type type = HEAD, int value = 0)  //初始化列表并同时开辟空间
		:_type(type)
		, _next(NULL)
	{
		if (_type == VALUE)
			_value = value;
		else if (_type == SUB)
			_subLink = NULL;
	}
};
                                  /*广义表数据元素创建结点：结点类型_type（HEAD,VALUE,SUB）
								  
								  与同层指向下一个结点的指针_next，以及值域_value(若没有值即是指向子表的指针_subLink)*/
class Generalized
{
public:
	Generalized()
		:_head(NULL)
	{}
	Generalized(const char*str)      
		:_head(NULL)
	{
		_head = _CreatList(str);   //创建广义表   由书写顺序到链表
	}
	Generalized(const Generalized& g)
	{
		_head = _Copy(g._head);  //复制广义表   由链表到链表
	}
	Generalized& operator=(Generalized g)   //运算符重载
	{
		swap(this->_head, g._head);   //????
		return *this;
	}
	~Generalized()   //析构
	{
		_Destory(_head);
	}
	bool _isValue(char ch)    //判断值域
	{
		if ((ch >= '0'&&ch <= '9') || (ch >= 'a'&&ch <= 'z') || (ch >= 'A'&&ch <= 'Z'))
		{
			return true;
		}
		else
		{
			return false;
		}
	}
	void Print()
	{
		_Print(_head);
		cout << endl;
	}     
	size_t Size()                 
	{
		return _Size(_head);
	}
	size_t Depth()
	{
		return _Depth(_head);
	}
protected:
	void _Destory(GeneralizedNode* head)   //销毁
	{
		GeneralizedNode* cur = head;
		while (cur)
		{
			GeneralizedNode* del = cur;
			cur = cur->_next;
			if (del->_type == SUB)
			{
				_Destory(del->_subLink);
			}
			delete del;
		}
		
	}
	GeneralizedNode*_Copy(GeneralizedNode* head)  // 复制
	{
		GeneralizedNode* newHead = new GeneralizedNode(HEAD);
		GeneralizedNode* newCur = newHead;
		GeneralizedNode* cur = head->_next;
		while (cur)
		{
			if (cur->_type == VALUE)
			{
				newCur->_next = new GeneralizedNode(VALUE, cur->_value);
				newCur = newCur->_next;
			}
			else if (cur->_type == SUB)
			{
				newCur->_next = new GeneralizedNode(SUB);
				newCur = newCur->_next;
				newCur->_subLink = _Copy(cur->_subLink);   
			}
			cur = cur->_next;
		}
		return newHead;
	}
	size_t _Depth(GeneralizedNode* head)
	{
		int depth = 1;
		GeneralizedNode* cur = head;
		while (cur)
		{
			if (cur->_type == SUB)
			{
				int   subDepth = _Depth(cur->_subLink);
				if (subDepth + 1 > depth)
				{
					depth = subDepth + 1;
				}
			}
			cur = cur->_next;
		}
		return depth;
	}
	size_t _Size(GeneralizedNode* head)
	{
		size_t size = 0;
		GeneralizedNode*cur = head;
		while (cur)
		{
			if (cur->_type == VALUE)
			{
				++size;
			}
			else if (cur->_type == SUB)
			{
				size += _Size(cur->_subLink);
			}
			cur = cur->_next;
		}
		return size;
	}
	void _Print(GeneralizedNode* head)
	{
		GeneralizedNode* cur = head;
		while (cur)
		{
			if (cur->_type == HEAD)
			{
				cout << "(";
			}
			else if (cur->_type == VALUE)
			{
				cout << (char)cur->_value;
				if (cur->_next)
					cout << ",";
			}
			else
			{
				_Print(cur->_subLink);
				if (cur->_next)
					cout << ",";
			}
			cur = cur->_next;
		}
		cout << ")";
	}
	GeneralizedNode* _CreatList(const char*&str)    // 创建
	{
		assert(*str == '(');
		++str;
		GeneralizedNode* head = new GeneralizedNode(HEAD);
		GeneralizedNode*cur = head;
		while (*str)
		{
			if (_isValue(*str))
			{
				cur->_next = new GeneralizedNode(VALUE, *str);
				cur = cur->_next;
				++str;
			}
			else if (*str == '(')
			{
				GeneralizedNode* subNode = new GeneralizedNode(SUB);
			    cur->_next = subNode;
				cur = cur->_next;
				subNode->_subLink = _CreatList(str);
			}
			else if (*str == ')')
			{
				++str;
				return head;
			}
			else
			{
				++str;
			}
		}
		cout << "广义表字符串错误" << endl;
		assert(false);
		return head;
	}

protected:
	GeneralizedNode* _head;
};
void TestGeneralized()
{
	Generalized g1("()");
	Generalized g2("(a,b)");
	Generalized g3("(a,b,(c,d))");
	Generalized g4("(a,b,(c,d),(e,(f),h))");

	g4.Print();

	cout << "g4.Size:>" << g4.Size() << endl;
	cout << "g4.Depth:>" << g4.Depth() << endl;

	Generalized g5(g4);
	g5.Print();
}
int main()
{
	TestGeneralized();
	
	system("pause");
	return 0;
}

18.练习
#include <stdio.h>
#include <windows.h>
void main()
{
	printf("my world\n");
	system("pause");
}

#include <stdio.h>
void main()
{
	printf("welcome!\n");
	system("pause")
}


#include <stdio.h >
int max(int x, int y, int z);
main()
{
	int a, b, c, d;
	printf("enter three numbers:");
	scanf_s("%d,%d,%d",&a,&b,&c);
	d = max(a,b,c);
	printf("max=%d\n", d);

	system("pause");
}
int max(int x, int y, int z)
{
	int w;
	if (x >= y)
	{
		if (x >= z)
			w = x;
		else
			w = z;
	}
	else
	{
		if (y <= z)
			w = z;
		else
			w = y;
	}
	return w;
 //一定要注意输入数据时的格式，用逗号隔开，而不是空格
 
 18.//编写程序实现字符串到整数的转换，如输入字符串“12345”，输出整数12345；
//即实现atoi（）； 
#include <stdio.h>
#include <assert.h>
#include <ctype.h>
#include <limits.h>
enum RET
{
	VALID,INVALID
};
enum RET state = VALID;
int my_atoi(const char* str)
{
	assert(str);
	int flag = 1;
	long long ret = 0;
	if (str == NULL)   //指针为NULL
	{
		return 0;
	}
	if (*str == '\0')  //空字符串
	{
		return 0;
	}
	while (isspace(*str))//空白字符处理
	{
		str++;
	}
	if (*str == '-') //+ -号处理
	{
		flag = -1;
	}
	if ((*str == '+') || (*str == '-'))
	{
		str++;
	}
	while (*str)
	{
		if ((*str >= '0') &&(*str <= '9'))
		{
			ret = ret * 10 + flag*(*str - '0');
			if ((ret>INT_MAX) || (ret < INT_MIN))    //处理溢出
			{
				printf("数值越界\n");
				return  0;
			}
			
		}
		else
		{
			state = INVALID;  //处理异常字符
			return ret;
			    
		}
		str++;
	}
	return ret;
	
	
}
int main()
{
	char arr[20];
	scanf("%s", arr);
	int ret = my_atoi(arr);
	if (state == VALID)
	{
		printf("%d\n", ret);
	}
	else 
	{
		printf("输入值非法\n");
		printf("%d\n", ret);
	}
	system("pause");
	return 0;
}

19.字符串右旋实现:(1)三步反转法  （2）直接移动法
# include <stdio.h>
# include <string.h>
# include <assert.h>
void Reverse(char* start, char* end)
{
	assert(start);
	assert(end);
	while (start < end)
	{
		char tmp = *start;
		*start = *end;
		*end = tmp;
		start++;
		end--;
	}
}
void RightLoopMove(char* pStr, size_t n)
{
	int len = strlen(pStr);
	Reverse(pStr, pStr + len - n - 1);
	Reverse(pStr+len-n, pStr + len - 1);
	Reverse(pStr, pStr + len- 1);
}
int main()
{
	char arr[] = "abcdef";
	RightLoopMove(arr, 2);
	printf("%s\n", arr);
	system("pause");
	return 0;
}


# include <stdio.h>
# include <string.h>
# include <assert.h>
RightLoopMove(char* pStr, size_t n)
{
	assert(pStr);
	int len = strlen(pStr);
	while (n)
	{
		char tmp = pStr[len-1];
		for (int i = len-1; i >0; i--)
		{
			pStr[i] = pStr[i - 1];
		}
		pStr[0] = tmp;
		n--;
	}
}
int main()
{
	char arr[] = "abcdef";
	RightLoopMove(arr, 2);
	printf("%s\n", arr);
	system("pause");
	return 0;
}


20.通讯录（静态）
#define _CRT_SECURE_NO_WARNINGS 1
# include <stdio.h>
# include <string.h>
enum {EXIT,ADD,DEL,MODIFY,FIX,SHOW,CLEAR,SORT};
typedef struct People
{
	char name[20];
	char sex[2];
	int age;
	int tel[11];
	char idd[40];
}Peo;

typedef struct Contact
{
	Peo dhb[1000];
	int count;
}Con, *pcon;
void init(pcon ppcon);
void add(pcon ppcon);
void del(pcon ppcon);
void modify(pcon ppcon);
void fix(pcon ppcon);
void show(pcon ppcon);
void clear(pcon ppcon);
void sort(pcon ppcon);

#define _CRT_SECURE_NO_WARNINGS 1
//# include <stdio.h>
//#define N 20
//
//int main()
//{
//	int cur = N;  //当下共有的瓶子数
//	int count = N;//当下共喝的汽水瓶数
//		while (cur > 1)
//	 {
//		int x;
//		x = cur % 2;
//		count += cur / 2;
//		cur = cur / 2 + x;
//	}
//	
//	printf("总共喝汽水：%d\n", count);
//	system("pause");
//	return 0;
//}
//注：当钱数为0或1元时，会直接用printf函数输出原数，其他则会进入循环判断

//#include <stdio.h>
//#define MAX  20
//int main()
//{
//	int money = MAX;
//	int count = MAX;
//	while (1)
//	{
//		if (money % 2 != 0)
//		{
//			count = count + money - 1;
//			break;
//		}
//		else
//		{
//			money = money / 2;
//			count += money;
//		}
//	}
//	printf("%d\n", count);
//	return 0;
//}


//#include <stdio.h>
//int add(int x, int y)
//{
//	int z = 0;
//	z = x + y;
//	return z;
//}
//int main()
//{
//	int a = 1;
//	int b = 2;
//	int c = 0;
//	c = add(a, b);
//	system("pause");
//	return 0;
//}
//
////字符串连接函数 strcat
////原型strcat(char[],const char[])
//#include <stdio.h>
////#include <string.h>
//#include <assert.h>
////void my_strcat(char strdest[], const char strsrc[]);
//char * my_strcat(char *strdest, const char *strsrc)
//{
//	assert(strdest);
//	assert(strsrc);
//	char *ret = strdest;
//	while (*strdest)
//	{
//		strdest++;
//	}
//	while (*strdest++ = *strsrc++)
//	{
//		;         //为了保证循环的继续 必须有！
//	}
//	return ret;
//}
//int main()
//{
//	char dest[20] = "This is ";
//	char src[] = "my_strcat";
//	my_strcat(dest, src);
//	printf("%s\n", dest);   //%s 输出一个字符串
//	system("pause");
//	return 0;
//
//}
//
//
////strstr函数   思路：在字符串s1中查找s2的第一次出现的位置，否则返回null
////原型 ： char *strstr(char *str1, const char *str2);
//# include <stdio.h>
////#include <string.h>
//char * my_strstr(char *s1, const char *s2)  
//{  
//    int n=0;  
//    if (*s2)  
//    {  
//        while (*s1)  
//        {  
//			if (*(s1 + n) == *(s2 + n))
//			{
//				if (*(s2 + n + 1) == NULL)
//				{
//					return (char *)s1;
//				}
//			   n++;
//			}
//           /* for (n=0; *(s1 + n) == *(s2 + n); n++)  
//            {  
//
//                if (*(s2 + n + 1)==NULL)  
//                    return (char *)s1;  
//            }  */
//            s1++;    //只要第n次不相等时，就进行s1++，直到满足条件时开始执行下一条语句
//        }  
//        return NULL;  
//    }  
//    else  
//        return (char *)s1;
//}

//int main()
//{
//	char*str1 = "1233456";
//	char* str2 = "345";
//	char*s=my_strstr(str1, str2);
//	printf("%s\n", s);
//	system("pause");
//	return 0;
//}


//1.模拟实现strcmp 
				/*C/C++函数，比较两个字符串.设这两个字符串为str1，str2，若str1 == str2，则返回零；若str1>str2，则返回正数；
				若str1<str2，则返回负数。*/
//2.模拟实现memcpy  c和c++使用的内存拷贝函数，
                //memcpy函数的功能是从源src所指的内存地址的起始位置开始拷贝n个字节到目标dest所指的内存地址的起始位置中。
//3.模拟实现memmove


//#include <stdio.h>
//#include <assert.h>
//char * my_strcmp(const char* str1,const char* str2) //字符串比较函数
//{
//	//assert(str1);
//	//assert(str2);
//	const char *s1 = str1;
//	const char *s2 = str2;
//	while (*s1||*s2 )
//
//	{
//		if (*s2 == '\0' || *s1 > *s2)
//		{
//			return 1;
//		}
//		else if (*s1 == '\0' || *s1 < *s2)
//		{
//			return -1;
//		}
//		else
//		{
//			return 0;
//		}
//		s1++;
//		s2++;
//	}
//		return 0;  // 是在两个字符串都为空时返回值 0
//}
//
//void* my_memcpy( void * dest,void *src,size_t n)//不相干内存
//{
//	assert(dest);
//	assert(src);
//	char * ret = dest;
//	char *pdest = (char *)dest;
//	char *psrc = (char *)src;
//	while (n-- > 0)
//	{
//		*pdest++ = *psrc++;
//	}
//	return ret;
//}
//
//void* my_memmove(void *dest,const void *src,size_t n)//相干不相干内存都可
//{
//	assert(dest);
//	assert(src);
//	char *pdest = (char *)dest;
//	char *psrc = (char *)src;
//	char *ret = dest;
//	if ((src < dest) && (pdest < psrc + n))   //内存重复时
//	{
//		*pdest =  *(pdest + n - 1);
//		*psrc =  *(psrc + n - 1);
//		while (n-->0)
//		{
//			//*pdest = *(pdest + n);
//			//*psrc = *(psrc + n);
//			*(pdest--) = *(psrc--);
//		}
//
//
//	}
//	else
//	{
//		while (n-- > 0)
//		{
//			*pdest++ = *psrc++;
//		}
//	}
//		
//	return ret;
//}
//void Test1()
//{
//	char *str1 = "12345";
//	char *str2 = "456";
//	char *tmp = my_strcmp(str1, str2);
//	printf("%d\n", tmp);
//}
//void Test2()
//{
//	char * str1 = "abcdefg";
//	char arr[20];
//	memset(arr, 0, sizeof(arr));     //将内存设置初始化为0
//	char* tmp = my_memcpy(arr, str1, 5);
//	printf("%s\n", tmp);
//}
//void Test3()
//{
//	char str[] = "123456789";
//	my_memmove(str + 4, str + 3, 3);
//	puts(str);
//
//}
//int main()
//{
//	//Test1();
//	//Test2();
//	Test3();
//	system("pause");
//	return 0;
//}


////冒泡排序  方法：1.数组 2.指针
//# include  <stdio.h>
////# define N  10
//void bubbleSort(int arr[], int size)
//{
//	int i = 0;
//	int j = 0;
//	for (i = 0; i < size - 1;i++)
//	for (j = 0; j < size - 1 - i; j++)
//	{
//		if (arr[j]>arr[j + 1])
//		{
//			int tmp = arr[j];
//			arr[j] = arr[j + 1];
//			arr[j + 1] = tmp;
//		}
//	}
//}
//	
//
//int main()
//{
//	int i=0;
//	int arr[] = { 9,8,7,6,5,4,3,2,1,0 };
//	int size = sizeof(arr) / sizeof(arr[0]);
//	 bubbleSort(arr,size);
//	 for (i = 0; i < size; i++)
//	 {
//		 printf(" %d ", arr[i]);
//	 }
//	system("pause");
//	return 0;
//}
//
//# include  <stdio.h>
////# define N  10
//void bubbleSort(int* p, int size)
//{
//	int i = 0;
//	int j = 0;
//	for (i = 0; i < size - 1; i++)
//	for (j = 0; j < size - 1 - i; j++)
//	{
//		if (*(p+j)>*(p+j+1))
//		{
//			int tmp = *(p + j);
//			*(p + j) = *(p + j + 1);
//			*(p + j + 1) = tmp;
//		}
//	}
//}
//
//
//int main()
//{
//	int i = 0;
//	int arr[] = { 9, 8, 7, 6, 5, 4, 3, 2, 1, 0 };
//	int size = sizeof(arr) / sizeof(arr[0]);
//	int *p = arr;                 //数组名指数组的起始位置
//	bubbleSort( p, size);
//	for (i = 0; i < size; i++)
//	{
//		printf(" %d ", *(p+i));
//	}
//	system("pause");
//	return 0;
//} 

//1.完成杨氏矩阵的查找函数
//2.模拟实现strchr和strrchr
//3.模拟实现strrstr
//4.研究结构体内存对齐
//5.研究柔性数组

//# include <stdio.h>
// char *my_strchr(const char *str, char ch)
//{
//	if (*str)
//	{
//		while (*str != '\0'&&*str != ch)
//		{
//			++str;      //str++;
//		}
//		return *str == ch ? str : null;
//	}
//	else
//		return null;
//
//}
//int  my_strchr(const char *str, int ch)
//{
//	int count = 1;
//	if (*str)
//	{
//		while (*str != '\0'&&*str != ch)
//		{
//			++str; //str++;
//			++count;//count++;
//		}
//		return *str == ch ? count : null;
//	}
//	else
//		return null;
//
//}
//char* my_strrchr(const char *str, char ch)
//{
//	const char *ptr = null;
//	
//	while (*str != ch)
//	{
//		++str;
//		if (*str == ch&&*str!='\0')
//		{
//			ptr = str;
//			++str;
//		}
//		else if (*str == '\0')
//		{
//			return  ptr;
//		}
//	}
//	
//}
//
//test1()
//{
//	char arr[] = "welcome to this world!";
//	int ret = my_strchr(arr, 'o');
//	printf("ret=%d", ret);
//}
//test2()
//{
//	char arr[] = "welcome to this world!";
//	char* ret = my_strrchr(arr, 'o');
//	printf("ret=%s", ret);
//}
//int main()
//{
//	//test1();
//	test2();
//	system("pause");
//	return 0;
//}

//# include <stdio.h>
//char *my_strrstr(const char *s1, const char *s2)
//{
//	char *last = NULL;
//	char *current = NULL;
//	if (*s2)  //只有在s2不为空时才查找，若s2为空，返回NULL
//	{
//		current = strstr(s1, s2);  //查找s2在s1中第一次出现的位置
//		while (current != NULL)
//		{
//			last = current;
//			current = strstr(last + 1, s2);
//		}
//	}
//	return last;
//}
//int main()
//{
//	char *str1 = "abcdefabcdef";
//	char *str2 = "bcd";
//	char * ret = my_strrstr(str1, str2);
//	printf("ret=%s", ret);
//	system("pause");
//	return 0;
//}

#include "Con1.h"
// 通讯录
//1.声明结构体
//3.实现
int search(pcon con, char *pname)
{
	for (int i = 0; i < con->count; i++)
	{
     if (strcmp(con->dhb[i].name, pname) == 0)
	  {
		return i;
	  }
	}
	return -1;
}
void init(pcon ppcon)    // 初始化
{
	ppcon->count = 0;
}
void add(pcon ppcon)
{
	if (ppcon->count >= 1000)
	{
	printf("电话本满了\n");
	return;
	}
	printf("请输入姓名：");
	scanf("%s", ppcon->dhb[ppcon->count].name);
	printf("请输入性别："); 
	scanf("%s", ppcon->dhb[ppcon->count].sex);
	printf("请输入年龄：");
	scanf("%d", &ppcon->dhb[ppcon->count].age);//&
	printf("请输入电话：");
	scanf("%s", ppcon->dhb[ppcon->count].tel);
	printf("请输入地址：");
	scanf("%s", ppcon->dhb[ppcon->count].idd);
	ppcon->count++;
	printf("添加联系人成功ok！\n");
}
void del(pcon ppcon)
{
	int ret;
	int n;
	char name[20];
	printf("请输入要删除人的姓名：");

	scanf("%s", name);
	ret = search(ppcon, name);
	if (ret != -1)
	{
		printf("此联系人存在\n");
		printf("是否确定要删除此联系人\n");
		printf("是请按1，否请按0\n");
		scanf("%d", &n);
		if (n == 1)
		{
			for (int i =ret; i < ppcon->count; i++)
			{
				ppcon->dhb[i] = ppcon->dhb[i + 1];
			}
			printf("删除成功");
			ppcon->count--;
		}
		else if (n == 0)
			printf("删除失败");
	}
}
void modify(pcon ppcon)
{
	char name[20];
	printf("请输入要查找的人的姓名：");
	scanf("%s", name);
	int ret = search(ppcon, name);
	if (ret != -1)
	{
		printf("此联系人存在\n");
		printf("%s", ppcon->dhb[ret].name);
		printf("%s", ppcon->dhb[ret].sex);
		printf("%d", ppcon->dhb[ret].age);
		printf("%s", ppcon->dhb[ret].tel);
		printf("%s", ppcon->dhb[ret].idd);
	}
	else
	{
		printf("此联系人不存在\n");
	}
}
void fix(pcon ppcon)
{
	char name[20];
	printf("请输入要修改的人的姓名：");
	scanf("%s", name);
	int ret = search(ppcon, name);
	if (ret != -1)
	{
		printf("此联系人存在\n");
		printf("姓名修改成：");
		scanf("%s", ppcon->dhb[ret].name);
		printf("性别修改成：");
		scanf("%s", ppcon->dhb[ret].sex);
		printf("年龄修改成：");
		scanf("%d", &ppcon->dhb[ret].age);
		printf("电话修改成：");
		scanf("%s", ppcon->dhb[ret].tel);
		printf("地址修改成：");
		scanf("%s", ppcon->dhb[ret].idd);
		printf("修改成功\n");
	}
	else
		printf("此人不存在\n");

}
void show(pcon ppcon)

{
	printf("输出所有人信息：");
	for (int i = 0; i < ppcon->count; i++)
	{
		printf("%s\n", ppcon->dhb[i].name);
		printf("%s\n", ppcon->dhb[i].sex);
		printf("%d\n", ppcon->dhb[i].age);//此处不许用再取地址，因为ppcon->dhb[i].age已经是int型的数字，加上&则是取12的地址了
		printf("%s\n", ppcon->dhb[i].tel);
		printf("%s\n", ppcon->dhb[i].idd);
	}
	printf("\n");
}
void clear(pcon ppcon)
{
	printf("清空所有联系人：");
	/*for (int i = 0; i < p->count; i++)
	{
		p->dhb[i] = p->dhb[i + 1];
	}*/
	ppcon->count = 0;

}
void sort(pcon ppcon)
{
	for (int i = 0; i < ppcon->count - 1; i++)
	{
			for (int j = 0; j < ppcon->count - 1 - i; j++)
		{
				if (strcmp(ppcon->dhb[j].name, ppcon->dhb[j + 1].name)>0)
			{
				Peo tmp;
				tmp = ppcon->dhb[j];
				ppcon->dhb[j] = ppcon->dhb[j + 1];
				ppcon->dhb[j + 1] = tmp;
			}
		}
	
	}
	show(&ppcon);
}


#define _CRT_SECURE_NO_WARNINGS 1
#include "Con1.h"
void menu()

{
	printf("****      menu     ****\n");
	printf("****1.add  2.delete****\n");
	printf("****3.modify 4.fix   ****\n");
	printf("****5.show 6.clear ****\n");
	printf("****7.sort 0.exit  ****\n");
}
void test()
{
	Con con;
	init(&con);
	int input = 1;
	
	while (input)
	{
		menu();
		printf("请选择操作选项：");
		scanf("%d", &input);
		switch (input)
		{
		case ADD:add(&con); break;
		case DEL:del(&con); break;
		case MODIFY:modify(&con); break;
		case FIX:fix(&con); break;
		case SHOW:show(&con); break;
		case CLEAR:clear(&con); break;
		case SORT:sort(&con); break;
		case EXIT:exit(1); break;
		}
	}
}
int main()
{
	test();
	system("pause");
	return 0;
}


21.通讯录（动态+文件）

#define _CRT_SECURE_NO_WARNINGS 1

//1.头文件
# include <stdio.h>
# include <string.h>
#include <assert.h>
#include <stdlib.h>

#define FILENAME  "contact.dat"



enum { EXIT, ADD, DEL, FIND, MODIFY, SHOW, CLEAR, SORT };

typedef struct People
{
	char name[20];
	char sex[2];
	int age;
	int tel[11];
	char idd[40];
}Peo;

typedef struct Contact
{
	Peo* dhb;  //指向电话本的指针
	int count; //记录当前有效人信息个数
	int capacity;  //容量
}Con, *pcon;


void init(pcon pc);
void add(pcon pc);
void del(pcon pc);
void find(pcon pc);
void modify(pcon pc);
void show(pcon pc);
void clear(pcon pc);
void sort(pcon pc);
void check(pcon pc);  //检查容量
void load(pcon pc);   //下载
void save(pcon pc);  //保存
void printff(int*pr);


//2.实现

int search(pcon con, char *pname)
{
	for (int i = 0; i < con->count; i++)
	{
		if (strcmp(con->dhb[i].name, pname) == 0)
		{
			return i;
		}
	}
	return -1;
}
void init(pcon pc)    // 初始化
{
	pc->count = 0;
	pc->dhb = (Peo*)malloc(2 * sizeof(Peo));
	if (pc->dhb == NULL)
	{
		printf("开辟失败\n");
		exit(EXIT_FAILURE);
	}
	memset(pc->dhb, 0, 2*sizeof(Peo));
	pc->capacity = 2;
	load(pc);
}

void check(pcon pc)
{
	
	if (pc == NULL)
	{
		return;
	}

	if ((pc->count) >= (pc->capacity))              //一定是>=,否则运行出错
	{
		pc->dhb =(Peo*) realloc(pc->dhb, (pc->capacity + 3)*sizeof(Peo));
		pc->capacity = pc->capacity + 3;
	}
	if (pc->dhb == NULL)
	{
		perror("开辟失败");
		exit(EXIT_FAILURE);
	}
	
}

void load(pcon pc)
{
	int i = 0;
	//pc->count = i;
	FILE* read = fopen(FILENAME, "r");
	if (read == NULL)
	{
		perror("open file contact.c for read");
		exit(EXIT_FAILURE);
	}
	
	while (fread(&(pc->dhb[i]), sizeof(Peo), 1, read))  //此处应该有个变量来i标记位置，方便检测
	{
		i++;
		pc->count++;
		check(pc);
	}
	
	//pc->count = i;
	
	fclose(read);

}
void save(pcon pc)
{
	int i = 0;
	//int* pr = NULL;
	FILE* write = fopen(FILENAME, "w");
	if (write == NULL)
	{
		perror("open file contact.c for write");
		exit(EXIT_FAILURE);
	}
	//fwrite((&pr), sizeof(Peo), 1, write);
	for (i = 0; i < pc->count; i++)
	{
		fwrite(&(pc->dhb[i]), sizeof(Peo), 1, write);
		fputc('\n', write);
	}
	fclose(write);
	free(pc->dhb);
}

void printff(int*pr)
{
	printf("%10s\t%5s\t%3s\t%12s\t%10s\n", "名字", "性别", "年龄", "电话", "地址");
}

//操作
void add(pcon pc)
{
	check(pc);
	/*if (pc->count >= 1000)
	{
		printf("电话本满了\n");
		return;
	}*/
	printf("请输入姓名：");
	scanf("%s", pc->dhb[pc->count].name);
	printf("请输入性别：");
	scanf("%s", pc->dhb[pc->count].sex);
	printf("请输入年龄：");
	scanf("%d", &pc->dhb[pc->count].age);  //&
	printf("请输入电话：");
	scanf("%s", pc->dhb[pc->count].tel);
	printf("请输入地址：");
	scanf("%s", pc->dhb[pc->count].idd);
	pc->count++;
	printf("添加联系人成功ok！\n");
}
void del(pcon pc)
{
	int ret;
	int n;
	enum {ZERO,ONE};
	char name[20];
	printf("请输入要删除人的姓名：");

	scanf("%s", name);
	ret = search(pc, name);
	if (ret != -1)
	{
		printf("此联系人存在\n");
		printf("是否确定要删除此联系人\n");
		printf("是请按1，否请按0\n");
		scanf("%d", &n);
		if (n == ONE)
		{
			for (int i = ret; i < pc->count; i++)
			{
				pc->dhb[i] = pc->dhb[i + 1];
			}
			printf("删除成功");
			pc->count--;
		}
		else if (n == ZERO)
			printf("删除失败");
	}
	else
	{
		printf("此联系人不存在\n");
	}
}
void find(pcon pc)
{
	char name[20];
	printf("请输入要查找的人的姓名：");
	scanf("%s", name);
	int ret = search(pc, name);
	if (ret != -1)
	{
		printf("此联系人存在\n");
		printf("%10s\t%5s\t%3s\t%12s\t%10s\n", "名字", "性别", "年龄", "电话", "地址");
		printf("%10s\t", pc->dhb[ret].name);
		printf("%5s\t", pc->dhb[ret].sex);
		printf("%3d\t", pc->dhb[ret].age);
		printf("%12s\t", pc->dhb[ret].tel);
		printf("%10s\t", pc->dhb[ret].idd);
		printf("\n");
	}
	else
	{
		printf("此联系人不存在\n");
	}
}
void modify(pcon pc)
{
	char name[20];
	printf("请输入要修改的人的姓名：");
	scanf("%s", name);
	int ret = search(pc, name);
	if (ret != -1)
	{
		printf("此联系人存在\n");
		printf("姓名修改成：");
		scanf("%s", pc->dhb[ret].name);
		printf("性别修改成：");
		scanf("%s", pc->dhb[ret].sex);
		printf("年龄修改成：");
		scanf("%d", &pc->dhb[ret].age);
		printf("电话修改成：");
		scanf("%s", pc->dhb[ret].tel);
		printf("地址修改成：");
		scanf("%s", pc->dhb[ret].idd);
		printf("修改成功\n");
		printf("%10s\t%5s\t%3s\t%12s\t%10s\n", "名字", "性别", "年龄", "电话", "地址");
		printf("%10s\t", pc->dhb[ret].name);
		printf("%5s\t", pc->dhb[ret].sex);
		printf("%3d\t", pc->dhb[ret].age);
		printf("%12s\t", pc->dhb[ret].tel);
		printf("%10s\t", pc->dhb[ret].idd);
		printf("\n");
	}
	else
		printf("此人不存在\n");

}
void show(pcon pc)

{
	printf("输出所有人信息：\n");
	printf("%10s\t%5s\t%3s\t%12s\t%10s\n", "名字", "性别", "年龄", "电话", "地址");
	for (int i = 0; i < pc->count; i++)
	{
		printf("%10s\t", pc->dhb[i].name);
		printf("%5s\t", pc->dhb[i].sex);
		printf("%3d\t", pc->dhb[i].age);//此处不许用再取地址，因为pc->dhb[i].age已经是int型的数字，加上&则是取12的地址了
		printf("%12s\t", pc->dhb[i].tel);
		printf("%10s\n", pc->dhb[i].idd);
	}
	printf("\n");
}
void clear(pcon pc)
{
	printf("清空所有联系人：");
	/*for (int i = 0; i < p->count; i++)
	{
	p->dhb[i] = p->dhb[i + 1];
	}*/
	pc->count = 0;

}
void sort(pcon pc)
{
	for (int i = 0; i < pc->count - 1; i++)
	{
		for (int j = 0; j < pc->count - 1 - i; j++)
		{
			if (strcmp(pc->dhb[j].name, pc->dhb[j + 1].name)>0)
			{
				Peo tmp;
				tmp = pc->dhb[j];
				pc->dhb[j] = pc->dhb[j + 1];
				pc->dhb[j + 1] = tmp;
			}
		}

	}
	show(pc);
}


//3.测试
void menu()

{
	printf("****      menu     ****\n");
	printf("****1.add  2.delete****\n");
	printf("****3.find 4.modify   ****\n");
	printf("****5.show 6.clear ****\n");
	printf("****7.sort 0.exit  ****\n");
}
void test()
{
	Con con;
	init(&con);
	int input = 1;

	while (input)
	{
		menu();
		printf("请选择操作选项：");
		scanf("%d", &input);
		switch (input)
		{
		case ADD:add(&con); break;
		case DEL:del(&con); break;
		case FIND:find(&con); break;
		case MODIFY:(&con); break;
		case SHOW:show(&con); break;
		case CLEAR:clear(&con); break;
		case SORT:sort(&con); break;
		case EXIT:save(&con); break; 
		default:printf("选择错误\n");break;//
		}
	}
}
int main()
{
	test();
	system("pause");
	return 0;
}

22.注释转换

#define _CRT_SECURE_NO_WARNINGS 1

#include "CommentConvert.h"

StateType state;
                 
void DoNullState(FILE* read, FILE* write)
{
	int ch1 = fgetc(read);
	int ch2 = 0;
	switch (ch1)
	{
	case '/':
		ch2 = fgetc(read);
		if (ch2 == '*')
		{
			fputc(ch1, write);
			fputc('/', write);
			state = C_STATE;
		}
		else if (ch2 == '/')
		{
			fputc(ch1, write);
			fputc(ch2, write);
			state = CPP_STATE;
		}
		else
		{
			fputc(ch1, write);
			fputc(ch2, write);
		}
		break;
	case EOF:
		fputc(ch1,write);
		state = END_STATE;
		break;
	default:
		fputc(ch1, write);
		break;
	}
}
void DoCState(FILE* read, FILE* write)
{
	int ch1 = fgetc(read);
	int ch2 = 0;
	int ch3 = 0;
	switch (ch1)
	{
	case '*':
		ch2 = fgetc(read);
		if (ch2 == '/')  //舍弃*/
		{
			ch3 = fgetc(read);
			if (ch3 == '\n')
			{
				ungetc(ch3, read);
			}
			else
			{
				ungetc(ch3, read);
				fputc('\n', write);
			}
			state = NULL_STATE;
		}
		else 
		{
			fputc(ch1, write);
			ungetc(ch2,read);   //把读取的第二个字符放回去
		}
		break;

	case '\n':
		fputc(ch1, write);
		fputc('/', write);
		fputc('/', write);
		break;
	//case EOF:            //不可以
	//	fputc(ch1, write);
	//	state = END_STATE;
	//	break;
	default:
		fputc(ch1, write);
		break;
	}
}
void DoCppState(FILE* read, FILE* write)
{
	int ch1 = fgetc(read);
	int ch2 = 0;
	switch (ch1)
	{
	case '\n':
		fputc(ch1, write);
		state = NULL_STATE;
		break;
	/*case '/':
		ch2 = fgetc(read);
		if (ch2 == '*')
		{
			state = C_STATE;
		}
		break;*/   //在cpp状态下面时直接输出

	case EOF:
		fputc(ch1, write);
		state = END_STATE;
		break;
	default:

		fputc(ch1, write);
		break;
	}
}

void  ConvertWork(FILE* read, FILE* write)
{
	state = NULL_STATE;
	while (state != END_STATE)
	{
		switch (state)
		{
		case NULL_STATE:
			DoNullState(read, write);
			break;
		case C_STATE:
			DoCState(read, write);
			break;
		case CPP_STATE:
			DoCppState(read, write);
			break;
		}
	}
}

void CommentConvert()    //转换文件的读取与写入
{
	FILE* pRead = fopen(INPUTFILE, "r");
	if (pRead == NULL)
	{
		perror("open file for read");
		exit(EXIT_FAILURE);
	}
	FILE* pWrite = fopen(OUTPUTFILE, "w");
	if (pWrite == NULL)
	{
		fclose(pRead);
		perror("open file for write");
		exit(EXIT_FAILURE);
	}
	ConvertWork(pRead,pWrite);
	fclose(pRead);
	fclose(pWrite);
}

23.顺序表（静态）

#define _CRT_SECURE_NO_WARNINGS 1

#include <string.h>
#include <assert.h>
#include <stdio.h>
#include <windows.h>

#define MAX_SIZE 5
typedef int DataType;
typedef unsigned int size_t;

typedef struct SeqList
{
	DataType array[MAX_SIZE];
	size_t size;
}SeqList, *PSeqList;


void InitSeqList(PSeqList pSeqList);

// 顺序表尾插
// 设计函数原型
// 参数检测
// 边界条件考虑
// 逻辑操作
// 尾插
void PushBack(PSeqList pSeqList, DataType data);
void PopBack(PSeqList pSeqList);
void PrintSeqList(PSeqList pSeqList);
void PushFront(PSeqList pSeqList, DataType data);
void PopFront(PSeqList pSeqList);

// 任意位置插入
void Insert(PSeqList pSeqList, size_t pos, DataType data);

// 在顺序表中查找元素data
int Find(PSeqList pSeqList, DataType data);

// 删除顺序表中pos位置上的元素
void Erase(PSeqList pSeqList, size_t pos);

//移除顺序表中的元素data
void Remove(PSeqList pSeqList, DataType data);

// 移除顺序表中所有元素data
void RemoveAll(PSeqList pSeqList, DataType data);


#define _CRT_SECURE_NO_WARNINGS 1

#include "SeqList.h"



void InitSeqList(PSeqList pSeqList)
{
	assert(pSeqList);
	memset(pSeqList->array, 0,sizeof(DataType)* MAX_SIZE);
	pSeqList->size = 0;
}
void PushBack(PSeqList pSeqList, DataType data)
{
	assert(pSeqList);
	if (MAX_SIZE==pSeqList->size)
	{
		printf("顺序表已满！\n");
		return;
	}
	pSeqList->array[pSeqList->size] = data;
	pSeqList->size++;
 //等价于	pSeqList->array[pSeqList->size++] = data;

}
void PopBack(PSeqList pSeqList)
{
	assert(pSeqList);
	if (0 == pSeqList->size)
	{
		printf("顺序表为空！");
		return;
	}
	pSeqList->size--;
}
void PrintSeqList(PSeqList pSeqList)
{
	int idex = 0;
	for (; idex <(int) pSeqList->size; idex++)
	{
		printf("%d ", pSeqList->array[idex]);
	}
	printf("\n");
}
void PushFront(PSeqList pSeqList, DataType data)
{
	assert(pSeqList);
	int idex = (int)pSeqList->size;
	if (MAX_SIZE == pSeqList->size)
	{
		printf("顺序表已满！\n");
		return;
	}
	for (; idex >0; --idex)
	{
		pSeqList->array[idex] = pSeqList->array[idex-1];
		
	}
	pSeqList->array[0] = data;
	pSeqList->size++;

}
void PopFront(PSeqList pSeqList)
{
	assert(pSeqList);
	int idex =1;
	if (0 == pSeqList->size)
	{
		printf("顺序表已空！\n");
		return;
	}
	for (; idex <(int)pSeqList->size; ++idex)
	{
		pSeqList->array[idex-1] = pSeqList->array[idex];
	}
	pSeqList->size--;
}
void Insert(PSeqList pSeqList, size_t pos, DataType data)
{
	assert(pSeqList);
	int idex =(int) pSeqList->size;
	if (MAX_SIZE == pSeqList->size)
	{
		printf("顺序表已满\n");
		return;
	}
	if (MAX_SIZE > pSeqList->size && ((pos >= 0) && (pos < pSeqList->size)))
	{
		for (; idex >pos; idex--)   //有= 前越界
		{
			pSeqList->array[idex] = pSeqList->array[idex-1];  
		}
		pSeqList->array[pos] = data;
		pSeqList->size++;
	}
}
int  Find(PSeqList pSeqList, DataType data)
{
	assert(pSeqList);
	int idex = 0;
	for (; idex < (int)pSeqList->size; ++idex)
	{
		if (pSeqList->array[idex] == data)
		{
			return idex;
		}
	}
	return -1;

}

void Erase(PSeqList pSeqList, size_t pos)
{
	assert(pSeqList);
	int idex = pos;
	if (pSeqList->size == 0)
	{
		printf("顺序表已空！\n");
		return;
	}
	if  ((pos >= 0) && (pos < pSeqList->size))
	{
		int ret=Find(pSeqList,pSeqList->array[pos]);
		if (ret != -1)
		{
			for (; idex < (int)pSeqList->size-1; ++idex)
			{
				pSeqList->array[idex] = pSeqList->array[idex+1];
			}
		}
	}
	pSeqList->size--;

}
void Remove(PSeqList pSeqList, DataType data)
{
	assert(pSeqList);
	if (0 == pSeqList->size)
	{
		printf("顺序表已空\n");
		return;
	}
	int ret = Find(pSeqList, data);
	if (ret != (int)pSeqList->size)
	{
		Erase(pSeqList, ret);
	}
	else if (ret==-1)
	{
		printf("没有找到该数据\n");
		return;
	}
}
void RemoveAll(PSeqList pSeqList, DataType data)
{
	assert(pSeqList);
	int idex = 0;
	int tmp = 0;
	if (0 == pSeqList)
	{
		printf("顺序表已空\n");
		return;
	}
	for (; idex < (int)pSeqList->size; idex++)
	{
		if (pSeqList->array[idex] == data)
		{
			for (tmp = idex; tmp < (int)pSeqList->size - 1; tmp++)
			{
				pSeqList->array[tmp] = pSeqList->array[tmp+1];
			}
			pSeqList->size--;
			idex--;
		}
	}

}


#define _CRT_SECURE_NO_WARNINGS 1
#include "SeqList.h"

SeqList seqList;
void Test1()
{
	InitSeqList(&seqList);

	PushBack(&seqList, 1);
	PushBack(&seqList, 2);
	PushBack(&seqList, 3);
	PushBack(&seqList, 4);
	PushBack(&seqList, 5);
	//PushBack(&seqList, 6);


	PrintSeqList(&seqList);

	PopBack(&seqList);
	PopBack(&seqList);
	PopBack(&seqList);
	PopBack(&seqList);
	PopBack(&seqList);
	PopBack(&seqList);

	PrintSeqList(&seqList);
}
void Test2()
{
	InitSeqList(&seqList);

	PushFront(&seqList, 1);
	PushFront(&seqList, 2);
	PushFront(&seqList, 3);
	PushFront(&seqList, 4);
	PushFront(&seqList, 5);

	PrintSeqList(&seqList);

	PopFront(&seqList);
	PopFront(&seqList);
	PopFront(&seqList);
	PopFront(&seqList);

	PrintSeqList(&seqList);
}
void Test3()
{
	InitSeqList(&seqList);

	PushBack(&seqList, 1);
	PushBack(&seqList, 2);
	//PushBack(&seqList, 3);
	//PushBack(&seqList, 4);
	//PushBack(&seqList, 5);

	PrintSeqList(&seqList);

	Insert(&seqList, 0, 10);
	PrintSeqList(&seqList);

	Insert(&seqList, 1, 20);
	PrintSeqList(&seqList);

	Insert(&seqList, 4, 30);
	PrintSeqList(&seqList);


	//Find(&seqList, 10);
	//Find(&seqList, 50);

	Erase(&seqList, 2);

	
	PrintSeqList(&seqList);
}
void Test4()
{
	InitSeqList(&seqList);

	PushBack(&seqList, 1);
	PushBack(&seqList, 2);
	PushBack(&seqList, 3);
	PushBack(&seqList, 4);
	PushBack(&seqList, 3);

	PrintSeqList(&seqList);

	Remove(&seqList, 2);
	PrintSeqList(&seqList);


	RemoveAll(&seqList, 3);
	PrintSeqList(&seqList);
}
int main()
{
	//Test1();
	//Test2();
	//Test3();
	Test4();

	system("pause");

	return 0;
}


24.搜索二叉树  BinarySearchTree

"BinarySearchTree.h"

#pragma once
#include <iostream>
using namespace std;


//BSTNode结点数据结构
template <class K, class V>
struct BSTNode
{
	//KV
	BSTNode<K, V>* _left;
	BSTNode<K, V>* _right;

	K _key;
	V _value;

	BSTNode(const K& key, const V& value)
		:_key(key)
		, _value(value)
		, _left(NULL)
		, _right(NULL)
	{}
};

//BSTree模板类的封装
template <class K, class V>
class BSTree
{
	typedef BSTNode<K, V> Node;
public:
	//非递归
	BSTree();  //默认构造函数

	//BSTree()
	//	:_root(NULL)
	//{}
	//~BSTree();

	bool Insert(const K& key, const V& value); //插入
	Node* Find(const K& key);                 //查找
	bool Remove(const K& key);               //删除
	//void InOrder(Node* _root);            //中序遍历找左最大或右最小


	//递归
	bool Insert_R(const K& key, const V& value);
	Node* Find_R(const K& key);
	bool Remove_R(const K& key);

protected:
	//非递归
	bool _Insert(const K& key, const V& value);
	Node* _Find(const K& key);
	bool _Remove(Node* root, const K& key);


	//递归
	bool _Insert_R(Node*& root, const K& key, const V& value);
	Node* _Find_R(Node*& root, const K& key);
	bool _Remove_R(Node*& root, const K& key);

protected:
	Node* _root;
};


"BinarySearchTree.cpp"

#include "BinarySearchTree.h"


template <class K, class V>
BSTree<K, V>::BSTree()
:_root(NULL)
{}

//非递归
template <class K, class V>
bool BSTree<K, V>::Insert(const K& key, const V& value)
{
	return _Insert(key, value);
}

template <class K, class V>
bool BSTree<K, V>::_Insert(const K& key, const V& value)
{
	//1.空  2.非空
	if (_root == NULL)
	{
		_root = new Node(key, value);
		return true;
	}
	Node* parent = NULL;
	Node* cur = _root;
	while (cur)
	{
		if (key < cur->_key)
		{
			parent = cur;
			cur = cur->_left;
		}
		else if (key>cur->_key)
		{
			parent = cur;
			cur = cur->_right;
		}
		else
			return false;
	}
	if (parent->_left == NULL&&key < parent->_key)
	{
		parent->_left = new Node(key, value);
	}
	else if (parent->_right == NULL&&key > parent->_key)
	{
		parent->_right = new Node(key, value);
	}
	return true;
}

template <class K, class V>
BSTNode<K, V>* BSTree<K, V>::Find(const K& key)                //查找
{
	return _Find(key);
}
template <class K, class V>
BSTNode<K, V>* BSTree<K, V>::_Find(const K&key)
{
	//1.空 2.非空
	Node*cur = _root;
	while (cur)
	{
		if (key < cur->_key)
		{
			cur = cur->_left;
		}
		else if (key>cur->_key)
		{
			cur = cur->_right;
		}
		else
			return cur;
	}
	return NULL;

}



template <class K, class V>
bool  BSTree<K, V>::Remove(const K& key)
{
	return _Remove(_root, key);
}
template <class K, class V>
bool BSTree<K, V>:: _Remove(Node* root, const K& key)
{
	//1.空  2.非空（1.左右都为空  2.左或右为空  3.左右都不为空）
	if (root== NULL)
	{
		return false;
	}

	Node* cur = root;
	Node* parent = NULL;
	Node* del = NULL;
	while (cur)
	{
		if (key < cur->_key)
		{
			parent = cur;
			cur = cur->_left;
		}
		else if (key>cur->_key)
		{
			parent = cur;
			cur = cur->_right;
		}
		else
		{
			del = cur;
			if (cur->_left == NULL&&cur->_right == NULL)  //1. 左右都为空
			{
				if (parent&&parent->_left == cur)
				{
					parent->_left = NULL;
				}
				else if (parent&&parent->_right == cur)
				{
					parent->_right = NULL;
				}
				else
				{
					root = NULL;
				}
			}
			else if (cur->_left == NULL) //2. 左为空
			{
				if (parent&&parent->_left == cur)
				{
					parent->_left = cur->_right;
				}
				else if (parent&&parent->_right == cur)
				{
					parent->_right = cur->_right;
				}
				else
				{
					root = cur->_right;
				}

			}
			else if (cur->_right == NULL)//2. 右为空
			{

				if (parent&&parent->_left == cur)
				{
					parent->_left = cur->_left;
				}
				else if (parent&&parent->_right == cur)
				{
					parent->_right = cur->_left;
				}
				else
				{
					root = cur->_left;
				}
			}
			else  //3.左右都不为空
			{
				//(1)找左子树的最大结点
				Node* maxleft = cur->_left;
				Node* parent = NULL;//   Node* parent = cur;
				while (maxleft->_right)
				{
					parent = maxleft;
					maxleft = maxleft->_right;
				}
				del = maxleft;
				swap(cur->_key, maxleft->_key);
				swap(cur->_value, maxleft->_value);
				//判断最大左子树是其父节点的左子树还是右子树
				if (parent&&parent->_left == maxleft)
				{
					parent->_left = maxleft->_left;
				}
				else if (parent&&parent->_right == maxleft)
				{
					parent->_right = maxleft->_left;
				}
				else
				{
					cur->_left = NULL;
				}


			}

			delete del;
			return true;
		}
	}
	return false;
}


//递归

template <class K, class V>
bool BSTree<K, V>::Insert_R(const K& key, const V& value)
{
	return _Insert_R(_root, key, value);
}
template <class K, class V>
bool BSTree<K, V>::_Insert_R(Node*& root, const K& key, const V& value)
{
	//1.空 2.非空
	if (root == NULL)
	{
		root = new Node(key, value);
		return true;
	}
	if (key < root->_key)
	{
		_Insert_R(root->_left, key, value);
	}
	else if (key>root->_key)
	{
		_Insert_R(root->_right, key, value);

	}
	else
	{
		return false;
	}
	return false;
}


template <class K, class V>
BSTNode<K, V>* BSTree<K, V>::Find_R(const K& key)                //查找
{
	return _Find_R(_root, key);
}
template <class K, class V>
BSTNode<K, V>* BSTree<K, V>::_Find_R(Node*& root, const K&key)
{
	//1.空2.非空
	Node* cur = root;
	if (root == NULL)
		return  NULL;
	if (key < cur->_key)
		_Find_R(cur->_left, key);
	else if (key>cur->_key)
		_Find_R(cur->_right, key);
	else
		return root;
	
}
//template <class K, class V>             //另外一种实现方法
//Node* Find_R(const K& key)
//{
//	//1.空2.非空
//	Node* cur = _root;
//	if (key < cur->_key)
//	{
//		Find_R(cur->_left->key);
//	}
//	else if (key>cur->_key)
//	{
//		Find_R(cur->_right->key);
//	}
//	else
//	{
//		return cur;
//	}
//	return NULL;
//}


template <class K, class V>
bool  BSTree<K, V>::Remove_R(const K& key)
{
	return _Remove_R(_root, key);
}
template <class K, class V>
bool BSTree<K, V>::_Remove_R(Node*& root, const K&key)
{
	//1.空  2.非空（1.左右都为空  2.左或右为空  3.左右都不为空）
	if (root == NULL)
	{
		return false;
	}
	if (key < root->_key)
	{
		_Remove_R(root->_left, key);
	}
	else if (key>root->_key)
	{
		_Remove_R(root->_right, key);
	}
	else
	{
		Node* del = root;
		//Node*parent = NULL;
		if (root->_left ==NULL&&root->_right == NULL)//1.左右都为空
		{
			root = NULL;
		}
		else if (root->_left == NULL)//2.左为空
		{
			root = root->_right;
		}
		else if (root->_right == NULL)//2.右为空
		{
			root = root->_left;

		}
		else  //3.左右都不为空
		{
			//找左子树最大结点
			Node* maxleft = root->_left;
			Node* parent = NULL;         //Node* parent = root;
			while (maxleft->_right)
			{
				parent = maxleft;
				maxleft = maxleft->_right;
			}
			del = maxleft;
			swap(root->_key, maxleft->_key);
			swap(root->_value, maxleft->_value);

			//判断最大结点是它父亲结点的左孩子还是右孩子  //即处理交换之后的删除工作，否则没有删除结点
			if (parent&&parent->_left == maxleft)
			{
				parent->_left = maxleft->_left;
			}
			else if (parent&&parent->_right == maxleft)
			{
				parent->_right = maxleft->_left;
			}
			else
			{
				root->_left = NULL;  //parent==NULL,即左结点只有一个，
			}
		}
		delete del;
		return true;
	}
	else
	{
		return false;
	}
	
}

"test.cpp"

#include "BinarySearchTree.h"
#include "BinarySearchTree.cpp"

void Test1()
{


	BSTree<int, int> t1;
	t1.Insert_R(5, 0);
	t1.Insert_R(3, 0);
	t1.Insert_R(4, 0);
	t1.Insert_R(1, 0);
	t1.Insert_R(7, 0);
	t1.Insert_R(8, 0);
	t1.Insert_R(2, 0);
	t1.Insert_R(6, 0);
	t1.Insert_R(0, 0);
	t1.Insert_R(9, 0);

	t1.Find_R(5);
	t1.Find_R(0);
	t1.Find_R(4);
	t1.Find_R(23);



	t1.Remove(4);
	t1.Remove(3);
	t1.Remove(1);
	t1.Remove(7);
	t1.Remove(8);
	t1.Remove(2);
	t1.Remove(6);
	t1.Remove(0);
	t1.Remove(5);
	t1.Remove(9);

}

int main()
{

	Test1();
	system("pause");
	return 0;
}



//文件压缩



“heap.h”
#define _CRT_SECURE_NO_WARNINGS 1

#include <vector>
#include <cassert>

template<class T>
struct Less
{
	bool operator() (const T& l, const T& r)
	{
		return l < r;
	}
};

template<class T>
struct Greater
{
	bool operator() (const T& l, const T& r)
	{
		return l > r;
	}
};

template<class T, class Compare = Less>
//template<class T, template<class> class Compare = Less>
class Heap
{
public:
	Heap()
		:_a(NULL)
	{}

	Heap(const T* a, size_t size)
	{
		_a.reserve(size);
		for (size_t i = 0; i < size; ++i)
		{
			_a.push_back(a[i]);
		}

		// 建堆
		for (int i = (_a.size() - 2) / 2; i >= 0; --i)
		{
			_AdjustDown(i);
		}
	}

	Heap(vector<T>& a)
	{
		_a.swap(a);

		// 建堆
		for (int i = (_a.size() - 2) / 2; i >= 0; --i)
		{
			_AdjustDown(i);
		}
	}

	void Push(const T& x)
	{
		_a.push_back(x);

		_AdjustUp(_a.size() - 1);
	}

	void Pop()
	{
		size_t size = _a.size();
		assert(size > 0);

		swap(_a[0], _a[size - 1]);
		_a.pop_back();
		_AdjustDown(0);
	}

	T& Top()
	{
		assert(!_a.empty());
		return _a[0];
	}

	size_t size()
	{
		assert(!_a.empty());
		return (_a.size());

	}
protected:
	void _AdjustUp(int child)
	{
		int parent = (child - 1) / 2;
		//while(parent>=0)
		while (child > 0)
		{
			Compare com;
			//Compare<T> com;
			//if (_a[child] > _a[parent])
			if (com(_a[child], _a[parent]))
			{
				swap(_a[child], _a[parent]);
				child = parent;
				parent = (child - 1) / 2;
			}
			else
			{
				break;
			}
		}
	}

	void _AdjustDown(size_t parent)
	{
		size_t child = parent * 2 + 1;
		while (child < _a.size())
		{
			// 选出孩子里面大的那一个
			//Compare<T> com;
			Compare com;
			//if (child+1 < _a.size() &&_a[child+1] > _a[child])
			if (child + 1 < _a.size()
				&& com(_a[child + 1], _a[child]))
			{
				++child;
			}

			// 如果父亲小于孩子，则交换并继续往下调整
			// 否则调堆完成

			//if(_a[child] > _a[parent])
			if (com(_a[child], _a[parent]))
			{
				swap(_a[parent], _a[child]);
				parent = child;
				child = 2 * parent + 1;
			}
			else
			{
				break;
			}
		}
	}

protected:
	vector<T> _a;
};

”Huffman.h“


#define _CRT_SECURE_NO_WARNINGS 1
#include "Heap.h"


template <class T>
struct  HuffmanNode
{
	HuffmanNode<T>*_left;    //左孩子
	HuffmanNode<T>*_right;  //右孩子
	T _weight;        //权值

	HuffmanNode(const T&weight)
		: _left(NULL)
		, _right(NULL)
		, _weight(weight)
	{}

};


//构建哈夫曼树                (利用小堆构建哈夫曼树)
template <class T>
class HuffmanTree
{
	typedef HuffmanNode<T> Node;
public:
	HuffmanTree()
		:_root(NULL)
	{}

	HuffmanTree(const T*a, size_t size, const T& invalid)     //invalid代表非法值，若为非法值，则不构建哈夫曼树
	{
		_root = CreateTree(a, size, invalid);
	}

	Node* GetRootNode()
	{
		return _root;
	}
public:
	Node* CreateTree(const T*a, size_t size, const T& invalid)
	{
		struct Compare
		{
			bool operator()(const Node*l, const Node*r)
			{
				return (l->_weight < r->_weight);
			}
		};
		Heap <Node*, Compare> minHeap;       //仿函数
		for (int i = 0; i <(int)size; ++i)
		{
			if (a[i] != invalid)
			{
				minHeap.Push(new Node(a[i]));
			}

		}
		//小堆的top结点的权值必是最小的，每次选出小堆的top构造哈夫曼树的结点
		while (minHeap.size()>1)
		{
			Node* left = minHeap.Top();
			minHeap.Pop();
			Node* right = minHeap.Top();
			minHeap.Pop();
			Node* parent = new Node(left->_weight + right->_weight);   //哈夫曼树特点，父结点是两个子结点和
			parent->_left = left;
			parent->_right = right;
			minHeap.Push(parent);

		}
		return minHeap.Top();
	}

protected:
	HuffmanNode<T>* _root;
};

”compress.h“
#define _CRT_SECURE_NO_WARNINGS 1
#include <iostream>
using namespace std;
#include <cassert>
#include "HuffmanTree.h"
#include <string>
#include <windows.h>



//1.统计字符次数   2.构建哈夫曼树（堆）   3.生成哈夫曼编码 4. 读取源文件字符压缩 5.解压
//哈夫曼树根结点的权值就是源文件读入的个数

//统计字符次数
typedef unsigned long long  LongType;
struct CharInfo
{
	unsigned char _ch;  //字符
	LongType _count;   //出现次数
	string _code;      //Huffman code


	CharInfo()
		:_ch(0)
		, _count(0)
	{}

	CharInfo(LongType count)
		:_ch(0)
		, _count(count)
	{}

	bool operator!=(const CharInfo&info) const
	{
		return _count != info._count;
	}

	CharInfo operator+(const CharInfo&info) const
	{
		return CharInfo(_count + info._count);
	}

	bool operator<(const CharInfo&info) const      //重载运算符 <
	{
		return _count < info._count;
	}


};

template <class T>
class FileCompress
{
	typedef HuffmanNode<T> Node;
public:
	FileCompress()
	{
		for (size_t i = 0; i < 256; ++i)
		{
			_infos[i]._ch = i;
			_infos[i]._count = 0;
		}
	}
public:
	void Compress(const char* filename)  //文件压缩
	{
		//1. 读取文件统计次数
		assert(filename);
		FILE*fOut = fopen(filename, "rb");
		assert(fOut);
		char ch = fgetc(fOut);
		while (!feof(fOut))
		{
			_infos[(unsigned char)ch]._count++;
			ch = fgetc(fOut);              //如何保证相同呢- 映射
		}

		//2.构建huffman并生成huffman编码
		CharInfo invalid(0);
		HuffmanTree<CharInfo> tree(_infos, 256, invalid);
		string code;
		GenerateHuffmanCode(tree.GetRootNode(), code);
		cout << endl;

		//3.将编码写入压缩文件中
		string compressfilename = filename;  //压缩文件名称
		compressfilename += ".compress";
		FILE*fIn = fopen(compressfilename.c_str(), "wb");  //c_str():将二进制码转换为c的字符串
		assert(fIn);
	
		fseek(fOut, 0, SEEK_SET);  //定位到文件起始的位置
		ch = fgetc(fOut);
		int pos = 0;//标记位置
		char value = 0;
		while (!feof(fOut))
		{
			
			string& code = _infos[(unsigned char)ch]._code;
	//cout << code << "->";
			for (size_t i = 0; i < code.size(); ++i)
			{
				value <<= 1;

				if (code[i] == '1')
				{
					value |= 1;
				}

				if (++pos == 8)
				{
					//cout<<"["<<value<<"]";
					fputc(value, fIn);
					pos = 0;
					value = 0;
				}
			}

			ch = fgetc(fOut);
			//cout << ch;
		}

		if (pos)   //残缺没满8位
		{
			value <<= (8 - pos);
			fputc(value, fIn);
		}

		cout << endl;
		//4.将huffman树的信息写入配置文件中
		string configfilename = filename;
		configfilename += ".config";
		FILE*fInConfig = fopen(configfilename.c_str(), "wb");
		assert(fInConfig);
		char buffer[128];  //buffer内容将为 12    作为一个整体的串作为配置文件
		string str;
		for (size_t i = 0; i < 256; ++i)
		{
			if (_infos[i]._count>0)
			{
				str += _infos[i]._ch;
				str += ",";
				str += _itoa((int)_infos[i]._count, buffer, 10);
				//sprintf(buffer, "%d", _infos[i]._count);
				//str += buffer;
				str += '\n';

			}
			fputs(str.c_str(), fInConfig);
			str.clear();   //置空，刷新  buffer清零
		}
		fclose(fInConfig);
		fclose(fOut);
		fclose(fIn);
	}
	void UnCompress(const char*filename)  //文件解压
	{
		// 1.读取配置文件中Huffman树的信息  直接写编码？
		string configfilename = filename;
		configfilename += ".config";
		FILE* fOutConfig = fopen(configfilename.c_str(), "rb");
		assert(fOutConfig);

		string str;
		while (ReadLine(fOutConfig, str))
		{
			if (!str.empty())
			{
				//sscanf(line.c_str(), "%s,%d", ch, appearCount);

				_infos[(unsigned char)str[0]]._count = atoi(str.substr(2).c_str());
				//string a=s.substr(0,5);即获得字符串s中从第0位开始长度为5的字符串，默认是的长度从开始到尾结束
				str.clear();
			}
			else
			{
				str += '\n';
			}
		}

		// 2.读出配置信息，重建Huffman树
		CharInfo invalid(0);
		HuffmanTree<CharInfo> tree(_infos, 256, invalid);
		LongType count = tree.GetRootNode()->_weight._count;  //统计根节点的次数

		// 3. 读取压缩信息，根据重建的Huffman树解压缩
		string compressfilename = filename;
		compressfilename += ".Compress";
		FILE* fOut = fopen(compressfilename.c_str(), "rb");
		assert(fOut);

		string uncompressfilename = filename;
		uncompressfilename += ".Uncompress";
		FILE*fIn = fopen(uncompressfilename.c_str(), "wb");  //c_str():将二进制码转换为c的字符串
		assert(fIn);

		HuffmanNode<CharInfo>* root = tree.GetRootNode();
		HuffmanNode<CharInfo>* cur = root;

		//int pos = 8;
		char ch = fgetc(fOut);


		int pos = 7;
		while (!feof(fOut))
		{
			if (ch & (1 << pos))
			{
				cur = cur->_right;
			}
			else
			{
				cur = cur->_left;
			}
			if (pos-- == 0)
			{
				pos = 7;
				ch = fgetc(fOut);          //继续读取字符
			}
			if (cur->_left == NULL&&cur->_right == NULL)
			{
				fputc(cur->_weight._ch, fIn);

				if (--count == 0)
				{
					break;
				}
				cur = root;
			}
		}

		cout << endl;

		fclose(fIn);
		fclose(fOut);
		fclose(fOutConfig);
	}
protected:

	void GenerateHuffmanCode(HuffmanNode<CharInfo>*root, string code) //生成huffman编码
	{
		if (root == NULL)
		{
			return;
		}
		if (root->_left)
		{
			GenerateHuffmanCode(root->_left, code + '0');
		}
		if (root->_right)
		{
			GenerateHuffmanCode(root->_right, code + '1');

		}
		if ((root->_left == NULL) && (root->_right == NULL))
		{
			_infos[root->_weight._ch]._code = code;  //？？？
		}
	}
	//{
	//	//回溯编码
	//	if (root)
	//	{
	//		GenerateHuffmanCode(root->_left, code);
	//		GenerateHuffmanCode(root->_right, code);
	//		if (root->_left == NULL&&root->_right == NULL)
	//		{
	//			string& code = _infos[root->_weight._ch]._code;//code为引用对象的别名
	//			HuffmanNode<CharInfo>* cur = root;
	//			HuffmanNode<CharInfo>* parent = root->_parent;
	//			while (parent)
	//			{
	//				if (parent->_left == cur)
	//				{
	//					code += '0';
	//				}
	//				else
	//				{
	//					code += '1';
	//				}
	//				cur = parent;
	//				parent = cur->_parent;  //回溯
	//			}
	//			reverse(code.begin(), code.end());   //逆置保存（位图来实现保存）
	//		}
	//	}
	//}


	bool ReadLine(FILE* fOut, string& line)
	{
		assert(fOut);
		char ch = fgetc(fOut);
		if (feof(fOut))
			return false;
		while (ch != '\n'&&!feof(fOut))
		{
			line += ch;
			ch = fgetc(fOut);
		}
		return true;

	}
protected:
	CharInfo _infos[256];
};




”tst.cpp“


#define _CRT_SECURE_NO_WARNINGS 1
#pragma  once
#include <iostream>
using namespace std;
#include "Compress.h"
#include <time.h>


void TestHuffmanTree()
{

	int a[10] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
	HuffmanTree<int>tree(a, 10, 0);
}
void TestCompress()
{

	FileCompress<int> f;
	double start_compress = clock();
	//f.Compress("little");
	f.Compress("Input.BIG");
	double finish_compress = clock();
	//f.UnCompress("little");
	f.UnCompress("Input.BIG");
	double finish_uncompress = clock();
	cout << "压缩时间是：" << finish_compress - start_compress << "ms" << endl;
	cout << "解压缩时间是：" << finish_uncompress - finish_compress << "ms" << endl;

}



int main()
{

	//TestHuffmanTree();
	TestCompress();

	system("pause");
	return 0;
}


7-2

#include <iostream>
using namespace std;

class Date
{
public:
	Date()
	{}
	Date& operator=(const Date&d)
	{
		//1.判断自己给自己赋值  2.返回值需要一个引用，确保进行连续赋值 3.拷贝构造函数中必须使用&
		if (this != &d)  
		{
			this->_year = d._year;
			this->_month = d._month;
			this->_day = d._day;
		}
		return  *this;
	}
private:
	int _year;
	int _month;
	int _day;

};
void Test()
{
	Date d1;
	Date d2(d1);  //调用拷贝构造函数

	Date d3;
	d3 = d1;  //调用赋值运算符构造函数
}   

int main()
{
	Test();
	system("pause");
	return 0;
}




class Array
{
public:
	Array(int capacity)
	{
		_arr = (int *)malloc(sizeof(int)*capacity);
		_capacity = capacity;
		_size = 0;
	}
	~Array()
	{
		if (_arr)
		{
			free(_arr);
			_arr = NULL;
			_size = 0;
			_capacity = 0;
		}
	}
private:
	int * _arr;
	size_t _size;
	int _capacity;
};


void Test()
{

	Array a1(10);
	Array a2(a1);    //会有浅拷贝问题，程序崩溃，因为析构两次空间  ，利用深拷贝进行解决
}


class Date
{
public:
	Date()
	{
		cout << "无参构造函数" << endl;
	}
	Date(const Date& d) //必须传引用，否则无穷递归
	{
		_year = d._year;
		_month = d._month;
		_day = d._day;  
	}
	~Date()
	{
		cout << "析构函数" << endl;
	}
private:
	int _year;
	int _month;
	int _day;
};
void Test()
{
	Date d1;
	Date d2(d1);  //调用拷贝构造函数
	Date d3 = d1; //调用拷贝构造函数  与上等价
}


class Date
{
public:
	////1.无参构造
	//Date()
	//{}
	////2.带参构造
	//Date(int year, int month, int day)
	//{
	//	_year = year;
	//	_month = month;
	//	_day = day;
	//}

     //3.带缺省参数的构造函数
	Date(int year = 2000, int month = 1, int day = 1)
	{
		_year = year;
		_month = month;
		_day = day;
	}
	//半缺省参数是构造函数
	Date(int year, int month = 1)
	{
		_year = year;
		_month = month;
		_day = 1;
	}
private:
	int _year;
	int _month;
	int _day;
};

void Test()
{
	Date d1;  //调用无参构造函数
	Date d2(2005, 1, 1);  //调用带参构造函数
	//Date d3();    //  这里非法，没有调用d3 的构造函数定义出d3；
	//cout << d1._year << "-" << d1._month << "-" << d1._day << endl;  //错误   成员变量为私有变量，不能在类外访问

	
}


//类内定义
//class Person
//{
//public:
//	void Display()
//	{
//		cout << _name << "-" << _sex << "-" << _age << endl;
//
//	}
//public:
//	char* _name;
//	char* _sex;
//	int _age;
//
//};


//类外定义
class Person
{
public:
	void Display();
public:
	char* _name;
	char* _sex;
	int _age;

};

 void Person::Display()
{
	 cout << _name << "-" << _sex << "-" << _age << endl;
}

void Test()
{
	Person p;
	p._name = "jack";
	p._sex = "男";
	p._age = 10;

	p.Display();

	Person* ptr = &p;
	ptr->_name = "peter";
	ptr->_sex = "女";
	ptr->_age = 13;

	ptr->Display();


}



//全缺省
int Add1(int a = 0, int b = 0)
{
	return a + b;

}
//半缺省
int Add2(int a, int b = 0)
{
	return a + b;

}
void Test()
{
	int ret1 = Add1();
	int ret2 = Add1(1);
	int ret3 = Add1(1, 1);
	int ret4 = Add2(2);
	int ret5 = Add2(2, 2);
	cout << "结果:" << ret1 << "-"<<ret2 <<"-"<< ret3 <<"-"<< ret4<<"-" << ret5<<"-" << endl;
}
int main()
{
	Test();
	system("pause");
	return 0;
}
int main()
{
	int i1 = 1;
	double d1 = 2.22;
	cout << "c++ type:" << "int->" << i1 << "double->" << d1 << endl;
	cout << "please input int and double:";
	cin >> i1 >> d1;
	cout << "c++ type:" << "int->" << i1 << "double->" << d1 << endl;
	system("pause");
	return 0;

}


int main()
{
	std::cout << "hello world" << std::endl;
	system("pause");
	return 0;
}

7-4



#define _CRT_SECURE_NO_WARNINGS

#include <iostream>
#include <string.h>
using namespace std;



//传统写法
class String
{
public:
	String()
		:_str(NULL)
	{}
	String(const char*str)
		:_str(new char[strlen(str)+1])  //必须开空间，否则析构崩溃
	{
		strcpy(_str, str);
	}
	String(const String& s)
		:_str(new char[strlen(s._str)+1])
	{
		strcpy(_str, s._str);
	}
	~String()
	{
		if (_str)
		{
			delete[] _str;
		}

	
	}
	String& operator=(const String&s)
	{
		if (this != &s)
		{
			/*delete[] _str;
			_str = new char[strlen(s._str) + 1];
			strcpy(_str, s._str);*/


			char*tmp = new  char[strlen(s._str) + 1];  //预防开辟空间失败
			strcpy(tmp, s._str);
			delete[] _str;
			_str = tmp;
		}
		return *this;
	}
	char *CStr()
	{
		return _str;
	}

private:
	char* _str;

};


//现代写法
class string
{
public:
	string(const char*str="")
		:_str(new char[strlen(str) + 1])  //必须开空间，否则析构崩溃
	{
		strcpy(_str, str);
	}
	string(const string& s)
		:_str(null)
	{
		string tmp(s._str);
		std::swap(_str, tmp._str);
	}
	~string()
	{
		if (_str)
		{
			delete[] _str;
		}


	}
	string& operator=(const string&s)
	{
		if (this != &s)
		{
			string tmp(s._str);
			std::swap(_str, tmp._str);
		}
		return *this;
	}
//  与上面等价
//	string& operator=(string s)
//	{
//		swap(this->_str, s._str);
//		return *this;
//	}

private:
	char* _str;

};

void Test()
{
	String s1("ssssssssssssss");
	String s2(s1);

	String s3("xxxxxxx");
	s3 = s1;

	//String s4;
	//String s5(s4);
	cout << s1.CStr() << endl;
	cout << s2.CStr() << endl;
	cout << s3.CStr() << endl;

}
int main()
{
	Test();
	system("pause");

	return 0;
}


7-7



#include <iostream>
using namespace std;
class A
{
public:
	A(int n)
	{
		value = n;
	}
	A( A& x)
	{
		value = x.value;
	}

	void Print()
	{
		std::cout << value << std::endl;
	}
	//~A();

private:
	int value;

};



void Test()
{
	A a = 10;
	A b = a;
	b.Print();
}
int main()
{
	Test();
	system("pause");
	return 0;
}

7-10


 #include <iostream>
using namespace std;



int main()
{
	printf("hello c-world\n");
	printf("****\n");
	printf("*\n");
	printf("*\n");
	printf("****\n");
	system("pause");
	return 0;


}

//数字排序不重复
int main()
{
	int i, j, k;
	for (i = 1; i < 5; i++)
	{
		for (j = 1; j < 5; j++)
		{
			for (k = 1; k < 5; k++)
			{
				if ((i!=j)&&(j!=k)&&(k!=i))
				{
					int num = i * 100 + j * 10 +k;
					printf("%d  ", num);

					//printf("%d,%d,%d\n", i, j, k);
				}
			}
		}
	}
	system("pause");
	return 0;
}
 
bool Find(int* matrix, int rows, int cols, int number)  //rows行,  cols列, number,要找的数字
{
	//bool found = false;


	if (matrix != NULL&&rows > 0 && cols > 0)
	{
		int row = 0;
		int col = cols- 1;
		while (row < rows && col > 0)
		{
			if (number == matrix[row*cols + col])
			{
				return true;
				break;
			}
			else if (number < matrix[row*cols + col])
			{
				--col;
			}
			else // if (number>matrix[row*cols + col])
			{
				++row;
			}
		}
	}
	return false;

}
int main()
{
	int arr[4][4] = { { 1, 2, 8, 9 }, { 2, 4, 9, 12 }, { 4, 7, 10, 13 }, { 6, 8, 11, 15 } };
	int ret1 = Find(*arr, 4, 4, 7);
	int ret2 = Find(*arr, 4, 4, 5);
	int ret3 = Find(*arr, 4, 4, 0);
	int ret4 = Find(*arr, 4, 4, 20);
	int ret5 = Find(arr[4], 4, 4, NULL);//传空指针相当于传0

	cout << ret1 << "-" << ret2 << "-" << ret3 << "-" << ret4 << "-" << ret5 << endl;



	system("pause");
	return 0;
}
int GetSize(int arr[])
{
	return sizeof(arr);
}
int main()
{
	int arr1[] = { 1, 2,3, 4, 5 };
	int size1 = sizeof(arr1);

	int *arr2 = arr1;
	int size2 = sizeof(arr2);

	int size3 = GetSize(arr1);

	//printf("%d,%d,%d", size1, size2, size3);  在c++中支持printf 输出，建议用cout
	cout << size1 << size2 << size3 << endl;

	system("pause");
	return 0;
}


7-11




#include <iostream>
using namespace std;


void ReplaceBlank(char string[], int len)   //string[]  字符数组  len   字符数组string的总容量
{
	if (string == NULL || len <= 0)
	{
		return;
	}
	int OLen = 0;
	int BCount = 0;
	int i = 0;
	遍历计算字符串的原长及空格的数目
	while (string[i] != '\0')
	{
		OLen++;
		if (string[i] == ' ')
		{
			BCount++;
		}

		i++;
	}
	计算字符串新长度
	int NewLen = BCount * 2 + OLen;
	int IndexOLen = OLen;
	int IndexNewLen = NewLen;
	转换空格
	while (IndexOLen >= 0 && IndexOLen < IndexNewLen)
	{
		if (string[IndexOLen] == ' ')
		{
			string[IndexNewLen--] = '0';
			string[IndexNewLen--] = '2';
			string[IndexNewLen--] = '%';
		}
		else
		{
			string[IndexNewLen--] = string[IndexOLen];
		}
		--IndexOLen;

	}

}

int main()
{
	string  str= "we are happy.";
	//int Lenstr = strlen(str) + 1;
	//ReplaceBlank(str[14],);
	system("pause");
	return 0;
}

int main()
{
	char str1[] = "hello";
	char str2[] = "hello";

	char* str3 = "hello";
	char* str4 = "hello";
	
	if (str1 == str2)
	{
		printf("str1 and str2 are same\n");
	}
	else
	{
		printf("str1 and str2 are not same\n");
	}

	if (str3 == str4)
	{
		printf("str3 and str4 are same\n");
	}
	else
	{
		printf("str3 and  str4 are not same\n");
	}
	system("pause");
	return 0;
}
 


7-17


  1 #include <stdio.h>                                                                                          
  2 #include <unistd.h>
  3 
  4 
  5 int main()
  6 {
  7     int count =2;
  8     alarm(1);
  9     for(;1;count++)
 10     {
 11         printf("count = %d\n",count);
 12     }
 13     return 0;
 14 }
~            




1 #include <stdio.h>                                                                                          
  2 #include <signal.h>
  3 #include <unistd.h>
  4 
  5 void printsigset(sigset_t *set){
  6     int i=0;
  7     for(;i<32;i++){
  8         if(sigismember(set,i)){
  9         putchar('1');
 10         }
 11         else{
 12         putchar('0');
 13         }
 14     }
 15     puts("");
 16 }
 17 int main()
 18 {
 19     sigset_t s,p;
 20     sigemptyset(&s);
 21     sigaddset(&s,SIGINT);
 22     sigprocmask(SIG_BLOCK,&s,NULL)
 23     while(1)
 24     {
 25         sigpending(&p);
 26         printsigset(&p);
 27         sleep(1);
 28     }
 29     return 0;
 30 }  
 
 
 
 
 7-21
 #include <iostream>
#include <string>
using namespace  std;

//异常的重新抛出
//重新抛出异常得注意释放空间的运用，否则内存泄漏如：new等的运用

class Exception
{
public:
	Exception(int errId=0, const char* errMsg="")
		:_errId(errId)
		, _errMsg(errMsg)
	{}

	void What() const
	{
		cout << "errId" << _errId << endl;
		cout << "errMsg" << _errMsg << endl;
	}

private:
	int _errId;     //错误码
	string _errMsg;  //错误信息

};


void Func1()
{
	throw string("Throw Func1 string");
}
void Func2()
{
	try
	{
		Func1();
	}
	catch (string& errMsg)
	{
		cout << errMsg << endl;
		//throw;   错误的
		//throw errMsg; 错误的

		//throw Exception(1, "Rethrow Exception");

		Exception e(1, "Rethrow Exception");
		throw e;
		
	}
}

void Func()
{
	try
	{
		Func2();
	}
	catch (Exception& e)
	{
		e.What();
	}
}
int main()
{
	Func();
	system("pause");
	return 0;
}

//
////异常
////即保证了在第一次catch后面的所有语句执行，并不一定会将每个的throw catch，除非只有catch（...）将catch一次，不论什么错误
//class Exception
//{
//public:
//	Exception(int errId, const char* errMsg)
//		:_errId(errId)
//		,_errMsg(errMsg)
//	{}
//
//	void What() const
//	{
//		cout << "errId" << _errId << endl;
//		cout << "errMsg" << _errMsg << endl;
//	}
//	
//private:
//	int _errId;     //错误码
//	string _errMsg;  //错误信息
//		
//};
//
//
//void Func1(bool isThrow)
//{
//	if (isThrow)
//	{
//		throw Exception(1, "抛出Exception对象");
//	}
//	printf("Func1(%d)\n", isThrow);
//}
//void Func2(bool isThrowString,bool isThrowInt)
//{
//	if (isThrowString)
//	{
//		throw string("抛出string对象");
//	}
//	if (isThrowInt)
//	{
//		throw 7;
//	}
//	printf("Func2(%d,%d)\n", isThrowString, isThrowInt);
//}
//void Func()
//{
//	try
//	{
//		Func1(true);
//		Func2(false,true);
//	}
//	catch (const string& errMsg)  //catch  string
//	{
//		cout << "Catch string Obiect:" << errMsg << endl;
//	}
//	catch (const int& errId)  //catch   int
//	{
//		cout << "Catch int Obiect:" << errId << endl;
//	}
//
//	catch (const Exception& e)     //
//	{
//		e.What();    //const Exception*  
//	}
//
//	catch (...)  //未知异常
//	{
//		cout << "未知异常" << endl;
//	}
//	printf("Func()\n");
//}
//int main()
//{
//	Func();
//	system("pause");
//	return 0;
//}

7-23


#include <stdio.h>

判断大端小端    例如ox11 22 33 44； 内存中：
大端：高字节放低地址，低字节放高地址（高低高低）11 22 33 44
小端：高字节放高地址，低字节放低地址（高高低低）44 33 22 11

1.用联合
union UN
{
	int i;
	char c;
}un;
int Check_sys()
{
	un.i = 1;
	if (un.c == 1)
		return 0;  //小端
	else
		return 1;  //大端
}

2.用int i=1；
int Check_sys()
{
	int a = 1;
	char* p = &a;
	//char* p = (char*)&a;
	if (*p == 1)
	{
		return 0; //小端
	}
	else
	{
		return 1;//大端
	}
}

int main()
{
	int ret = Check_sys();
	if (ret == 0)
	{
		printf("little\n");
	}
	else
	{
		printf("big\n");
	}
	system("pause");
	return 0;
}



#define _CRT_SECURE_NO_WARNINGS 1

#include <iostream>
#include <string.h>
using namespace std;


 

//string 的现代写法
class string
{
public:
	string(char* str="")
		:_str(new char[strlen(str) + 1])
	{
		strcpy(_str, str);
	}
	string(const string& s)
		:_str(null)
	{
		string tmp(s._str);
		std::swap(_str, (char*)s._str);

	}
	string& operator=(const string& s)
	{
		if (this != &s)
		{
			string tmp(s._str);
			std::swap(_str, (char*)s._str);
		}
		return *this;
	}

	~string()
	{
		if (_str)
		{
			delete[] _str;
		}
	}

private:
	char* _str;     //字符串
	

};


//写时拷贝+引用计数
//普通的引用计数、静态引用计数都有问题
//用引用计数指针
class String
{
public:
	String(char* str = "")
		:_str(new char[strlen(str) + 1])
		,_pRefCount(new int(1))
	{
		strcpy(_str, str);
	}
	String(const String& s)
		:_str(s._str)
		,_pRefCount(s._pRefCount)
	{
		++(*_pRefCount);
	}
	/*String& operator=(const String& s)
	{
		if (this != &s)
		{
			_str = s._str;
			_pRefCount = s._pRefCount;
		}
		return *this;
	}*/        //有影响 对s4

	~String()
	{
		if (--(*_pRefCount)==0)
		{
			delete[] _str;
			delete _pRefCount;
		}
	}

private:
	char* _str;     //字符串
	int* _pRefCount;  //引用计数指针

};

void Test1()
{
	String  s1("xxxxxxxxxxxx");
	String  s2(s1);

	String  s3("ssssssssssssssss");
	String  s4(s3);

	String s5;
	s5 = s4;
}


int main()
{

	Test1();
	system("pause");
	return 0;
}




     
7-25

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>
#include <string.h>
#include <windows.h>


//从两边聚集中间打印字符串
int main()
{
	int i = 0;
	char arr1[] = "welcome to bit!";
	char arr2[] = "###############";
	int size = strlen(arr1);
	int left = 0;
	int right = size - 1;
	for (i = 0; i < (size + 1) / 2; i++)
	{
		arr2[left] = arr1[left];
		arr2[right] = arr1[right];
		left++;
		right--;
		Sleep(1000);
		printf("%s\n", arr2);
	}

	system("pause");
	return 0;
}


//模拟用户密码登录
//int main()
//{
//	int i = 0;
//	char input[10];
//	for (i = 0; i < 3; i++)
//	{
//		printf("请输入密码：\n");
//		scanf("%s", input);
//		if (strcmp("12345",input) == 0)
//		{
//			printf("登陆成功！\n");
//
//			break;
//		}
//		else
//		{
//			printf("密码错误！再次输入：");
//		}
//	}
//	if (i == 3)
//	{
//		return 0;
//	}
//	printf("取钱成功！\n");
//	system("pause");
//	return 0;
//}




epoll_server

  #include <stdio.h>                                                                                                                
  2 #include <stdlib.h>
  3 #include <string.h>
  4 #include <unistd.h>
  5 #include <fcntl.h>
  6 #include <sys/socket.h>
  7 #include <netinet/in.h>
  8 #include <sys/epoll.h>
  9 
 10 
 11 
 12 static int startup(const char*_ip,int _port)
 13 {
 14     int sock=socket(AF_INET,SOCK_STREAM,0);
 15     if(sock<0)
 16     {
 17         perror("socket");
 18         exit(2);
 19     }
 20     struct sockaddr_in local;
 21     local.sin_family=AF_INET;
 22     local.sin_port=htons(_port);
 23     local.sin_addr.s_addr=inet_addr(_ip);
 24 
 25     if(bind(sock,(struct sockaddr*)&local,sizeof(local))<0)
 26     {
 27         perror("bind");
 28         exit(3);
 29     }
 30     if(listen(sock,5)<0)
 31     {
 32         perror("listen");
 33         exit(4);
 34     }  
 35     return sock;
 36 }
 37 
 38 static int set_noblock(int sock)
 39 {
 40     int fl=fcntl(sock,F_GETFL);
 41     return fcntl(sock,F_SETFL,fl | O_NONBLOCK);
 42 }
 43 static void usage(const char*proc)
 44 {
 45     printf("Usage: %s [ip] [port]\n",proc);
 46 }
 47 int main(int argc,char *argv[])
 48 {
 49     if(argc!=3)
 50     {
 51         usage(argv[0]);
 52         exit(1);
 53     }
 54     //create listen socket
 55     int listen_sock=startup(argv[1],atoi(argv[2]));
 56     int epfd=epoll_create(256);
 57     if(epfd<0)
 58     {
 59         perror("epoll_create");
 60         exit(5);
 61     }
 62     
 63     struct epoll_event _ev;
 64     _ev.events=EPOLLIN;
 65     _ev.data.fd=listen_sock;
 66  epoll_ctl(epfd,EPOLL_CTL_ADD,listen_sock,&_ev);
 68 
 69     struct epoll_event _ready_ev[128];
 70     int _ready_evs=128;
 71     int _timeout=-1;  //block
 72 
 73     int nums=0;
 74     int done=0;
 75     while(!done)
 76     {
 77         switch(nums=epoll_wait(epfd,_ready_ev,_ready_evs,_timeout))
 78         {
 79             case 0:
 80               printf("timeout...\n");
 81               break;
 82             case -1:
 83                 perror("epoll_wait");
 84                 break;
 85             default:
 86                 {
 87                     int i=0;
 88                     for(;i<nums;i++)
 89                     {
 90                         int _fd= _ready_ev[i].data.fd;
 91                         if(_fd==listen_sock&&_ready_ev[i].events & EPOLLIN)
 92                         {
 93                             //get a new link...
 94                             struct sockaddr_in peer;
 95                             socklen_t len=sizeof(peer);
 96                             int new_sock=accept(listen_sock,(struct sockaddr*)&peer,&len);
 97                             if(new_sock>0)
 98                             {
 99                                 printf("client info,socket:%s:%d\n",\
100                                        inet_ntoa(peer.sin_addr),ntohs(peer.sin_port));                                        
101                                 _ev.events=EPOLLIN | EPOLLET;  //ET
102                                 _ev.data.fd=new_sock;
103                                 set_noblock(new_sock);
104 
105                                 epoll_ctl(epfd,EPOLL_CTL_ADD,new_sock,&_ev);
106                             }
107                         }
108                         else
109                         {
110                             if(_ready_ev[i].events & EPOLLIN)
111                             {
112                                 char buf[12400];
113                                 memset(buf,'\0',sizeof(buf));
114                                 
115                                 //read/write
116                                 ssize_t _s=recv(_fd,buf,sizeof(buf)-1,0);//while need recv done...
117 
118                                 if(_s>0)
119                                 {
120                                     printf("client# %s\n",buf);
121                                     _ev.events=EPOLLOUT | EPOLLET;
122                                     _ev.data.fd=_fd;
123                                     epoll_ctl(epfd,EPOLL_CTL_MOD,_fd,&_ev);
124                                 }
125                                 else if(_s==0)
126                                 {
127                                     printf("client close...\n");
128                                     epoll_ctl(epfd,EPOLL_CTL_DEL,_fd,NULL);
129                                     close(_fd);
130                                 }
131                                 else
132                                 {
133                                     perror("recv");  
                            	    }
135                             }
136                             else if(_ready_ev[i].events &EPOLLOUT)
137                            {
138                                 const char*msg="HTTP/1.1 200 OK\r\n\r\n<h1>hello world =_=||</h1>\r\n";
139                                 send(_fd,msg,strlen(msg),0);
140                                 epoll_ctl(epfd,EPOLL_CTL_DEL,_fd,NULL);
141                                 close(_fd);
142                             }
143                         }
144                     }
145                 }
146                 break;
147         }
148     }
149 
150 }  
                      

  8-7
  
  
  #include <iostream>
using namespace std;

//c语言
//非递归

int bsearchWithoutRecursion(int array[], int low, int high, int target)
{
	while (low <= high)
	{
		int mid = (low + high) / 2;
		if (array[mid]>target)
			high = mid - 1;
		else if(array[mid]<target)
			low = mid + 1;
		else//findthetarget
			return mid;
	}
	//the array does not contain the target
	return-1;
}


//递归
int binary_search(const int arr[], int low, int high, int key)
{
	int mid = low + (high - low) / 2;
	if (low>high)
		return -1;
	else{
		if (arr[mid] == key)
			return mid;
		else if (arr[mid]>key)
			return binary_search(arr, low, mid - 1, key);
		else
			return binary_search(arr, mid + 1, high, key);
	}
}


//c++
int binSearch(const int *Array, int start, int end, int key)
{
	int left, right;
	int mid;
	left = start;
	right = end;
	//注释中为递归算法，执行效率低，不推荐
	/*
	if(key<Array[mid])
	{
	return(binSearch(Array,left,mid,key));
	}
	else if(key>Array[mid])
	{
	return(binSearch(Array,mid+1,right,key));
	}
	else
	return mid;
	*/

	while (left <= right)
	{
		mid = (left + right) / 2;
		if (key == Array[mid])  return mid;
		else if (key<Array[mid]) right = mid - 1;
		else if (key>Array[mid ]) left = mid + 1;
	}
	return -1;
	//找不到就返回-1
}
 

struct BinaryTreeNode
{
	int _value;
	BinaryTreeNode* _left;
	BinaryTreeNode* _right;
};
int TreeDepth(BinaryTreeNode* pRoot)
{
	if (pRoot == NULL)
	{
		return 0;
	}
	int nleft = TreeDepth(pRoot->_left);
	int nright = TreeDepth(pRoot->_right);

	return (nleft>nright)?(nleft+1):(nright+1);
}

//回文数的测试代码
int main()
{
	int i = 0, k = 12321, p, a[10], tmp, begin, end;
	cout << "please input number:>"<<endl;
	cin >> k;
	p = k;
	while (p)
	{
		tmp = p % 10;
		a[i] = tmp;
		p = p / 10;
		++i;
	}
	 begin = 0;
	 end = i-1;
	 while (begin < end)
	 {
		 if (a[begin] != a[end])
		 {
			 break;
		 }
		 else
		 {
			 begin++;
			 end--;
		 }
	 }
	 if (begin < end)
	 {
		 cout << "假的"<<endl;
	 }
	 else
	 {
		 cout << "真的" << endl;
	 }
	 cout << "i" << i << endl;
	 cout << k<<endl;

	system("pause"); 
	return 0;
}

33,1-4        27%

 
                       
8-16#include <iostream>                                                         
  2 #include <sys/socket.h>
  3 #include <sys/types.h>
  4 #include <string.h>
  5 #include <arpa/inet.h>
  6 
  7 class server{
  8     public:
  9         server()
 10         {
 11             sock_fd=-1;
 12             port=8080;
 13             ip="192.168.0.114";
 14         }
 15 
 16         int server_init()
 17         {
 18             sock_fd=socket(AF_INET,SOCK_DGRAM,0);
 19             if(sock_fd==-1)
 20             {   
 21                 return 1;
 22             }
 23             print_log("creat socket success");
24             struct sockaddr_in server_sock;
 25             bzero(&server_sock,sizeof(server_sock));
 26             server_sock.sin_family=AF_INET;
 27             server_sock.sin port=htons(port);
 28             server_sock.sin_addr.s_addr=htonl(INADOR_ANY);
 29             socklen_t len=sizeof(sockaddr_in);
 30             if(bind(sock_fd,(struct sockaddr*)&server_sock,len)==-1)
 31             {
 32                 return 2;   
 33             }
 34             print_log("bind socket success");
 35             return 0;
 36         }
 37 
 38         void get_msg(std::string &msg)
 39         {
 40             char buf[1024];                                                 
 41             memset(buf,'\0',sizeof(buf));
 42             struct sockaddr_in cli;
 43             socklen_t len-sizeof(struct sockaddr_in);
    int ret=recvfrom(sock_fd,buf,sizeof(buf)-1,0,(struct sockaddr*)&    cli,&len);
 45             if(ret!=-1){
 46             print_log("get  msg success");
 47             msg=buf;
 48             std::cout<< "client ip is: "<< inet_ntoa(cli.sin_addr)<<std::end    l;
 49             }else{
 50                 msg="";
 51             }
 52         }
 53 
 54         void send_msg()
 55         {
 56             //do nothing
 57         }
 58 
 59         ~server()
 60         {
 61             close(sock_fd);   
 
  62         }
 63 
 64     private:
 65         int sock_fd;
 66         std::string ip;
 67         short int port;
 68 };
 69 
 70 
 71 int  main()
 72 {
 73     server ser;
 74     ser.server_init();
 75     std::string msg;
 76     while(1){
 77         ser.get_msg(msg);
 78         std::cout<<msg<<std::endl;
 79     }
 80     return 0;
 81 }        
