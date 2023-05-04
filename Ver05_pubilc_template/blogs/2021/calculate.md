# 关于项目

## 起因

- 受人委托，帮忙写一个作业，就这么简单

## 资料查阅

- 好像也没啥需要查的资料，就一个差集的定义之前没接触过

# 项目解析

- 没啥解析了，比较简单，直接看源码！

# 项目完整代码

##### calculate.cpp

``` C++
#include <iostream>
#include <stdlib.h>


#include "inter.h"
#include "uni.h"
#include "diff.h"

using namespace std;



//主函数部分
int main(void)   
{
	//声明函数定义，在函数被使用之前要先对函数进行声明，才可以保证函数的正常使用
	void inter(int* arr_a, int* arr_b, int a_le, int b_le); 
	void uni(int* arr_a, int* arr_b, int a_le, int b_le);
	void diff(int* arr_a, int* arr_b, int a_le, int b_le);
	int judgement(int* array, int len);
	//定义两个数组，作为集合
	int* array_a, * array_b;  


	//定义两个整型变量，表示两个数组的长度
	int len_a, len_b;


	//输入数组的长度
	cout << "please input the len of array_a:";  
	cin >> len_a;
	cout << "please input the len of array_b:";
	cin >> len_b;
	cout << endl;


	//对数组进行初始化
	array_a = (int*)malloc(sizeof(int) * len_a);
	array_b = (int*)malloc(sizeof(int) * len_b);


	//对数组元素进行输入
	judgement_a:cout << "please enter the elements of array_a:";
	for (int i = 0; i < len_a; i++)
	{
		cin >> array_a[i];
	}
	if (judgement(array_a, len_a) == 1)
	{ 
		cout << "\033[31;4m******WARNING******\033[0m\n" << endl;  //颜色转换方法
		cout << "\033[31mthe inputed array has repeated elements!\033[0m";
		cout << "\033[31mplease input agagin!\033[0m" << endl;
		goto judgement_a; 
	}
	cout << endl;


	judgement_b:cout << "please enter the elements of array_b:";
	for (int i = 0; i < len_b; i++)
	{
		cin >> array_b[i];
	}


	if (judgement(array_b, len_b) == 1) 
	{
		cout << "\033[31;4m******WARNING******\033[0m\n" << endl;  //颜色转换方法
		cout << "\033[31mthe inputed array has repeated elements!\033[0m";
		cout << "\033[31mplease input agagin!\033[0m" << endl;
		goto judgement_b; 
	}
	cout << endl;
	cout << endl;


	//测试用的，为了检验之前的代码是否正常运行，程序中适当写一下测试代码，有助于检测分段整个程序是否正常
	/*cout << "test:" << endl;
	for (int i = 0; i < len_a; i++)
	{
		cout << array_a[i];
		cout << " ";
	}
	cout << endl;

	for (int i = 0; i < len_b; i++)
	{
		cout << array_b[i];
		cout << " ";
	}
	cout << endl;*/



	//getchar放置在这里的目的是：排除之前cin输入数值后按下的回车的影响
	//这是一个刷新缓冲区的知识点，在两个连续的输入之间不做处理，容易导致后面的输入的内容读取的是：前面输入内容之后所按下的“回车”
	getchar();


	//定义choice 该变量的值决定了我们选择哪一种集合的运算
	int choice;
	again:printf("please input your choice (1:inter;2:uni;3:diff;):");
	cin >> choice;


	//switch-case语句，根据choice的值选择我们使用哪一种集合运算
	switch (choice)
	{
	case 1:
		inter(array_a, array_b, len_a, len_b);  //函数调用
		break;
	case 2:
		uni(array_a, array_b, len_a, len_b);
		break;
	case 3:
		diff(array_a, array_b, len_a, len_b);
		break;
	default://如果输入的值不属于我们的选择范围则报错
		cout << endl;
		cout << "\033[31;4m******WARNING******\033[0m\n" << endl;  //颜色转换方法
		cout << "\033[31mthe choice you chose is wrong!\033[0m";
		cout << "\033[31mplease input agagin!\033[0m"<<endl; 
		cout << endl;
		goto again;
	}

	return 0;
}



int judgement(int* array, int len) 
{
	for (int i = 0; i < len; i++) 
	{
		for (int j = i + 1; j < len; j++) 
		{
			if (array[i] == array[j])
			{
				return 1;
			}
		}
	}

	return 0;
}
```
##### inter.h

``` C++
//求交集的函数

#include <iostream>
#include <stdlib.h>

using namespace std;

#ifndef _INTER_H_
#define _INTER_H_

void inter(int* arr_a, int* arr_b, int a_le, int b_le)
{

	//因为是求集合的交集，交集中元素的数量一定不会比两者中大的哪一方的数量更大，所有我们取新数组的长度为两这中大的那一方
	int len_c;
	len_c = a_le > b_le ? a_le : b_le; 


	//定义新数组并初始化
	int* array_c;
	array_c =(int*)malloc(sizeof(int) * len_c);

	int i;
	int j;
	int k = 0;

	for ( i= 0; i < a_le; i++)//遍历数组a
	{
		for ( j= 0; j < b_le; j++)//遍历数组b
		{
			if (arr_a[i] == arr_b[j])  //如果数组a和数组b中的元素相同，那么该元素就属于交集中的元素，就把他放入新建的数组中
			{
				array_c[k] = arr_a[i];
				k++;
			}
		}
	}

	//冒泡排序算法，升序排列数组
	int a;
	int b;
	int temp;
	for (b = 0; b < k - 1; b++)
	{
		for (a = 0; a < k - 1 - b; a++)
		{
			if (array_c[a] > array_c[a + 1])//冒泡排序算法，如果想要降序排列数组的话，就更改成小于号
			{
				temp = array_c[a];
				array_c[a] = array_c[a + 1];
				array_c[a + 1] = temp;
			}
		}
	}


	//输出最后的集合
	cout << "inter array_a and array_b is:";
	for (int i = 0; i < k; i++)
	{
		cout << array_c[i] << " ";
	}
	cout << endl;
}

#endif
```
##### uni.h

``` C++
#include <iostream>
#include <stdlib.h>

using namespace std;

#ifndef _UNI_H_
#define _UNI_H_

void uni(int* arr_a, int* arr_b, int a_le, int b_le)
{
	int count = a_le;//我们先把数组arr_a中的元素全部放到array_c中，那么数组arr_b中的元素再往数组array_c后面排序的话，下标就从a_le开始，因此我们先定义这个变量——第40行

	int flag;  //设置一个标志位

	int* array_c;  //array_c的定义与初始化
	array_c=(int*)malloc(sizeof(int)* (a_le + b_le)); //数组的长度不可能比a_le + b_le还大，所以a_le + b_le够用，并且不浪费内存

	//求并集，第一步，把arr_a的全部放到array_c中
	for (int i = 0; i < a_le; i++)//遍历数组arr_a
	{
		array_c[i] = arr_a[i];   
	}

	// 求并集，第二步，把array_c中没有，但是arr_b中有的元素放到array_c中
	for (int i = 0; i < b_le; i++) //遍历arr_b
	{
		flag = 1;
		for (int j = 0; j < a_le; j++)  //遍历array_c
		{

			if (arr_b[i] == array_c[j])
			{
				flag = 0;//标志位的作用就是，说明arr_b中的元素，他已经在array_c中了，我们做好标记，通过if语句，将其不添加到array_c中
			}

		}

		if (flag==1)  //标志位的作用表现出来了
		{
			array_c[count] = arr_b[i];   //往已经把array_a的全部插入array_c中后，下一个位置就是array_a的长度
			count++;
		}
	}

	//冒泡排序  作用与求交集的一个样
	int a;
	int b;
	int temp;
	for (b = 0; b < count - 1; b++)
	{
		for (a = 0; a < count - 1 - b; a++)
		{
			if (array_c[a] > array_c[a + 1])
			{
				temp = array_c[a];
				array_c[a] = array_c[a + 1];
				array_c[a + 1] = temp;
			}
		}
	}


	//输出
	cout << "uni array_a and array_b is:";
	for (int i = 0; i < count; i++)
	{
		cout << array_c[i] << " ";
	}
	cout << endl;
}
#endif
```
##### diff.h

```C++
#include <iostream>
#include <stdlib.h>

using namespace std;

#ifndef _DIFF_H_
#define _DIFF_H_

void diff(int* arr_a, int* arr_b, int a_le, int b_le)
{

	int i;
	int j;

	//定义并初始化三个新的数组
	int* array_c;
	array_c=(int*)malloc(sizeof(int) * a_le);//先把arr_a中的元素全部放入，这个是一个中间的过渡数组


	int* array_d;
	array_d = (int*)malloc(sizeof(int) * a_le);//用与存放arr_a与arr_b的交集，在求差集的时候有用


	int* array_e;
	array_e = (int*)malloc(sizeof(int) * a_le); //最终的结果所保存的数组



	//遍历arr_a，把arr_a中的全部元素先放到array_c中
	for (int i = 0; i < a_le; i++)
	{
		array_c[i] = arr_a[i];
	}


	//先找到arr_a和arr_b的交集，放到array_d中去
	int xx = 0;
	for (int i = 0; i < a_le; i++)
	{
		for (int j = 0; j < b_le; j++)
		{
			if (arr_a[i] == arr_b[j])
			{
				array_d[xx] = arr_a[i];
				xx++;
			}
		}
	}

	//测试用的代码
	//cout << "test:" << endl;
	//for (i = 0; i < xx; i++)
	//{
	//	cout << array_d[i] << " ";
	//}
	//cout << endl;



	int x = 0;
	for ( i= 0; i < a_le; i++) //遍历d (交集)
	{
		int flag = 0;//定义一个标志位
		for (j= 0; j < xx; j++) //遍历c（arr_a）
		{
			if (array_d[j] == array_c[i])//交集array_d和array_d中都有的元素，我们在求交集的时候不要这些元素，因此我们做一个标记flag = 1
			{
				flag = 1;
				break;
			}
		}

		if (flag == 0)  //flag = 0：那么不符合我们之前的要求，需要将其加入到最终的结果数组array_e中
		{
			//cout << "test:" << array_c[i] << endl;
			array_e[x++] = array_c[i];
		}
	}

	//测试代码
	//cout << "test:" << endl;
	//cout << x << endl;

	//for (i = 0; i < x; i++)
	//{
	//	cout << array_e[i] << " ";
	//}
	//cout << endl;

	//冒泡排序   升序
	int a;
	int b;
	int temp;
	for (b = 0; b < x - 1; b++)
	{
		for (a = 0; a < x - 1 - b; a++)
		{
			if (array_c[a] > array_c[a + 1])
			{
				temp = array_c[a];
				array_c[a] = array_c[a + 1];
				array_c[a + 1] = temp;
			}
		}
	}


	cout << "diff array_a and arrar_b is:";
	for (int i = 0; i < x; i++)
	{
		cout << array_e[i] << " ";
	}
	cout << endl;
}

#endif
```

# 关于项目的思考

- 在对差集的计算中，算法设计还不够最优化，为了完成操作，定义了太多的数组，占用过多的内存空间，不是最优的算法。