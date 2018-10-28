**Things  that I think useful but maybe overlook**
**1.三目运算符**
基本形式
e1?  e2 : e3 (若e1为真,则表达式数值取e2,否则取e3)
eg:`a>b? a:b`(取a,b中大的数)

**2常用数字函数名**
sqrt(x) ------x的平方根
fabs(x)-------x的平均值
exp(x)-------e的x次方
pow(x,y)------x的y次方

**3.逻辑运算符用在判断条件中**
eg:  判断leap year
`year%400==0 || (year%4==0 && year%100!=0)`

**4.自增的前置与后置**
++a 后置,变量先增值,后被引用
a++ 前置,变量先被引用,后增值

**5.数据类型**
(1)double
scanf("%lf"   );
printf("%f"    );
(2)当浮点数和整数一起运算,c自动将整数转换为浮点数进行运算
eg: 
```
            int i,a;
	    i=10;
            a=i/3;
            a=i/3.0
```
           ( the output is different)     

**6.switch语句**
```
swith(  )
{
	case  常数1: 语句1
	break;
	……
	case  常数n: 语句n
	break;
	default:  语句n-1;
}
```
**7.if语句注意问题**
(1)表达式间用';'而非','
(2)判断条件==而非=
(3)大括号莫忘

**8.string.h中常用的函数**
(1)测试字符串长度函数strlen
(2)字符比较函数strcmp
(3)字符串拷贝函数strcpy
(4)字符串连接函数strcat

**9.枚举**
enum 枚举类型名字{名字0,...,名字n};
大括号里的名字是符号常量,类型为interesting,数值从0到n
eg:
```
enum food{rice,noodles,soup};
```
应用场景:当需要一些可以排列的常量时,赋予这些常量名字.


**10.function**
```
(函数头)  int(返回类型)  sum(函数名)  (int a,int b)(参数表)
    {
        函数体
     }
```
**11.指针与const**
(1)所指是const
表示不能通过这个指针取修改那个变量,并不能使那个变量成为const
eg:
```
const int *p=&i;        
 int  const  *p=&i;   (the same)
*p=26; //error! (*p) is const
i=26;   //ok 
```
(2)指针是const
表示一旦得到了某个变量的地址,不能再指向其他变量
eg:
```
int *const p=&i;
*p=26;  //ok
p++; //error
```

**12.数组变量是特殊的指针**
(1)数组变量本身表示地址
`int a[10];   int *p=a;`(无需用&)
(2)数组单元表示的是变量,需用&
`a==&a[0]`

**13.交换两个变量的值**
```
int swap(int *pa,int *pb)
{
int t=*pa;
*pa=*pb;
*pb=t;
}
```


**14.'n'---读入/写入的个数**
```
int num;
printf ("%d456day%n",123,&num);
printf("%d",num);

the output  is:
123456day
9
```
num读入的是%n之前的写入个数


**15.表示跳过的符号**
eg:读入GPS数据
```
//$GPRMC,00034534.45,A,4368.458659,N,2142353.4576,E,...
scanf("%*[^,],%[^,],%[^,].....",&a,&b...);
```
`%*[^,]`意味着将第一个逗号之前的内容跳过

**16.宏的灵活应用**
甚至可以产生函数
(下例只是简单示范)
```
#define pi 3.14159
#define pi2 2*pi
#define PRT printf("%f",pi);\
            printf("%f",pi2)
```                
Notes: ';'与'\\'的使用              

**17.关于typedef**
作用:声明新的类型的名字
该新名字是某种类型的别名,改善程序可读性
```
typedef struct numberofthedays
{
...
}date;
```
date即为numberofthedays,简化复杂名字



**18.动态内存分布**  (约瑟夫游戏中会用到~)
用stdlib.h中的malloc函数
```
#incude<stdio.h>
#include<stdlib.h>

int main
{
int number,i;
int *a;
scanf("%d",&number);
a=(int*)malloc(number*sizeof(int));
for(i=0;i<number;i++)
scanf("%d",&a[i]);
...
free(a);
return 0;
}
```
**19.随机数**
举例：在0到100随机产生10个整数。
```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
int main(void)
{	
//种种子 
srand(time(NULL));
int i ;	int j ;	
for(i = 0 ; i < 10 ; i ++)	
{		
//产生10个100以内的随机数 		
   j = rand()%100 ;		
   printf("j:%d\n",j);
} 
return 0 ;
}
```
要取[a,b]ss之间的随机整数，使用： 
x=(rand() % (1+b - a)) + a ;
eg:函数产生20-90的随机整数
20-90共有71个数字，所以是rand()%71+20 


s


