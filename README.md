# MagoYang.github.io
Mycode~博客
# include <stdio.h>
#define n 20

int main()
{
	int cur = n;  //当下共有的瓶子数
	int count = n;//当下共喝的汽水瓶数
		while (cur > 1)
	 {
		int x;
		x = cur % 2;
		count += cur / 2;
		cur = cur / 2 + x;
	}
	
	printf("总共喝汽水：%d\n", count);
	system("pause");
	return 0;
}
注：当钱数为0或1元时，会直接用printf函数输出原数，其他则会进入循环判断
