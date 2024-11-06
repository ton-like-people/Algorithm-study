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

