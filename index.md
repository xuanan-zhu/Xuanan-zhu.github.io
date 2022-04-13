## 康康你发现了什么？欢迎来到我的博客！

这是一个小白从入门到出家的故事，一个是为了记录，另外一个是为了分享，学习点点滴滴的快乐！

4.13
今天我们来讲讲递归~
递归可以理解成把复杂问题的问题简单化，把一个问题拆解，一步步去解决。
注意写代码的时候尽量少用++x,x++,对于小白来说这是比较犯错的
简单的递归例子：

![image](https://user-images.githubusercontent.com/84304647/163237833-8f4b6269-efdc-4920-9b2b-9613905f4971.png)



但是这个代码会中途中断，这就涉及到栈溢出的概念


![image](https://user-images.githubusercontent.com/84304647/163238006-6a87ee16-c165-4840-8444-e00a6f6c3a30.png)
![image](https://user-images.githubusercontent.com/84304647/163238040-fcd2c9f5-abf2-49e5-b4c9-3a0a9dbb27d7.png)



在栈区我们存储局部变量和形参，main函数在里面开辟空间用来存储局部变量，而调用函数的时候就会开辟空间给形参，调用完自动销毁，而调用不终止并且一直在调用会一直开辟空间直到溢出，这就是中断的原因。



![image](https://user-images.githubusercontent.com/84304647/163238674-81009672-d4e7-4341-b6e6-11aeeef001b8.png)

简单的递归例子：
1、输入数字并分别打印出来
```
void print(unsigned int);
int main()
{
	unsigned int input;
	scanf("%u", &input);
	print(input);
	return 0;
}

void print(unsigned int x)
{
	if (x > 9) 
	{
		print(x / 10);
	}
	printf("%d", x % 10);
}
```
2、不用产生变量实现strlen()功能
```
int main()
{
	char arr[] = "hello";
	//printf("%d", strlen(arr));
	printf("%d\n", my_strlen(arr));
	printf("%s", (arr + 1));
	return 0;
}

int my_strlen(char* p)
{
	if (*p != '\0')
	{
		return(1+my_strlen(p+1));
	}
	else
	{
		return(0);
	}
}
```
3、斐波那契数列的递归与迭代的对比
```
int fib(int n)
{
	if (n <= 2)
	{
		return 1;
	}
	else
		return fib(n - 1) + fib(n - 2);
}

int fibxun(int n)
{
	int a = 1;
	int b = 1;
	int c = 0;
	if (n < 3)
	{
		return(1);
	}
	while (n>=3 && --n>=2)
	{
		c = a + b;
		a = b;
		b = c;
	}
	return(c);
}
```
在斐波那契数列的函数我们不难看出递归远远比不上迭代，因为做出了很多重复计算！
今天的分享就到这里
4.14
