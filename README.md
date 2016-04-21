# MagoYang.github.io
Mycode~博客

//字符串连接函数 strcat
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


//strstr函数   思路：在字符串s1中查找s2的第一次出现的位置，否则返回null
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


1.模拟实现strcmp 
				/*C/C++函数，比较两个字符串.设这两个字符串为str1，str2，若str1 == str2，则返回零；若str1>str2，则返回正数；
				若str1<str2，则返回负数。*/
2.模拟实现memcpy  c和c++使用的内存拷贝函数，
                memcpy函数的功能是从源src所指的内存地址的起始位置开始拷贝n个字节到目标dest所指的内存地址的起始位置中。
//3.模拟实现memmove


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

