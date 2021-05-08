# hdoj笔记

1.为什么会Output limited exceeded

``` c
#include<stdio.h>
#include<string.h>
#include<math.h>
int main()
{
  double x1,x2,y1,y2,d;

while(scanf("%lf %lf %lf %lf",&x1,&y1,&x2,&y2)!=EOF)
  {
  d=(x2-x1)*(x2-x1)+(y2-y1)*(y2-y1);//printf("%.2lf\n",sqrt(pow(x2-x1,2)+pow(y2-y1,2)))
  d=pow(d,0.5);
  printf("%.2lf\n",d);
  }
return 0;
}
```

2008

``` c
#include<stdio.h>//correct
int main()
{
	int n,i;
	float m;
	int sumfu,sum0,sumzhen;
	while(scanf("%d",&n)!=EOF&&n)
	{
		sumfu=sum0=sumzhen=0;
		while(n--)
		{	scanf("%f",&m);
		if(m==0)
			sum0++;
		if(m>0)
			sumzhen++;
		if(m<0)
			sumfu++;
		}
		printf("%d %d %d\n",sumfu,sum0,sumzhen);
				
	}
}


#include<iostream>//wrong
#include<stdio.h>
#include<cmath>
using namespace std;

int main()
{
	int n;
	while (scanf_s("%d",&n)!=EOF&&n)
	{
		int a=0, b=0,c=0;
		double x;
		while (n--)
		{
			scanf_s("%f", &x);
			if (x > 0)
				a++;
			if (x == 0)
				b++;
			if(x < 0)
				c++;
		}
		printf("%d %d %d\n",a,b,c);
	}
	return 0;
}

```

2012

``` c++
#include<iostream>//为什么错了
#include<stdio.h>
#include<cmath>
using namespace std;
int isPrime(int i)
{
    for (int j = 2; j < i/2;j++)
    {
        if (i % j == 0)
            return 1;
    }
    return 0;
}
int main()
{
    int x, y,flag=1;
    while (scanf_s("%d %d", &x,&y) != EOF)     
    {
        if (x == 0 && y == 0)
            continue;
        for (int i = x; i < y+1; i++)
        {
            if (!isPrime(i * i + i + 41))
            {
                printf("sorry\n");
                flag = 0;
                break;
            }
        }
        if(flag)
            printf("ok\n");
    }
    return 0;
}
```

2015偶数求和

```c++

#include<cstdio>
int main(){
	int n,m;
	while(scanf("%d%d",&n,&m)!=EOF){
		int i=1;
		for(i;(i+m)<=n;i+=m)
			printf("%d ",2*i+m-1);
		printf("%d\n",2*i+n-i);
	}
}


#include <stdio.h>
int main()
{
    int n,m,a[100],i,k;
    while(~scanf("%d%d",&n,&m))
    {
        int sum=0,j=0;
        for(i=1;i<=n;i++)
        {
            sum+=2*i;
            if(i%m==0||i==n)
            {
                a[j]=sum;
                j++;
                sum=0;
            }

        }
        k=n%m;
        for(i=0;i<j-1;i++)
        printf("%d ",a[i]/m);

        if(k!=0)
        printf("%d\n",a[j-1]/k);
        else
            printf("%d\n",a[j-1]/m);
    }
```

2017

```c++
#include<stdio.h>
int main()
{
	int n,t,i;
	char a[1000];
	scanf("%d",&n);
	getchar();//think about its function,换行输入必加getchar()，不然\n符读入下个gets
	while(n--)
	{
		i=0;
          	gets(a);
		for(t=0;a[t]!='\0';t++)
		{
			if(a[t]>='0'&&a[t]<='9')  i++;
		}
		printf("%d\n",i);
	}
	return 0;
}
```

2018

```c++
#include"stdio.h"

int fun(int n){
	if(n<=4) return n;
	else return fun(n-1)+fun(n-3);
	//fun(n-3)为新生牛数量=已满4岁牛数量
}

int main(){
	int n;
	while(scanf("%d",&n)&&n){
		printf("%d\n",fun(n));}

	return 0;
}
```

2019

```c++
int main()//runtime error(access_violation)
{
    int n, m,temp;
	int a[110] = {0};
	while (scanf_s("%d %d",&n,&m)!=EOF)
	{
		if (n == 0 && m == 0)
			break;
		for (int i = 0; i < n; i++)
		{
			scanf_s("%d", a + i);
			if (m < a[i])
			{
				temp = a[i];
				a[i] = m;
				a[++i] = temp;
			}
		}
		for (int i = 0; i < n+1; i++)
		{
			printf("%d", a[i]);
			if (i != n + 1)
				printf(" ");
		}
		printf("\n");
	}
    return 0;
}

#include<stdio.h>
int main()
{
	int n,m,a[10000],b;
	while(scanf("%d %d",&n,&m)!=EOF)
	{
		if(n==0&&m==0)
			break; 
		for(int i=0;i<n;i++)
		scanf("%d",&a[i]);
		for(int i=0;i<n;i++)
		{
			if(a[i]<=m&&m<=a[i+1])
				b=i+1;
		}
		for(int i=n-1;i>=b;i--)
			a[i+1]=a[i];
		a[b]=m;
		for(int i=0;i<n;i++)
			printf("%d ",a[i]);
		printf("%d\n",a[n]);
	}
	
}
```

2020

```c++
#include<iostream>//runtime error(access_violation)
#include<cstdio>
#include<cstring>
#include<cmath>
using namespace std;


int main()
{
    int n,x=0;
	int a[110] = {0};
	while (scanf_s("%d",&n)!=EOF&&n)
	{
		for (int i = 0; i < n; i++)
		{
			scanf_s("%d",&x);
			if (x >= 0)
				a[abs(x)] = 1;
			else
				a[abs(x)] = -1;
		}
		for (int i = 109; i >=0; i--)
		{
			if (a[i] == 1&&n!=0)
				printf("%d ", i);
			else if(a[i] ==-1 && n!=0)
				printf("-%d ", i);
			if (a[i] == 1 && n==0)
				printf("%d\n", i);
			else if (a[i] == -1 && n==0)
				printf("-%d\n", i);
			n--;
		}
		printf("\n");
	}
    return 0;
}
```

2021

```c++
int main()//wrong anwser
{
    int n,x=0,count=0;
	int a[100] = {0};
	while (scanf_s("%d",&n)!=EOF&&n)
	{
		getchar();
		for (int i = 0; i < n; i++)
		{
			scanf_s("%d",a+i);	
		}
		for (int i = 0; i < n; i++)
		{
			if (x = a[i] / 100)
			{
				count += x;
				a[i] = a[i] % 100;
			}
			if (x = a[i] / 50)
			{
				count += x;
				a[i] %= 50;
			}
			if(x = a[i] / 10)
			{
				count += x;
				a[i] %= 10;
			}
			if(x = a[i] / 5)
			{
				count += x;
				a[i] %= 5;
			}
			if(x = a[i] / 2)
			{
				count += x;
				a[i] %= 2;
			}
			if(x = a[i])
			{
				count += x;
			}
		}
		printf("%d\n", count);
	}
    return 0;
```

2030

因为汉字处理系统要保证中西文的兼容，当系统中同时存在[ASCII码](https://baike.baidu.com/item/ASCII码)和汉字[国标码](https://baike.baidu.com/item/国标码)时，将会产生二义性。例如：有两个字节的内容为30H和21H，它既可表示汉字“啊”的国标码，又可表示西文“0”和“!”的ASCII码。为此，汉字机内码应对国标码加以适当处理和变换。

国标码的机内码为二[字节](https://baike.baidu.com/item/字节)长的[代码](https://baike.baidu.com/item/代码)，它是在相应[国标](https://baike.baidu.com/item/国标)码的每个字节最高位上加“1”，即

汉字机内码=[汉字国标码](https://baike.baidu.com/item/汉字国标码)+8080H

例如，上述“啊”字的国标码是3021H，其汉字机内码则是B0A1H。

汉字机内码的基础是汉字国标码。

机内码：为了避免ASCII码和[国标码](https://baike.baidu.com/item/国标码)同时使用时产生二义性问题，大部分汉字系统都采用将国标码每个字节高位置1作为汉字机内码。这样既解决了汉字机内码与西文机内码之间的二义性，又使汉字机内码与国标码具有极简单的对应关系。

汉字机内码、国标码和[区位码](https://baike.baidu.com/item/区位码)三者之间的关系为：区位码（十进制）的两个字节分别转换为十六进制后加2020H得到对应的国标码；机内码是汉字交换码（国标码）两个字节的最高位分别加1，即汉字交换码（国标码）的两个字节分别加80H得到对应的机内码；区位码（十进制）的两个字节分别转换为十六进制后加A0H得到对应的机内码。



```c++

#include<iostream>//output number of hanzi 汉字机内码在计算机的表达方式的描述是,使用二个字节，每个字节最高位一位为1.计算机中,补码第一位是符号位,1 表示为负数,所以 汉字机内码的每个字节表示的十进制数都是负数

计算机中,补码第一位是符号位,1 表示为负数,所以 汉字机内码的每个字节表示的十进制数都是负数
#include<string.h>
#include<string>
using namespace std;
int main(){
	int n;
	char str[10000];
	cin>>n;
	getchar();
	while(n--){
		int sum=0;
		cin.getline(str,10000);
		for(int i=0;str[i]!='\0';i++){
			if(str[i]<0){
				sum++;
				i++;
			}
		}
		cout<<sum<<endl;	
	}
	return 0;
}
```

2032

```c++
#include <stdio.h>
#include <stdlib.h>
const int ROW=35;
const int COL=35;
int a[ROW][COL];
int main(){
    for(int i=0;i<ROW;i++){
        a[i][0]=0;
    }
    for(int i=0;i<COL;i++){
        a[0][i]=0;
    }//最外圈初始化为0 多余？
    a[1][1]=1;
    for(int i=2;i<ROW;i++){ 
        for(int j=1;j<=i;j++){
            a[i][j]=a[i-1][j-1]+a[i-1][j];
        }
    }
    int n;
    while(scanf("%d",&n)!=EOF){
        for(int i=1;i<=n;i++){
            for(int j=1;j<=i;j++){
                if(j!=1) printf(" ");
                printf("%d",a[i][j]);
            }
            printf("\n");
        }
        printf("\n");
    }

    return 0;
}
```

2034

```c++
#include <stdio.h>
#include <stdlib.h>//为何错了？
int main()
{
    int n,m,t;
    int a[100] = { 0 }, b[100] = { 0 };
    while(scanf_s("%d %d",&n,&m)!=EOF)
    {
        if (n & m == 0)
            return 0;
        while (n--) {
            scanf_s("%d", &t);
            a[t] = 1;
        }
        while (m--)
        {
            scanf_s("%d", &t);
            b[t] = 1;
        }
        for (int i = 0; i < 100; i++)
        {
            if (a[i] = b[i])
                a[i] = 0;
        }
        for (int i = 0; i < 100; i++)
        {
            if (a[i])
                printf("%d", i);
        }
    }
    return 0;
}
```

2045

```c++
#include<bits/stdc++.h>
using namespace std;
typedef long long LL;
const int MAXN=51;
LL f[MAXN];
int main(){
    f[1]=3;
    f[2]=6;
    f[3]=6;
    for(int i=4;i<MAXN;i++) f[i]=f[i-1]+2*f[i-2];//dp,写出递推方程
    int n;
    while(scanf("%d",&n)!=EOF){
        printf("%lld\n",f[n]);
    }
    return 0;
}
设满足PRG要求的x个方格的涂法为f(x)，求n个方格的涂法.
按照相邻颜色不同的要求染色，染到第n(n>=4)格，第n格的情况有两种
①第n-1个方格的颜色与第1个方格不同,相邻颜色不同,那么从1到n-1满足RPG涂色的要求，涂法为f(n-1),在此种情况下,第n个方格和第n-1相邻,涂法不同,那么第1个,第n-1个,第n个颜色都必须不同,第n格只能是除了第1格,第n-1格外的颜色,故总的可能为f(n-1)*1
②第n-1个方格的颜色和第1个方格相同,相邻颜色不同,那么第n-2格和第1格的颜色就不同,从1到n-2满足RPG要求,涂法为f(n-2),第n格的要求为,与n-1格不同,与第1格不同,n-1格和第1格一同一个颜色，那么第n格剩下2种颜色可选.故总的可能有f(n-2)*2
综上,f(n)=f(n-1)+2*f(n-2)(n>=4)
初值为f(1)=3,f(2)=6,f(3)=6.

```

2046

```c++
#include<iostream>
using namespace std;
int main(void)
{
    long long a[100];
    int i,n;
    a[1]=1;
    a[2]=2;
    for(i=3;i<=50;++i)
    a[i]=a[i-1]+a[i-2];
    while(cin>>n)
    {
        cout<<a[n]<<endl;
    }
}
/* 
(1)先铺好n-1个格，有f(n-1)个方法，再铺第n层的时候只有一种方法，所以总方法是１*f(n-1);
(2)先铺好n-2格，有f(n-2)个方法，再铺后面两层的时候只能两个都横着铺（否则与第一种情况重复）,所以也只有一种;
*/
```

2047

```c++
#include<bits/stdc++.h>
using namespace std;
typedef long long LL;
const int MAXN=41;
LL f[MAXN];
int main(){
    f[1]=3;
    f[2]=8;
    for(int i=3;i<MAXN;i++) f[i]=2*(f[i-1]+f[i-2]);
    int n;
    while(scanf("%d",&n)!=EOF){
        printf("%lld\n",f[n]);
    }
    return 0;
}
设满足定义x长度的字符串有f(x)种
长度为n(n>=3)时
①n为O,假定1-n-2都满足定义,那么n-1位置不能为O,故总数为2*f(n-2)
②n不为O,n-1位置任取，1-n-1都满足定义,总数为2*f(n-1)
递推公式为:f(n)=2*f(n-1)+2*f(n-2);
初值为:f(1)=3,f(2)=8;
```

2048

```c++
计算概率之前，先用递归计算f(n)代表n个人都没抽中的算例个数。
有两种可能性，
1）前n-1个人本来就失败了，第n个人随便和前n-1人谁换一下即可，个数：f(n-1)*(n-1);
2）前n-1个人有一个人成功！第n个人与这个人调换，这个人随便选一个即可，总个数：f(n-2)*(n-1);
总之，f(n) = f(n-2)*(n-1) + f(n-1)*(n-1)；
算概率时，分母是全排列。

# include <iostream>
# include <stdio.h>
# include <vector>
# include <string.h>
# include <algorithm>
# include <math.h>

using namespace std;
long long num_case[30];
long long num_gross_case[30];

long long getnum(int n){
	if (num_case[n]){
		return num_case[n];
	}
	else{
		return (num_case[n] = (n-1)*getnum(n-1) + (n-1)*getnum(n-2));
	}
}
int main(){
	int C; cin >> C;
	num_gross_case[1] = 1;
	for (int i = 2; i <= 21; i++){
		num_gross_case[i] = num_gross_case[i-1] * i;
	}
	num_case[0] = 0;
	num_case[1] = 0;
	num_case[2] = 1;
	
	while (C--){
		int nn;
		cin >> nn;
		printf("%.2lf%%\n", 100.0 * getnum(nn) / num_gross_case[nn]);//%%表示四舍五入
	}
	return 0;
}

```

2049

2050

```c++
(1) n条直线最多分平面问题

题目:n条直线，最多可以把平面分为多少个区域。

解析: 可能你以前就见过这题目，这充其量是一道初中的思考题。
      但一个类型的题目还是从简单的入手，才容易发现规律。
      当有n-1条直线时，平面最多被分成了f(n-1)个区域。
      则第n条直线要是切成的区域数最多，就必须与每条直线相交且不能有同一交点。
      这样就会得到n-1个交点。这些交点将第n条直线分为2条射线和n-2条线断。
      而每条射线和线段将已有的区域一分为二。这样就多出了2+(n-2)个区域。

         故：f(n)=f(n-1)+n

             f(n-1)=f(n-2)+n-1

                 ……
       
             f(2)=f(1)+2

       因为，f(1)=2

       所以，f(n)=n*(n+1)/2 + 1

(2) 折线分平面（hdu2050）
题目：http://acm.hdu.edu.cn/showproblem.php?pid=2050
解析：根据直线分平面可知，由交点决定了射线和线段的条数，进而决定了新增的区域数。
      当n-1条折线时，区域数为f（n-1）。为了使增加的区域最多，
      则折线的两边的线段要和n-1条折线的边，即2*（n-1）条线段相交。
      那么新增的线段数为4*（n-1），射线数为2。
      但要注意的是，折线本身相邻的两线段只能增加一个区域。


       故：f(n)=f(n-1)+4*(n-1)+1

           f(n-1)=f(n-2) + 4*(n-2)+1

               ......
           f(2)=f(1) + 4*1 + 1 

     因为，f(1)=2

     所以，f(n)=2n^2-n+1

 (3) 封闭图形分平面问题

 <a>三角形划分区域（hdu1249）

  题目：http://acm.hdu.edu.cn/showproblem.php?pid=1249
  解析：当n-1个三角形时，区域面积数为 f(n-1) 。
           要区域数最多，那么第n个三角形就必须与前n-1个三角形相交。
           则第n个三角形的一条边就被分割成 2*（n-1）-1条线段与两个半条的线段 ，
           即相当于2*（n-1）条线段。则第 n 个三角形被分割成 3*2*（n-1）条线段。
           则增加了 6*（n-1）个面。

 

            故：f(n)=6*(n-1)+f(n-1)

                f(n-1)=6*(n-2)+f(n-2)

                    ........

                f(2)=6*1+f(1)

          因为，f(1)=2

          所以，f(n)=3*n*(n-1)+2

<b>圆形划分区域

 题目：设有n条封闭曲线画在平面上，而任何两条封闭曲线恰好相交于两点，
            且任何三条封闭曲线不相交于同一点，问这些封闭曲线把平面分割成的区域个数。

 解析：当n-1个圆时，区域数为f(n-1).那么第n个圆就必须与前n-1个圆相交，
            则第n个圆被分为2（n-1）段线段，增加了2（n-1）个区域。

 

             故： f(n)=f(n-1)+2*(n-1)    

                  f(n-1)=f(n-2)+2*(n-2)

                        ......

                  f(2)=f(1)+2*1

            因为，f(1)=2

            所以，f(n)=n^2-n+2

(5)平面分割空间问题（hdu1290）

题目：http://acm.hdu.edu.cn/showproblem.php?pid=1290

解析：由二维的分割问题可知，平面分割与线之间的交点有关，即交点决定射线和线段的条数，
      从而决定新增的区域数。
      试想在三维中则是否与平面的交线有关呢？
      当有n-1个平面时，分割的空间数为f（n-1）。
      要有最多的空间数，则第n个平面需与前n-1个平面相交，且不能有共同的交线。
      即最多有n-1 条交线。而这n-1条交线把第n个平面最多分割成g（n-1）个区域。
      （g（n）为（1）中的直线分平面的个数）此平面将原有的空间一分为二，
      则最多增加g（n-1）个空间。

        

        故：f(n)=f(n-1)+g(n-1)    (  ps: g(n)=n(n+1)/2+1  )

            f(n-1)=f(n-2)+g(n-2)

                 ……

            f(2)=f(1)+g(1)

      因为，f(1)=g(1)=2

      所以，f(n)=2+(1*2+2*3+3*4+……+(n-1)n)/2+（n-1）

                =[ (1^2+2^2+3^2+4^2+……+n^2) - (1+2+3+……+n ) ]/2 + n+ 1

                =(n^3+5n)/6+1

```

2053

```c++
#include<iostream>
using namespace std;
int main()
{
	int n;
	while(cin>>n)
	{
		int flag=0;
		for(int i=1;i<=n;i++)
		{
			if(n%i==0)  //只对第n个位置变换
			{
				if(flag==0)
				flag=1;
				else
				flag=0;
			}
			
		}
		cout<<flag<<endl;
	}
}
```

2054

```c++
#include <iostream>
#include <string>
using namespace std;

bool quwei(string&temp){
	int i = 0, flag = 1;
	while (i<temp.length()){
		if (temp[i] == '.'){
			while (temp[temp.length() - 1] == '0'){
				temp.erase(temp.length() - 1, 1);
			}
			if (temp[temp.length() - 1] == '.'){
				temp.erase(temp.length() - 1, 1);
				flag = 0;
			}
		}
		if (flag == 0){
			break;
		}
		i++;
	}
	
	return true;
}

bool qutou(string&temp){
	while ((temp[0] <= '0'||temp[0] > '9')&&temp[1]!='.'){
		temp.erase(0, 1);
	}
	return true;
}


bool fuhao(string& temp)
{
	if (temp[0] == '-')return false;
	else return true;
}

int main(){
	string a, b;
	while (cin >> a >> b){
		if (fuhao(a) != fuhao(b)){
			cout << "NO" << endl;
			continue;
		}
		qutou(a);
		qutou(b);
		quwei(a);
		quwei(b);
		if (a == b){
			cout << "YES" << endl;
		}
		else{
			cout << "NO" << endl;
		}

	}
}
```

2057

```c++
#include<stdio.h>//c写法
int main()
{
	long long a,b;
	while(scanf("%llx %llx",&a,&b)!=EOF)
	{
		if(a+b<0) 
		{
			printf("-");
			a=-a;b=-b;
		}	
		printf("%llX\n",a+b);
	}
	return 0;
}
dec 置基数为10 相当于"%d"
hex 置基数为16 相当于"%X"
oct 置基数为8 相当于"%o"
setiosflags(ios::uppercase) 16进制数大写输出
//c++提交
#include<iostream>
#include<iomanip>
using namespace std;
int main(){
    long long a,b,z;
    while(cin>>hex>>a>>b){
    if(a+b<0)
       cout<<setiosflags(ios::uppercase)<<hex<<'-'<<-(a+b)<<endl;//16进制大写
    else
       cout<<setiosflags(ios::uppercase)<<hex<<a+b<<endl;}
```

2058

```c++
#include <iostream>
#include <math.h>
using namespace std;
int main()
{
    __int64 m ,n;
    while(cin>>n>>m,n||m)
    {
        __int64 a,k;
        for(k=(int)sqrt(2*m);k>0;k--)//因为1+2+。。。+（2*m)^1/2>m;所一和为m的元素个数应该小于等于（2*m）^1/2;
        {
            a=m/k-(k-1)/2;//假设从a开始一直加到a+k-1,一共k个元素和为m,可以计算出a;
            if((2*a-1+k)*k==2*m) //（2*m)^1/2可能不是整数，判断是有必要的；
                cout<<"["<<a<<","<<k+a-1<<"]"<<endl;
        }
cout<<endl;

    }
return 0;
}
```

2059

```c++
/*
这道题目是DP中多阶段决策的典型例题
我们将起点和终点划分到N个加电站中去
这样一共有N+2点,用DP[i]表示到第i个加电站的最小耗费时间
那么在求DP[i]的时候，DP[0]...DP[i-1]已经求得
让j从0遍历到i-1,每一个j表示最后一次充电到i点
那么状态转移方程为
DP[i] = min(DP[j] + t(j, i)) //t(j, i)表示从j充完电一直到i点(中途没有充过电)
*/
#include<iostream>
#include<string>
#include<cstdio>
#include<cstring>
#include<cstdlib>
#include<cmath>
#include<algorithm>
#include<map>
#include<queue>
#include<stack>
#include<iomanip>
const int MAX=150;
const double INF=0xfffff;//0x代表十六进制
double DP[MAX];//DP[i]表示到第i个加电站的最小耗费时间
int s[MAX];//s[i]表示到第i个加电站距离起点的距离
using namespace std;
double Min(double x,double y)//判断大小
{
    return x>y?y:x;
}
int main()
{
    double L;
    int n,i,j;
    double electricity_l,electricity_t;
    double vt_rabbit,vt_ele,vt_none;
    double len,sum,Time;
    while(cin>>L)//输入跑道长度
    {
        cin>>n>>electricity_l>>electricity_t;//输入加电站的个数、电动车最大行驶距离、电动车的充电时间
        cin>>vt_rabbit>>vt_ele>>vt_none;//输入兔子、电动车、乌龟用脚踏的各个速度
        for(i=1;i<=n;i++)//输入各个加电站距离起点的位置
        cin>>s[i];
        s[n+1]=L;//把第n+1个加电站设为终点，长度为L
        s[0]=0;//把第0个加电站设为起点，长度为0
        DP[0]=0;//起点到起点最小耗费时间为0
        for(i=1;i<=n+1;i++)
        {
            DP[i]=INF;//因为到第i个加电站最小耗费时间未知所以赋值无穷大
            for(j=0;j<i;j++)
            {
                len=s[i]-s[j];//从第j个加电站到第i个加电站的距离
                if(len>electricity_l)//如果该距离大于电动车能行驶的最大距离
                Time=electricity_l/vt_ele+(len-electricity_l)/vt_none;//把电动车行驶的时间加上乌龟用脚踏的时间
                else//如果小于
                Time=len/vt_ele;//直接加上这段距离除于电动车的速度所得的时间
                Time+=DP[j];//之后加上到第j个加电站的最优时间
                if(j>0)//这里判断j>0是因为如果j==0的话,即表明从起点出发，因为起点已经充满电了所以不需要加上电动车的充电时间
                {
                    Time+=electricity_t;//如果j>0加上电动车的充电时间
                }
                DP[i]=Min(DP[i],Time);//每次挑出到第i个加电站的最优时间
            }
        }
        if(DP[n+1]<(L/vt_rabbit))//如果乌龟从起点到终点最小时间小于兔子的跑到终点的时间
        cout<<"What a pity rabbit!"<<endl;
        else
        cout<<"Good job,rabbit!"<<endl;
    }
    return 0;
}
```

2062

https://blog.csdn.net/qq_33266889/article/details/53468509

2063

匈牙利算法[https://baike.baidu.com/item/%E5%8C%88%E7%89%99%E5%88%A9%E7%AE%97%E6%B3%95]

很好的解答和总结http://acm.hdu.edu.cn/discuss/problem/post/reply.php?postid=29526&messageid=1&deep=0

求二分最大匹配数

```c++
#include<stdio.h>
#include<string.h>
int n1, n2, m, ans;
int result[101];//记录V2中的点匹配的点的编号
bool state[101];//记录V2中的每个点是否被搜索过
bool data[101][101];//邻接矩阵true代表有边相连
void init()
{
    int t1, t2;
    memset(data, 0, sizeof(data));
    memset(result, 0, sizeof(result));
    ans = 0;
    scanf("%d%d%d", &n1, &n2, &m);
 
    for(int i = 1; i <= m; i++)
    {
        scanf("%d%d", &t1, &t2);
        data[t1][t2] = true;
    }
 
    return;
}
bool find(inta)
{
    for(int i = 1; i <= n2; i++)
    {
        if(data[a][i] == 1 && !state[i]) //如果节点i与a相邻并且未被查找过
        {
            state[i] = true; //标记i为已查找过
 
            if(result[i] == 0 //如果i未在前一个匹配M中
                || find(result[i])) //i在匹配M中，但是从与i相邻的节点出发可以有增广路
            {
                result[i] = a; //记录查找成功记录
                 
                return true;//返回查找成功
            }
        }
    }
 
    return false;
}
int main()
{
    init();
 
    for(int i = 1; i <= n1; i++)
    {
        memset(state, 0, sizeof(state)); //清空上次搜索时的标记
        if(find(i))
        {
            ans++;    //从节点i尝试扩展
        }
    }
 
    printf("%d\n", ans);
    return 0;
}
```

汉诺塔问题

用f(n, a, b, c)表示要求解的问题，其含义是有a、b、c三根棒和n只盘，且这n个盘叠放在a棒上，依次叠放为大盘在下，小盘在上。借助b棒将n只盘从a棒移到c棒上。每次只移一个盘，在移动时保持大盘在下，小盘在上。

将f(n, a, b, c)转化分解为如下三个子问题：
①f(n - 1, a, c, b)，即将a棒上面的n-1个盘移到b棒，借助c棒。
②move(a, c)，即将在a棒上的一个盘移到c棒。
③f(n - 1, b, a, c)，即将b棒上面的n-1个盘移到c棒，借助a棒。

```c++
void hanoit(int n, char a, char b, char c) {
	if(n == 1){
		move(a, c);
	} else {
		hanoit(n - 1, a, c, b);
		move(a, c);
		hanoit(n - 1, b, a, c);
	}
 
}
```

2064

```c++
假设将n层塔从A经B挪到C需要f[n]步。那么具体的移动过程可以这样看：将上面n-1层从A经B挪到C需要f[n-1]步，再将第n层从A挪到B，需要一步，再将上n-1层从C经B挪到A，需要f[n-1]步，再将第n层从B挪到C，需要一步，再将上n-1层从A经B挪到C，需要f[n-1]步，总计3*f[n-1] + 2步，其中 f[1] = 2;


#include <stdio.h>
 
__int64 dp[36] = {0, 2};
 
int main()
{
    int n;
    for(n = 2; n < 36; ++n) dp[n] = dp[n-1] * 3 + 2;
    while(scanf("%d", &n) == 1) printf("%I64d\n", dp[n]);
    return 0;
}
```

2065 快速幂或打表https://blog.csdn.net/qq_43553133/article/details/83588633

```c++
ll pow(ll a,ll i){
  if (i==0) return 1;
  int temp=pow(a,i>>1);
  temp=temp*temp%MOD;
  if (i&1) temp=(ll)temp*a%MOD;
  return temp%MOD;
}
```



2066 dijkstra

2067

```c++

#include <cstdio>//Catalan数
int main()
{
	__int64 Catalan[40] = {0};
	Catalan[0] = 1;
	Catalan[1] = 1;
	for (int i = 2 ; i <= 35 ; i++)
		for (int j = 0 ; j <= i - 1 ; j++)
			Catalan[i] += Catalan[j] * Catalan[i - 1 - j];
	int num = 1;
	int n;
	while (~scanf ("%d",&n) && n != -1)
		printf ("%d %d %I64d\n",num++,n,Catalan[n] * 2);
	return 0;
}

所以我们事先把第一行所有点的值设为1，进行遍历，到达对角线时i==j,所以map[i][j]=map[i][j-1]，只能接受从下面的点传递过来的走法。i!=j时，map[i][j]=map[i-1][j]+map[i][j-1]，可以接受两边传递过来的走法。
#include <iostream>
#include <cstring>
#include <cstdio>
using namespace std;
int n;
long long map[40][40];
int main()
{
    int i,j,cnt=1;;
    while(cin>>n&&n!=-1)
    {
        memset(map,0,sizeof(map));
        for(i=0;i<=n;++i)
            map[0][i]=1;
        for(i=1;i<=n;++i)
            for(j=0;j<=i;++j)
        {
            if(i==j)
                map[i][j]=map[i][j-1];
            else
                map[i][j]=map[i-1][j]+map[i][j-1];
        }
        printf("%d %d %I64d\n",cnt++,n,2*map[n][n]);
    }
    return 0;
}


```

2068 错排公式 排列组合

元素编号与位置编号各不对应的方法数用D(n)表示

D(n) = (n-1) [D(n-2) + D(n-1)]

```c++
int con(int n,int m)
{
    __int64 a=1,b=1,i;
    //算C(n,m)的部分
    for(i=1; i<=m; i++,n--)//将组合数公式C(n,m)化简后其实就是算((n-m+1)*(n-m+2)*…*n)/(m!)
    {
        b*=i;//算(m!)
        a*=n;//算((n-m+1)*(n-m+2)*…*n)
    }
    return a/b;
}
int main()
{
    int i,n;
    __int64 t,a[13];
    a[0]=1;
    a[1]=0;
    a[2]=1;
    a[3]=2;
    for(i=4; i<=12; i++)//算错排
        a[i]=(i-1)*(a[i-1]+a[i-2]);
    while(scanf("%d",&n)!=EOF&&n!=0)
    {
        t=0;
        for(i=0; i<=n/2; i++)//答对一半以上的总排序和
            t+=a[i]*con(n,i);//分步乘 分类加
        printf("%I64d\n",t);
    }
}
```

2069 dfs 母函数？ 暴力solve

2070 fibbonacci number 用大数 long long

2072 set sstream map

```c++
#include <iostream>
#include <set>
#include <map>
#include <algorithm>
#include <vector>
#include <string>
#include <string.h>
#include <stdio.h>
#include <cctype>//isalpha所在头文件
using namespace std;
int main(){
    string s;
    map<string,int>m;
    while(getline(cin,s)){
        if(s == "#"){
            break;
        }
        m.clear();
        string str = "";
        int len = s.length();
        for(int i = 0;i < len;i++){
            if(isalpha(s[i])){
                str.clear();
                int j;
                for(j = i;isalpha(s[j]) && j < len;j++){
                    str += s[j];
                }
                i = j;
                m[str]++;
            }
        }
        cout<<m.size()<<endl;
    }
    return 0;
}
```



* 从本质上讲，逗号的作用是将一系列运算按顺序执行。最右边的那个表达式的值将作为整个逗号表达式的值，其他表达式的值会被丢弃。例如：

2073

```c++
int main()//二维数组解决对称问题
{
    int n;
    char c1,c2;
    char a[100][100];
    int flag=0;
    while(~scanf("%d %c %c",&n,&c1,&c2)){
            if(flag==1){
                printf("\n");
            }
            flag=1;
            if(n==1){
                printf("%c\n",c1);
                continue;
            }
            for(int i=0;i<=n/2;i++){
            char t;
            if((n/2)%2==0){
                if(i%2==0){
                    t=c1;
                }else{
                    t=c2;
                }
            }else{
                if(i%2==0){
                    t=c2;
                }else{
                    t=c1;
                }
            }
            for(int j=i;j<n-i;j++){
                a[i][j]=t;
                a[n-i-1][j]=t;
            }
            for(int j=i;j<n-i;j++){
                a[j][i]=t;
                a[j][n-i-1]=t;
            }
        }
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                if(i==0&&j==0||i==0&&j==n-1||i==n-1&&j==0||i==n-1&&j==n-1){
                    printf(" ");
                }else{
                    printf("%c",a[i][j]);
                }
            }
            printf("\n");
        }
    }
    return 0;
}
```

2077 而汉诺塔四相对其来说，只是最后一步转移时，可以改为：n-1个圆盘从A移到B、之后令A上最大的盘子经过B移到C，之后令n-1个B上的盘子转移到C上，此时即可完成，反映在代码中，就是递推式的最后一步有所变化。

2079 母函数

通用表达式为

(x^(v[0]*n1[0])+x^(v[0]*(n1[0]+1))+x^(v[0]*(n1[0]+2))+...+x^(v[0]*n2[0]))
(x^(v[1]*n1[1])+x^(v[1]*(n1[1]+1))+x^(v[1]*(n1[1]+2))+...+x^(v[1]*n2[1]))
...
(x^(v[K]*n1[K])+x^(v[K]*(n1[K]+1))+x^(v[K]*(n1[K]+2))+...+x^(v[K]*n2[K]))
K对应具体问题中物品的种类数。
v[i]表示该乘积表达式第i个因子的权重，对应于具体问题的每个物品的价值或者权重。
n1[i]表示该乘积表达式第i个因子的起始系数，对应于具体问题中的每个物品的最少个数，即最少要取多少个。
n2[i]表示该乘积表达式第i个因子的终止系数，对应于具体问题中的每个物品的最多个数，即最多要取多少个。

```c++
//a为最终结果，b保存当前相乘的2个多项式系数。两者都用以储存多项式系数（母函数通用模板）
int a[MAX],b[MAX];
//初始化a
memset(a,0,sizeof(a));
a[0]=1;
for (int i=1;i<=17;i++)//选第几个括号相乘，17指母函数括号项数
{
	memset(b,0,sizeof(b));
	for (int j=n1[i];j<=n2[i]&&j*v[i]<=P;j++)//循环每个因子的每一项（系数权）
		for (int k=0;k+j*v[i]<=P;k++)//循环a的每个项（幂指数）
			b[k+j*v[i]]+=a[k];//把结果加到对应位
	memcpy(a,b,sizeof(b));//b赋值给a
}

#include<bits/stdc++.h>//该题易读版
using namespace std;

int t,n,K;
int val[10],num[10];
int a[10000],b[10000];
int main(){
	scanf("%d",&t);
	while(t--){
		memset(a,0,sizeof(a));
		memset(b,0,sizeof(b));
		scanf("%d%d",&n,&K);
		int sum = 0;
		for(int i=1;i<=K;i++){
			scanf("%d%d",&val[i],&num[i]);
			sum += val[i]*num[i];
		}
		if(sum<n)	printf("0\n");
		else{

			a[0] = 1;
			for(int i=1;i<=K;i++){
				for(int j=0;j<=sum;j++){
					for(int k=0;k<=num[i] && k*val[i]+j<=sum;k++)
						b[k*val[i]+j] += a[j];
				}
				for(int j=0;j<=sum;j++){
					a[j] = b[j];	 b[j] = 0;
				}
			}
			printf("%d\n",a[n]);
		}
	}
	return 0;
}
```

2082 母函数

2083

```c++
#include <iostream>//暴力解决
#include <cmath>
#include <algorithm>
using namespace std;
int main(int argc, char *argv[])
{
	int n,m;
	int a[505],b[505];
	cin>>n;
	while(n--){
		cin>>m;
		for(int i=0;i<m;i++)
		cin>>a[i];
		for(int j=0;j<m;j++)
		{	b[j]=0;
			for(int k=0;k<m;k++)
			{
			
				b[j]+=abs(a[j]-a[k]);
			}
		}
		sort(b,b+m);
		cout<<b[0]<<endl;
	}
	return 0;
}
```

2089

```c++
#include<stdio.h>//学会暴力
int a[1000000]={0};
int main()
{
    int i,n,m,d=0;
    for(i=1;i<1000000;++i)
    {
        if(i%10==4||i/10%10==4||i/100%10==4||i/1000%10==4||i/10000%10==4||i/100000%10==4) d+=0;
        else if(i%100==62||i/10%100==62||i/100%100==62||i/1000%100==62||i/10000%100==62) d+=0;
        else ++d;
        a[i]+=d;
    }
    while(scanf("%d%d",&n,&m)!=EOF&&n!=0||m!=0)
        printf("%d\n",a[m]-a[n-1]);
}
这道题很简单，统计任意区内内不含有4或者62的数字、

最朴素的算法就是枚举n-m之间的所有数字进行在线判断。
判断可以利用itoa把数字转化成字符串，利用字符串函数strstr快速判断之后输出答案，再继续搜索下一个n-m
    
但是我们考虑一个问题。由于本题目没有提问组数的范围，考虑一个极端情况，询问100000次1-1000000，很显然，肯定是会超时的。

因此我们考虑来离线回答这个问题，也就是预处理。我们知道，如果在线回答100000次1-1000000就意味着要做100000次1-1000000的循环，那么我们提前在回答前就算好并记录好答案，然后询问的话只要直接输出就行了。

那么怎么预先算好呢？很简单，读入前先做一次1-1000000的循环，建立一个数组a，记录前i个数有几个是不符合的。也就是利用了前缀和。这样的话后面读入n与m后，我们只需要a[m]-a[n]能在o（1）的复杂度内就知道n-m内不符合的数字，同时计算出答案。这样就绝对不会超时了。

 1 2 3 4 5 6 7 8 9我想知道任意区间[n,m]的值，我们读入的时候不要存一个数，而是把前I项存起来。
存完是这样的1 3 6 10 15 21 28 36 45，如果我想知道[2,10]内数字的和，就直接a[10]-a[2-1]即可，不需要循环了。

下面附上AC代码参考：
int a[1000010],i,j,n,m;
char num[1000010];

int main(){
  memset(a,0,sizeof(0));
  for(i=1;i<=1000001;i++){
   itoa(i,num,10);
   if(strstr(num,"4")!=NULL){a[i]+=a[i-1]+1; continue;}
   if(strstr(num,"62")!=NULL){a[i]+=a[i-1]+1; continue;}
   a[i]=a[i-1];
  }
  scanf("%d%d",&n,&m); int sum,ans;
  while(n!=0&&m!=0){
   sum=m-n+1; ans=sum-(a[m]-a[n-1]);
   printf("%dn",ans);
   scanf("%d%d",&n,&m);
  }
  return 0;
}
```

区别取值四舍五入和输出四舍五入

输出的话printf("%n.mf",x);例如两位的printf("%.2f",x);

```c++
double y = ((int)(x*100 + 0.5))/100.0; // 取值用法
```

2094 dfs实现拓扑排序，或者题意推理引申

2095 异或运算或者找最大 为什么？有点不懂题意