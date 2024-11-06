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










