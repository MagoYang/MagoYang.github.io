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

