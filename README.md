# test.c.code
#include <stdio.h>

int main()
{
	char a = 3;
	char b = 127;
	char c = a+b;
	printf("%d\n",c);
	/*char c = 1;
	printf("%u\n",sizeof(c));
	printf("%u\n",sizeof(+c));
	printf("%u\n",sizeof(!c));*/
	return 0;
}
int main()
{
	int a = 0x11223344;
	int* pa = &a;
	*pa = 0;
	/*char* pc = &a;
	*pc = 0;*/
	return 0;
}
int main()
{
	int a = 0x11223344;
	int* pa = &a;
	char* pc = &a;
	printf("%p\n",pa);
	printf("%p\n",pa+1);//int* pa->pa+1 指针步长为4
	printf("%p\n",pc);
	printf("%p\n",pc+1);//char* pc->pc+1 指针步长为1
	return 0;
}
//对比int与char在地址改变时的不同
int main()
{
	int arr[10]={0};
	int* p = arr;
	/*char* p = arr;*/
	int i = 0;
	for(i=0;i<10;i++)
	{
		*(p+i) = 1;
	}
	return 0;
}
//野指针
int* test()
{
	int a = 10;
	return &a;
//出了函数&a的空间被释放，不在属于int* p
int main()
{
	int* p;//指针变量未初始化
	*p = 20;
	int arr[10] = {0};
	int* p = arr;
	int i = 0;
	for(i=0;i<12;i++)//p循环12次超出arr空间的范围
	{
		p++;
	}
	int* p = test();
	*p = 20;
	return 0;
}
int main()
{
	int a = 10;
	int* pa = &a;
	pa = NULL;
	if(*pa != NULL)//使用指针之前线判断指针是否为空
	{
	    *pa = 20;
	}
	printf("%d\n",*pa);
	return 0;
}
int main()
{
	int arr[10]={1,2,3,4,5,6,7,8,9,10};
	int i =0;
	int* p = &arr[9];
	int sz = sizeof(arr)/sizeof(arr[0]);
	for(i=0;i<5;i++)
	{
		printf("%d ",*p);
		p -= 2;
	}
	//for(i=0;i<sz;i++)
	//{
	//	printf("%d ",*p);
	//	p++;//或者p = p+1;
	//}
	return 0;
}
int main()
{
	char ch[5]={0};
	int arr[10]={1,2,3,4,5,6,7,8,9,10};
	printf("%d\n",&arr[9]-&arr[0]);
	printf("%d\n",&arr[0]-&arr[9]);
	printf("%d\n",&arr[9]-&ch[0]);//不可行，指针只有指向同一空间才可使用
	return 0;
}
int my_strlen (char* str)
{
	char* start = str;
	char* end = str;
    while(*end != '\0')
	{
		end++;
	}
	return end - start;
}
int main()
{
	char arr[]="bit";
	int len = my_strlen(arr);
	printf("%d\n",len);
	return 0;
}
//指针访问数组
int main()
{
	int arr[10] = {1,2,3,4,5,6,7,8,9,10};
	int i = 0;
	int* p = arr;
	for(i=0;i<10;i++)
	{
		*(p+i) = i;
	}
	for(i=0;i<10;i++)
	{
		printf("%d ",*(p+i));
		//printf("%d ",arr[i]);
	}
	printf("\n");
	for(i=0;i<10;i++)
	{
	    printf("%p ===== %p\n",p+i,&arr[i]);
	}
	return 0;
}
//二级指针
int main()
{
	int a = 10;
	int b = 20;
	int c = 30;
	int* arr[]={&a,&b,&c};
	int i = 0;
	for(i=0;i<3;i++)
	{
	    printf("%d ",*(arr[i]));
	}
	int a = 10;
	int* pa = &a;
	int** ppa = &pa;//二级指针
	int*** pppa = &ppa;
	printf("%d\n",***pppa);
	return 0;
//创建一个整形数组实现init（）初始化为0，实现print（）打印每一个元素，实现reverse（）函数完成数组元素的逆置
void Init (int arr[],int sz)
{
	int i = 0;
	for(i=0;i<sz;i++)
	{
		arr[i] = 0;
	}
}
void print (int arr[],int sz)
{
	int i = 0;
	for(i=0;i<sz;i++)
	{
		printf("%d ",arr[i]);
	}
	printf("\n");
}
void reverse (int arr[],int sz)
{
	int left = 0;
	int right = sz-1;
	while(left<right)
	{
	   int tmp = arr[left];
	   arr[left] = arr[right];
	   arr[right] = tmp;
	   left++;
	   right--;
	}
}
int main()
{
	int arr[10]={1,2,3,4,5,6,7,8,9,10};
	int sz = sizeof(arr)/sizeof(arr[0]);
    /*Init(arr,sz);*/
	print(arr,sz);
	reverse(arr,sz);
	print(arr,sz);
	return 0;
}
两个数组进行交换元素（数组一样大）
int main()
{
	int arr1[]={1,2,3,4,5};
	int arr2[]={6,7,8,9,0};
	int sz = sizeof(arr1)/sizeof(arr1[0]);
	int i = 0;
	int tmp =0;
	for(i=0;i<sz;i++)
	{
		tmp = arr1[i];
		arr1[i] = arr2[i];
		arr2[i] = tmp;
	}
	return 0;
}
int main()
{
	/*int a = 0x11223344;
	char* pc = (char*)&a;
	*pc = 0;*/
	/*printf("%x\n",a);*/
	/*int arr[]={1,2,3,4,5};
	short* p = (short*)arr;
	int i = 0;
	for(i=0;i<4;i++)
	{
		*(p+i) = 0;
	}
	for(i=0;i<5;i++)
	{
		printf("%d\n",arr[i]);
	}*/
    return 0;
}
