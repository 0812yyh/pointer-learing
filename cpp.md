# 0907

## 1. <>和""区别：寻找路径不同

<>：从系统配置的环境路径下寻找
""：先从自己项目的路径下寻找，if not再从系统配置的环境路径下

## 2. 强制类型转换

### 2.1 隐式类型转换

#### 2.1.1 如果类型相同，直接计算

#### 2.1.2 如果类型不相同，先转换成相同类型，再进行计算

①由简单类型想复杂类型进行转换
②向长度更长的方向进行转换
③向精度更高的方向进行转换
④以赋值运算符左边为准  int a = (double)b + (double)c
⑤类型兼容

### 2.2 float和double

float       单精度浮点数类型 4个字节 %f    6-7位
double  双精度浮点数类型 8个字节 %lf   15-16位
**首选double**

%n.mlf
n：表示宽度（整数位数+小数点+小数位数）
1、限制宽度<实际宽度：限制失效
2、限制宽度>实际宽度：左边补空格，如果n左边有0，左边补0；如果n左边有负号，右边补空格


m：表示小数位数

# 0908

## 1. 大象喝水（const）

~~~
#include <iostream>
#include <cmath>

using namespace std;

int main() {
  int h,r;
  // const 修饰一个变量为常量，常量不可以被修改
  const double pi=3.14;
  cin >> h >> r;
  double v = pi * r * r * h;
  int ans = ceil(20.0 * 1000 / v);
  cout<<ans<<endl;
  return 0;
}
~~~

## 2. 牛吃牧草

（（20✖15）-（20✖10））/（20-10）=10

## 3. 判断、比较、逻辑运算符

### 3.1 判断语句：判断条件为真 进入代码块 否则跳过

真：非0 假：0

if……else

if……else if……else if……else

### 3.2 比较运算符

 >    <    >=    <=    ==    !=

### 3.3 逻辑运算符

&&    ||    ！

## 4 肥胖问题

~~~
#include <iostream>
#include <stdlib.h>

using namespace std;

// 为了代码的完整性，BMI判断条件应该写的全部要写
int main() {
	double m,h,BMI;
	cin>>m>>h;
	BMI=m/(h*h);
	if(BMI<18.5)
		cout<<"Underweight";
	else if(BMI >= 18.5 && BMI  <24)
		cout<<"Normal";
	else
	{
		printf("%.4lf\nOverweight",BMI);
	}
    return 0;
}
~~~

## 5. 地球人口承载力估计

~~~#include <iostream>
#include <iostream>
#include <cmath>

using namespace std;

int main() {
	int x, a, y, b;
	cin>>x>>a>>y>>b;
	int cha = b-a;
	// (y*b-x*a)可以将这部分强转成double，也可以直接✖1.0。
	printf("%.2lf", (y*b-x*a)*1.0/cha);
    return 0;
}
~~~

## 6. 1007打印字符串

### 6.1 char 1个字节 8比特 ascii码

### 6.2 scanf()

scanf("%c%c",&a,&b);
输入方式：①a空格b回车②a回车b回车

# 0910

## 1. 1304

~~~
#include <iostream>
using namespace std;

int main()
{
	double luggage,cost;
	cin >> luggage;
	if(luggage <= 20.00)
	{
		cost = luggage * 1.68;
	}
	else
	{
		cost = luggage * 1.98;
	}
	printf("%.2lf", cost);
	return 0;
}
~~~

### 2. 1320

~~~
#include <iostream>
using namespace std;

int main()
{
	double x,y;
	cin >> x;
	if(x>=0 && x<5)
	{
		y = - x + 2.5;
	}
	else if(x>=5 && x<10)
	{
		y = 2 - 1.5 * (x-3) * (x-3);
	}
	else
	{
		y = x / 2 - 1.5;
	}
	printf("%.3lf", y);
	return 0;
}
~~~

### 3. 1317

~~~
#include <iostream>
using namespace std;

int main()
{
	int x, a = 0, b = 0, c = 0;
	cin >> x;
	if(x % 4 == 1) {
		a = x / 4 - 1;
		b = 1;
	}else if(x % 4 == 2) {
		a = x / 4 - 1;
		c = 1;
	}else if(x % 4 == 3) {
		a = x / 4 - 2;
		b = 1;
		c = 1;
	}else if(x % 4 == 0) {
		a = x / 4;
	}
	cout << c << " " << b << " " << a;
	return 0;
}
~~~

### 4. 1011

~~~
#include <iostream>
#include <cmath>
using namespace std;

int main()
{
	
	int s, v, needH, needM, time, HH, MM;
	cin >> s >> v;
	time = ceil(s * 1.0 / v) + 10;
	needH = ceil(time * 1.0 / 60);
	needM = time % 60;
	if(needH < 8) {
		HH = 8 - needH;
	} else {
		HH = 24 + 8 - needH;
	}
	MM = 60 - needM;
	printf("%02d:%02d", HH, MM);
	return 0;
}


/*	// from teacher
	int s, v;
	cin >> s >> v;
	int time = ceil(s * 1.0 / v) + 10;
	int min = 24 * 60;
	int left = min - time;
	int h = left / 60 + 8, m = left % 60;
	if(h >= 24) h -= 24;
	printf("%02d:%02d", h, m);
	return 0;
*/
~~~

### 5. 1316

#### 5.1 ‘ ’ 字符 " " 字符串

#### 5.2 scanf("%d %d %c", &a,  &b,  &c);

注意这里c和b容易区分不开，如果是%d%c

~~~
#include <iostream>
#include <cmath>
using namespace std;

int main()
{
	int a, b, ans;
	char ope;
	cin >> a >> b >> ope;
	if(ope == '+')
	{
		ans = a + b;
	} else if(ope == '-')
	{
		ans = a - b;
	} else if(ope == '*')
	{
		ans = a * b;
	} else if(ope == '/')
	{
		// ！！！如果没检测符号之前就检测这个，会导致1+0 or 1-0这类运算出现错误
		if(b == 0)
		{
			cout << "Divided by zero!";
			return 0;
		}
		ans = a / b;
	} else 
	{
		cout << "Invalid operator!";
	}	
	cout << ans;
	return 0;
}
~~~

### 6. 1301

~~~
#include <iostream>
using namespace std;

int main()
{
	int a;
	cin >> a;
	if(a % 2 == 0) {
		cout << "yes";
	}
	return 0;
}
~~~

### 7. 1302

~~~ 
#include <iostream>
using namespace std;

int main()
{
	int a;
	cin >> a;
	if(a > 1 && a < 100)
	{
		cout << "yes";
	}
	return 0;
}
~~~

### 8. 循环

#### 8.1 while

判断次数 = 执行次数 + 1

// 1. 循环变量的初始化

while ( 判断条件 ) 	// 2. 循环的判断条件

{

​	// 3. 循环变量的变化

}

#### 8.2 for(;;)	----while和for差不多。同等情况下，推荐使用for，更不容易出错。

// 注意定义到for以外和for以内，涉及到定义域的问题

// 如果判断条件非要写for里面，那么里面一定先得写----if(判断条件){break;}----，即逻辑代码之前。

for(int i = 1; i <= 10; i++) 

{

}

#### 8.3 do{ } while()

执行次数 = 判断次数

# 0913

## 















