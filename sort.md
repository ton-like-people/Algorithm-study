# 代码一

这一份代码没有用到sort()函数的第三个参数

```c++
#include<bits/stdc++.h>
using namespace std;
const int N = 5e5 + 5;
int a[N];

int main()
{
    	int n;
    	cin >> n;
    	for(int i=1; i<=n; ++i) cin >> a[i];
    	
        sort(a+1, a+1+n);
    	for(int i=1; i<=n; ++1) cout << a[i] << " \n"[i == n];
    	for(int i=n; i>=1; --i) cout << a[i] << " \n"[i == 1];
    	return 0;
}
```



# 代码二
这一份代码使用了第三个参数，但是这里用的是lambda表达式

```c++
#include<bits/stdc++.h>
using namespace std;
const intt N=5e5 + 5;
int a[N];

int main()
{
    int n; cin >> n;
    for(int i=1; i <= n; ++i) cin >> a[i];
    
    sort(a+1, a+1+n);
    for(int i=1; i<=n; ++i) cout << a[i] << " \n"[i==n];
    
    sort(a+1, a+1+n, [](const int &u, const int &v){
        return u>v;
    });
    
    for(int i=1; i<=n; ++i) cout << a[i] << " \n"[i==n];
        
    return 0;

}
```



# 代码三
这一份代码使用了第三个参数，但是我们只传入函数名。函数定义为全局的。

```c++
#include<bits/stdc++.h>
using namespace std;
const int N = 5e5 + 6;
int a[N];
bool cmp(const int &u, const int &v){
		return u>v;
}

int main()
{
    int n; cin >> n;
    for(int i=1; i<=n; ++i) cin >> a[i];
    
    sort(a+1, a+1+n);
    
    for(int i=1; i<=n; ++i) cout << a[i] << " \n"[i == n];
    
    sort(a+1, a+1+n, cmp);
    for(int i=1; i<=n; ++i) cout << a[i] << " \n"[i == n];
    return 0;
}
```

### 题目描述

小蓝给学生们组织了一场考试，卷面总分为 100 分，每个学生的得分都是一个 0 到 100 的整数。

请计算这次考试的最高分、最低分和平均分。

### 输入描述

输入的第一行包含一个整数 n (1≤n≤104)*n* (1≤*n*≤104)，表示考试人数。

接下来 n*n* 行，每行包含一个 0 至 100 的整数，表示一个学生的得分。

### 输出描述

输出三行。

第一行包含一个整数，表示最高分。

第二行包含一个整数，表示最低分。

第三行包含一个实数，四舍五入保留正好两位小数，表示平均分。

### 输入输出样例

#### 示例

> 输入

```txt
7
80
92
56
74
88
99
10
```

> 输出

```txt
99
10
71.29
```

# 答案一

```c++
#include<bits/stdc++.h>
using namespace std;
using ll = long long;
const int N = 1e4+9;
int a[N];
int main()
{
    ios::sync_with_stdio(0), cin.tie(0), cout.tie(0);
	int n; cin >> n;
    for(int i = 1; i <= n; ++i) cin >> a[i];
    
    cout << *max_element(a+1, a+1+n) << "\n";
    cout << *min_element(a+1, a+1+n) << "\n";
    
    ll sum = 0;
    for(int i = 1; i <= n; ++i) sum += a[i];
    cout << fixed << setprecision(2) << 1.0 * sum / n << "\n";
    return 0;
}
```



# 答案二

```c++
#include<bits/stdc++.h>
using namespace std;
using ll = long long;
const int N = 1e4 + 9;
int a[N];

int main()
{
    int n; cin >> n; 
    for(int i = 1; i <= n; ++i) cin >> a[i];
    
    ll mx = a[1], mi = a[1];
    for(int i = 1; i <= n; ++i)
    {
        mx = max(mx, (ll)a[i]);
        mi = min(mi, 1ll * a[i]);
    }
    cout << mx << "\n" << mi << "\n";
    
    ll sum = 0;
    for(int i = 1; i <= n; ++i) sum += a[i];
    cout << fixed << setprecision(2) << 1.0 * sum / n << "\n";
    return 0;
}
```

第三种方法就是在170行去除ll改为int，对应的173和174行也去除就行，实际上我们的成绩最大值还达不到long long 的门槛

# 二分查找数组元素



### 题目描述

给定一个数组，其采用如下代码定义：

```
int data[200];
for(i = 0 ; i < 200 ; i ++）data[i] = 4 * i + 6;
```

现给定某个数，请你求出它在 data 数组中的位置（下标）。

### 输入描述

输入一个待查找的整数（该整数一定在数组 data 中）。

### 输出描述

输出该整数在数组中的指标。

### 输入输出样例

#### 示例 1

> 输入

```txt
262
```

> 输出

```txt
64
```

#### 示例 2

> 输入

```txt
438
```

> 输出

```txt
108
```

#### 示例 3

> 输入

```txt
774
```

> 输出

```txt
192
```

```c++
// 下面是上面题目对应的代码
#include<bits/stdc++.h>
using namespace std;
int main()
{
  int data[200];
  for(int i = 0 ; i < 200 ; i++)data[i] = 4 * i + 6;
  int target; cin >> target;
 
  cout << lower_bound(data, data + 200, target) - data << "\n";
  return 0;
}
```












