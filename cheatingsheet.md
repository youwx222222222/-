to_string
int num1 = atoi(str1);

输入加速:
```
ios::sync_with_stdio(false);
cin.tie(nullptr);
```

万能库:
```
#include<bits/stdc++.h>
```

线性筛法:
```
void eulerSieve(int n) {// 查找记录2-n的素数{
    for (int i = 2; i <= n; i++){
        if (p[i] == false)  // 如果未被筛过，则为素数
            prime[pNum++] = i;
        for (int j = 0; j < pNum; j++){
            if (i * prime[j] > n) // 当要标记的合数超出范围时跳出
                break;
            p[i * prime[j]] = true; // 将已经记录的素数的倍数进行标记
            if (i % prime[j] == 0)  //关键步骤
                break;
        }
    }
}//gpt
```

数位dp:
```
```

一键全排列:
```
#include <iostream>
#include <algorithm>
using namespace std;
int main ()
{
    int arr[] = {3,2,1};
    cout<<"用prev_permutation对3 2 1的全排列"<<endl;
    do
    {
        cout << arr[0] << ' ' << arr[1] << ' ' << arr[2]<<'\n';
    }
    while ( prev_permutation(arr,arr+3) );      ///获取上一个较大字典序排列，如果3改为2，只对前两个数全排列
 
    int arr1[] = {1,2,3};
    cout<<"用next_permutation对1 2 3的全排列"<<endl;
    do
    {
        cout << arr1[0] << ' ' << arr1[1] << ' ' << arr1[2] <<'\n';
    }
    while ( next_permutation(arr1,arr1+3) );      ///获取下一个较大字典序排列，如果3改为2，只对前两个数全排列
    ///注意数组顺序，必要时要对数组先进行排序
 
    return 0;
}//https://blog.csdn.net/KYJL888/article/details/85069557
```

二分:
```
int BinarySearch(int x) { // 二分查找
    int l=0, r=n-1;
    while(l<=r) {
        int mid=(l+r)/2; // mid 为查找范围的中间值
        if(x==a[mid]) // 查找成功
            return mid;
        else if(x<a[mid]) // 在前半部分查找
            r=mid-1;
        else // 在后半部分查找
            l=mid+1;
    }
    return -1;
}
```

字符串切割
```
//借助strtok实现split
#include <string.h>
#include <stdio.h>
 
int main()
{
    char s[] = "Golden Global   View,disk * desk";
    const char *d = " ,*";
    char *p;
    p = strtok(s,d);
    while(p)
    {
        printf("%s\n",p);
        p=strtok(NULL,d);
    }
 
    return 0;
}
```

```
        getline(cin, st);
        stringstream ss(st);
        string word;
        vector<string> words;
        while (ss >> word) {
            words.push_back(word);
        }
```

并查集（路径压缩+按秩合并）
```
inline void init(int n)
{
    for (int i = 1; i <= n; ++i)
    {
        fa[i] = i;
        rank[i] = 1;
    }
}//初始化

inline void merge(int i, int j)
{
    int x = find(i), y = find(j);    //先找到两个根节点
    if (x == y) return;
    if (rank[x] <= rank[y])
        fa[x] = y;
    else
        fa[y] = x;
    if (rank[x] == rank[y] && x != y)
        rank[y]++;                   //如果深度相同且根节点不同，则新的根节点的深度+1
}//合并

int find(int x)
{
    if(x == fa[x])
        return x;
    else{
        fa[x] = find(fa[x]);  //父节点设为根节点
        return fa[x];         //返回父节点
    }
}//查询
```

sort排序多个元素:
```
struct Edge {
    int u, v, w;
};

// 比较函数:返回 true 时表示 a 应排在 b 前面
bool cmp(const Edge &a, const Edge &b) {
    return a.w > b.w;   // 按权值从大到小排序
}

sort(edges, edges + m, cmp);
stable_sort也可以，这个会保持相对顺序。
```

```
pow(2, 10); // 计算2的10次方
```

1. 字符类型

CHAR_BIT:char 类型的位数(通常为 8)。
CHAR_MIN:char 类型的最小值。
CHAR_MAX:char 类型的最大值。
SCHAR_MIN:有符号 char 类型的最小值。
SCHAR_MAX:有符号 char 类型的最大值。
UCHAR_MAX:无符号 char 类型的最大值。
2. 短整型

SHRT_MIN:short 类型的最小值。
SHRT_MAX:short 类型的最大值。
USHRT_MAX:无符号 short 类型的最大值。
3. 整型

INT_MIN:int 类型的最小值。
INT_MAX:int 类型的最大值。
UINT_MAX:无符号 int 类型的最大值。
4. 长整型

LONG_MIN:long 类型的最小值。
LONG_MAX:long 类型的最大值。
ULONG_MAX:无符号 long 类型的最大值。
5. 长长整型

LLONG_MIN:long long 类型的最小值。
LLONG_MAX:long long 类型的最大值。
ULLONG_MAX:无符号 long long 类型的最大值。

注意**溢出**。

dfs
```
void dfs(int cur, vector<int>& visited, vector<vector<int>>& graph) {
    visited[cur] = 1; // 标记当前节点已经被访问
    // 处理当前节点cur
    for (int i = 0; i < graph[cur].size(); i++) {
        int next = graph[cur][i];
        if (!visited[next]) { // 如果下一个节点未被访问
            dfs(next, visited, graph); // 继续访问下一个节点
        }
    }
}
void dfsTraversal(vector<vector<int>>& graph) {
    int n = graph.size();
    vector<int> visited(n, 0); // 初始化访问数组
    for (int i = 0; i < n; i++) {
        if (!visited[i]) { // 如果当前节点未被访问
            dfs(i, visited, graph); // 从当前节点开始进行深度优先遍历
        }
    }
}
vector<vector<int>> graph(n+1)
```

bfs
```
void bfsTraversal(vector<vector<int>>& graph) {
    int n = graph.size();
    vector<int> visited(n, 0); // 初始化访问数组
    queue<int> q;
    for (int i = 0; i < n; i++) {
        if (!visited[i]) { // 如果当前节点未被访问
            q.push(i); // 将当前节点加入队列
            visited[i] = 1; // 标记当前节点已经被访问
            while (!q.empty()) { // 循环遍历队列中的节点
                int cur = q.front();
                q.pop();
                // 处理当前节点cur
                for (int j = 0; j < graph[cur].size(); j++) {
                    int next = graph[cur][j];
                    if (!visited[next]) { // 如果下一个节点未被访问
                        q.push(next); // 将下一个节点加入队列
                        visited[next] = 1; // 标记下一个节点已经被访问
                    }
                }
            }
        }
    }
}
```

离散化（其实就是排序去重+二分查找）
```
sort(b, b + n);
int m = unique(b, b + n) - b;// m = 不同元素的个数
for (int i = 0; i < n; i++) {
    a[i] = lower_bound(b, b + m, a[i]) - b;找到第一个大于等于 a[i] 的位置。
}

完整:
#include <bits/stdc++.h>
using namespace std;
int main() {
    int n = 6;
    int a[6] = {100, 200, 100, -50, 200, 300};
    int b[6];
    // 拷贝 + 排序
    for (int i = 0; i < n; i++) b[i] = a[i];
    sort(b, b + n);
    // 去重
    int m = unique(b, b + n) - b;
    // 离散化
    for (int i = 0; i < n; i++) {
        a[i] = lower_bound(b, b + m, a[i]) - b;
    }
    // 输出结果
    for (int i = 0; i < n; i++) cout << a[i] << " ";
    cout << endl;
    return 0;
}
```
lower_bound(b, b + m, a[i])在有序区间 [b, b+m) 中，找第一个 ≥ a[i] 的位置（指针/迭代器）。

快读快写
```
inline char nc() {
    static char buf[1 << 20], *p1 = buf, *p2 = buf;
    return p1 == p2 && (p2 = (p1 = buf) + fread(buf, 1, 1<<20, stdin), p1 == p2) ? EOF : *p1++;
}

inline int read() {
    int x = 0, f = 1; char ch = nc();
    while (!isdigit(ch)) { if (ch == '-') f = -1; ch = nc(); }
    while (isdigit(ch)) { x = x * 10 + ch - '0'; ch = nc(); }
    return x * f;
}

inline void write(int x) {
    static char buf[20]; int p = 0;
    if (x == 0) buf[p++] = '0';
    else {
        if (x < 0) { putchar('-'); x = -x; }
        while (x) { buf[p++] = x % 10 + '0'; x /= 10; }
        reverse(buf, buf + p);
    }
    for (int i = 0; i < p; i++) putchar(buf[i]);
}
n = read();
write(ans[i]);
putchar(' ');  // 或 '\n' 看你需要

这时不能用
ios::sync_with_stdio(false);
cin.tie(nullptr);
而且只有OJ可用，本地不行
```

搜索时建图不用向量的方法：
```
const int MAXN = 1000005;
const int MAXM = 2 * MAXN; // 无向图每条边存两次

int n, u, v;
int a[MAXN], b[MAXN], ans[MAXN], kind[MAXN], visited[MAXN];

// 前向星建图
struct Edge { int to, nxt; };
Edge edges[MAXM];
int head[MAXN], tot;

inline void addEdge(int u, int v) {
    edges[++tot] = {v, head[u]};//v 是这条边指向的节点，nxt 指向原来 head[u] 的边
    head[u] = tot;//更新 u 的第一条边为新加入的边
}//添加边

addEdge(u, v);
addEdge(v, u);

for (int i = head[cur]; i; i = edges[i].nxt) {//从当前节点 cur 的第一条边开始，沿链表走到下一条边
    int v = edges[i].to;//邻居节点
    if (!visited[v]) {
        kind[a[v]]++;
        dfs(v, ans[cur]);
        kind[a[v]]--;
    }
}//遍历邻居
```
edges 数组存储了图中的所有边
head[u] 指向节点 u 的第一条边在 edges 数组中的位置
Edge.nxt 指向 下一条从 u 出发的边 的下标
这样就形成了一个 链表结构，但是存储在数组里，避免了动态分配，没有动态分配开销。

最大子段和
```
ll max_kadane = a[1], cur = 0;
for (int i = 1; i <= N; i++) {
    cur = max(a[i], cur + a[i]);
    max_kadane = max(max_kadane, cur);
}
```
最小子段和
```
ll min_kadane = a[1]; cur = 0;
ll total_sum = 0;
for (int i = 1; i <= N; i++) {
    cur = min(a[i], cur + a[i]);
    min_kadane = min(min_kadane, cur);
    total_sum += a[i];
}
```
if(tot == minans) ans = max(ans, maxans);
ans = max(ans, max(maxans,tot-minans));就是「跨过最小子段」得到的环形最大子段和。

赋值
```
memset(arr, 0, sizeof(arr));
vector<int> v(n, 42);
```

![alt text](image.png)

将浮点数 x 保留三位小数输出可以使用 printf("%.3f", x) 或者 std::cout << std::fixed << std::setprecision(3) << x。


g++ U283172.cpp -o U283172


dijkstra（单源多目标无负边）
```
#include <bits/stdc++.h>
using namespace std;
const int N = 505;
const long long INF = 1e18;

long long g[N][N], d[N];
bool vis[N];

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    int n, m, s; cin >> n >> m >> s;
    for (int i = 1; i <= n; i++) 
        for (int j = 1; j <= n; j++) 
            g[i][j] = (i == j ? 0 : INF);

    while (m--) {
        int u, v; long long w;
        cin >> u >> v >> w;
        g[u][v] = min(g[u][v], w); // 若是无向图加上 g[v][u]
    }

    fill(d + 1, d + n + 1, INF);
    d[s] = 0;
    for (int i = 1; i <= n; i++) {
        int u = -1;
        for (int j = 1; j <= n; j++)
            if (!vis[j] && (u == -1 || d[j] < d[u])) u = j;
        vis[u] = true;
        for (int v = 1; v <= n; v++) d[v] = min(d[v], d[u] + g[u][v]);
    }

    for (int i = 1; i <= n; i++) 
        cout << (d[i] == INF ? -1 : d[i]) << " ";
}//(O(n²))
```

```
#include <bits/stdc++.h>
using namespace std;
const int N = 200005;
const long long INF = 1e18;

vector<pair<int,int>> g[N]; // 邻接表 (终点, 权重)
long long d[N];             // 最短路距离
bool vis[N];                // 是否确定最短路
int pre[N];                 // 前驱数组

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int n, m, s; 
    cin >> n >> m >> s;

    // 读入边
    for (int i = 0; i < m; i++) {
        int u, v, w;
        cin >> u >> v >> w;
        g[u].push_back(make_pair(v, w)); 
        // 如果是无向图，加一条反向边：
        // g[v].push_back(make_pair(u, w));
    }

    // 初始化
    for (int i = 1; i <= n; i++) {
        d[i] = INF;
        pre[i] = -1;
    }
    d[s] = 0;

    // 小根堆 (距离, 节点)
    priority_queue<pair<long long,int>, vector<pair<long long,int>>, greater<pair<long long,int>>> pq;
    pq.push(make_pair(0, s));

    // Dijkstra
    while (!pq.empty()) {
        pair<long long,int> top = pq.top(); pq.pop();
        long long du = top.first;
        int u = top.second;
        if (vis[u]) continue;
        vis[u] = true;

        for (int j = 0; j < (int)g[u].size(); j++) {
            int v = g[u][j].first;
            int w = g[u][j].second;
            if (d[v] > du + w) {
                d[v] = du + w;
                pre[v] = u; // 记录前驱
                pq.push(make_pair(d[v], v));
            }
        }
    }

    // 输出结果
    for (int i = 1; i <= n; i++) {
        cout << "节点 " << i << ": ";
        if (d[i] == INF) {
            cout << "不可达\n";
        } else {
            cout << "距离 = " << d[i] << ", 路径 = ";
            vector<int> path;
            for (int x = i; x != -1; x = pre[x]) {
                path.push_back(x);
            }
            reverse(path.begin(), path.end());
            for (int j = 0; j < (int)path.size(); j++) {
                cout << path[j] << (j + 1 == (int)path.size() ? "\n" : " -> ");
            }
        }
    }

```

优先队列
```
//升序队列
priority_queue <int,vector<int>,greater<int> > q;
//降序队列
priority_queue <int,vector<int>,less<int> >q;
```
priority_queue<Type, Container, Functional>
Type 就是数据类型，Container 就是容器类型（Container必须是用数组实现的容器，比如vector,deque等等，但不能用 list。STL里面默认用的是vector），Functional 就是比较的方式，当需要用自定义的数据类型时才需要传入这三个参数，使用基本数据类型时，只需要传入数据类型，默认是大顶堆
```
struct Node {
    int ra;
    int a;
    int other;
    int id;
    bool operator>(const Node& o) const {
        if (ra != o.ra) return ra > o.ra;
        if (a != o.a) return a > o.a;
        if (other != o.other) return other > o.other;
        return id > o.id;
    }
};
priority_queue<Node, vector<Node>, greater<Node>> pq1;
```
Floyd-Warshall（多源最短路算法，用于求图中 任意两点间的最短距离。支持 有向图和负权边，但图中不能有负环。）
```
#include <bits/stdc++.h>
using namespace std;
const int N = 505;
const long long INF = 1e18;

long long d[N][N];

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int n, m;
    cin >> n >> m;

    // 初始化
    for (int i = 1; i <= n; i++)
        for (int j = 1; j <= n; j++)
            d[i][j] = (i == j ? 0 : INF);

    // 读入边
    for (int i = 0; i < m; i++) {
        int u, v;
        long long w;
        cin >> u >> v >> w;
        d[u][v] = min(d[u][v], w);
    }

    // 三重循环更新最短路
    for (int k = 1; k <= n; k++)
        for (int i = 1; i <= n; i++)
            for (int j = 1; j <= n; j++)
                if (d[i][k] != INF && d[k][j] != INF)
                    d[i][j] = min(d[i][j], d[i][k] + d[k][j]);

    // 输出任意两点最短路
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= n; j++) {
            if (d[i][j] == INF) cout << "INF ";
            else cout << d[i][j] << " ";
        }
        cout << "\n";
    }
}
```

Bellman-Ford 是 单源最短路算法，可处理：有向图、负权边，能检测负权环（负环）
```
#include <bits/stdc++.h>
using namespace std;
const long long INF = 1e18;

struct Edge {
    int u, v;
    long long w;
};

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int n, m, s;
    cin >> n >> m >> s;
    vector<Edge> edges(m);
    for (int i = 0; i < m; i++)
        cin >> edges[i].u >> edges[i].v >> edges[i].w;

    vector<long long> d(n+1, INF);
    d[s] = 0;

    // 松弛操作 n-1 次
    for (int i = 1; i <= n-1; i++) {
        for (int j = 0; j < m; j++) {
            Edge e = edges[j];
            if (d[e.u] != INF && d[e.v] > d[e.u] + e.w)
                d[e.v] = d[e.u] + e.w;
        }
    }

    // 检测负环
    bool neg_cycle = false;
    for (int j = 0; j < m; j++) {
        Edge e = edges[j];
        if (d[e.u] != INF && d[e.v] > d[e.u] + e.w) {
            neg_cycle = true;
            break;
        }
    }

    if (neg_cycle) {
        cout << "Graph has a negative weight cycle\n";
    } else {
        for (int i = 1; i <= n; i++)
            cout << (d[i] == INF ? "INF" : to_string(d[i])) << " ";
        cout << "\n";
    }
}
```

SPFA（Bellman-Ford 算法的队列优化版，尤其适合稀疏图和带负权边的单源最短路问题。）
```
#include <bits/stdc++.h>
using namespace std;
const long long INF = 1e18;

struct Edge { int to; long long w; };

int main() {
    int n, m, s;
    cin >> n >> m >> s;
    vector<vector<Edge>> g(n+1);
    for (int i = 0; i < m; i++) {
        int u, v; long long w;
        cin >> u >> v >> w;
        g[u].push_back({v, w});
    }

    vector<long long> d(n+1, INF);
    vector<int> cnt(n+1, 0);
    vector<bool> inq(n+1, false);
    queue<int> q;

    d[s] = 0; q.push(s); inq[s] = true; cnt[s] = 1;
    bool neg_cycle = false;

    while (!q.empty()) {
        int u = q.front(); q.pop(); inq[u] = false;
        for (int i = 0; i < g[u].size(); i++) {
            int v = g[u][i].to; long long w = g[u][i].w;
            if (d[v] > d[u] + w) {
                d[v] = d[u] + w;
                if (!inq[v]) {
                    q.push(v); inq[v] = true;
                    cnt[v]++;
                    if (cnt[v] > n) { neg_cycle = true; break; }
                }
            }
        }
        if (neg_cycle) break;
    }

    if (neg_cycle) cout << "Graph has a negative weight cycle\n";
    else {
        for (int i = 1; i <= n; i++)
            cout << (d[i] == INF ? "INF" : to_string(d[i])) << " ";
        cout << "\n";
    }
}
```

快速幂
```
long long fastPow(long long a, long long b, long long c)
{
	long long ret = 1;
	a %= c;
	while (b)
	{
		if (b & 1)
		{
			ret *= a;
			ret %= c;
		}
		a *= a;
		a %= c;
		b >>= 1;
	}
	return ret;
}//https://blog.csdn.net/m0_70980326/article/details/134624631

```

拓扑排序
```
#include <iostream>
#include <queue>
#include <vector>
using namespace std;

int n;//节点个数
int d[10005];//入读
vector<int> v[10005];//vector存图，方便找到相邻节点
int cur, ans[10005];//数组光标和答案数组

void topusort()//拓扑排序的函数
{
	queue<int> q;//入读为0的队列
	for (int i = 1; i <= n; i++)//将入度为0的节点加入队列
		if (d[i] == 0)
			q.push(i);
	while (!q.empty())
	{
		int f = q.front();//取队头结点
        ans[++cur] = f;//数组光标常规操作
		q.pop();//别忘了把队头出队
		for (int i = 0; i < v[f].size(); i++)//遍历与队头相邻的节点
		{
			int t = v[f][i];//与队头相邻的节点的编号
			d[t]--;//入度-1
			if (d[t] == 0)//入度为0就入队
				q.push(t);
		}
	}
}

int main()
{
    //读入
	scanf("%d", &n);
	for (int i = 1; i <= n; i++)
	{
        //x要在y之前完成，就要连一条从x到y的边
		int x, y;
        cin >> x >> y;
        d[y]++;
        v[x].push_back(y);
	}
	topusort();//调用拓扑排序的函数
    if (cur != n) //正常情况下应该有n个节点
        printf("图中有环，无法进行拓扑排序！！！\n");
    else
    {
        printf("拓扑排序后的序列：");
        for (int i = 1; i <= cur; i++)
            printf("%d ", ans[i]);
        puts("");//换个行
    }
	return 0;
}//https://blog.csdn.net/Happy2019_/article/details/130796610
```

| 数据结构                | 功能 / 用途      | 常用操作                                                                                    | 时间复杂度                        | 遍历方式                                                                    |
| ------------------- | ------------ | --------------------------------------------------------------------------------------- | ---------------------------- | ----------------------------------------------------------------------- |
| **vector**          | 动态数组，随机访问    | `push_back(x)` / `pop_back()`<br>`size()`<br>`v[i]`                                     | O(1) 随机访问，O(1) 平均 push\_back | `for(int x : v)`<br>`for(int i=0;i<v.size();i++) v[i]`                  |
| **deque**           | 双端队列         | `push_back()` / `push_front()`<br>`pop_back()` / `pop_front()`                          | O(1) 两端操作                    | `for(int x : dq)`<br>`for(auto it=dq.begin(); it!=dq.end(); ++it)`      |
| **stack**           | 栈 LIFO       | `push()` / `pop()` / `top()` / `empty()`                                                | O(1)                         | 无直接遍历，需 pop 一次遍历                                                        |
| **queue**           | 队列 FIFO      | `push()` / `pop()` / `front()` / `back()` / `empty()`                                   | O(1)                         | 无直接遍历，需 pop 一次遍历                                                        |
| **priority\_queue** | 优先队列（堆）      | `push()` / `pop()` / `top()`                                                            | 插入 O(log n)，取顶 O(1)          | 无直接遍历，需 pop 一次遍历                                                        |
| **set / multiset**  | 有序集合 / 多重集合  | `insert(x)` / `erase(x)` / `find(x)` / `count(x)` / `lower_bound(x)` / `upper_bound(x)` | O(log n)                     | `for(auto x : s)`<br>`for(auto it=s.begin(); it!=s.end(); ++it)`        |
| **map / multimap**  | 有序键值对 / 多键值对 | `mp[key]=value` / `find(key)` / `erase(key)` / `count(key)`                             | O(log n)                     | `for(auto [k,v] : mp)`<br>`for(auto it=mp.begin(); it!=mp.end(); ++it)` |
| **unordered\_set**  | 无序集合（哈希表）    | `insert(x)` / `erase(x)` / `find(x)` / `count(x)`                                       | 平均 O(1)                      | `for(auto x : us)`<br>`for(auto it=us.begin(); it!=us.end(); ++it)`     |
| **unordered\_map**  | 无序键值对（哈希表）   | `mp[key]=value` / `find(key)` / `erase(key)` / `count(key)`                             | 平均 O(1)                      | `for(auto [k,v] : um)`<br>`for(auto it=um.begin(); it!=um.end(); ++it)` |
| **bitset**          | 固定长度位操作      | `set(i)` / `reset(i)` / `flip(i)` / `test(i)` / `count()`   /` bitset<n> b;`                            | O(1) 单位操作                    | `for(int i=0;i<n;i++) if(bs[i]) ...`                                    |
| **string**          | 字符串处理        | `s.size()` / `s[i]` / `s.substr(l,r)` / `s.find()`                                      | O(n)                         | `for(char ch : s)`<br>`for(int i=0;i<s.size();i++)`                     |
| **array**           | 固定长度数组       | `arr[i]` / `size()` / `fill(arr.begin(), arr.end(), val)`                               | O(1)                         | `for(int x : arr)`<br>`for(int i=0;i<arr.size();i++)`                   |
| **pair**            | 二元组          | `make_pair(a,b)` / `p.first` / `p.second`                                               | O(1)                         | `for(auto [x,y] : v)`                                                   |
| **tuple**           | 多元组          | `make_tuple(a,b,c)` / `get<0>(t)`                                                       | O(1)                         | `for(auto t : v) get<0>(t)`                                             |


### 1. **vector**（动态数组）

```cpp
#include <vector>
using namespace std;

vector<int> v;              // 空的 int 向量
vector<int> v2(10, 5);      // 长度10，所有值初始化为5

v.push_back(3);             // 尾部插入
cout << v[0] << endl;       // 随机访问
for (int x : v) cout << x;  // 遍历
```

---

### 2. **deque**（双端队列）

```cpp
#include <deque>
deque<int> dq;

dq.push_back(1); 
dq.push_front(2); 
cout << dq.front() << " " << dq.back();
```

---

### 3. **stack**（栈 LIFO）

```cpp
#include <stack>
stack<int> st;

st.push(1);
st.push(2);
cout << st.top();  // 2
st.pop();
```

---

### 4. **queue**（队列 FIFO）

```cpp
#include <queue>
queue<int> q;

q.push(1);
q.push(2);
cout << q.front();  // 1
q.pop();
```

---

### 5. **priority\_queue**（优先队列 / 堆）

```cpp
#include <queue>

// 大根堆（默认）
priority_queue<int> pq;
// 小根堆
priority_queue<int, vector<int>, greater<int>> minpq;

pq.push(10); pq.push(5);
cout << pq.top();   // 10
```

---

### 6. **set / multiset**（有序集合）

```cpp
#include <set>
set<int> s;
multiset<int> ms;

s.insert(3); s.insert(1);
if (s.count(1)) cout << "存在";
s.erase(3);

for (int x : s) cout << x;  // 升序遍历
```

---

### 7. **map / multimap**（有序键值对）

```cpp
#include <map>
map<string,int> mp;

mp["apple"] = 5;
mp["banana"] = 3;

if (mp.count("apple")) cout << mp["apple"];
for (auto [k,v] : mp) cout << k << ":" << v << endl;
```

---

### 8. **unordered\_set / unordered\_map**（无序哈希表）

```cpp
#include <unordered_set>
#include <unordered_map>

unordered_set<int> us;
us.insert(10); us.insert(20);

unordered_map<string,int> um;
um["a"] = 1;
um["b"] = 2;
```

---

### 9. **bitset**（固定长度位图）

```cpp
#include <bitset>
bitset<10> bs;   // 长度固定 10 位，默认全 0

bs.set(3);       // 第 3 位置 1
bs.flip(3);      // 第 3 位取反
bs.reset(3);     // 第 3 位置 0

if (bs.test(3)) cout << "bit 3 = 1";
cout << bs.count();  // 统计 1 的个数
```

---

✅ **总结小技巧**：

* 如果要 **动态大小** → `vector`
* 如果要 **两端操作** → `deque`
* 如果要 **LIFO** → `stack`
* 如果要 **FIFO** → `queue`
* 如果要 **取最大/最小** → `priority_queue`
* 如果要 **有序集合/映射** → `set/map`
* 如果要 **哈希集合/映射** → `unordered_set/map`
* 如果要 **大规模 01 标记** → `bitset`

---


好的 👍 我来帮你把 **vector 的核心内容**总结一下：

---

## 🚀 `std::vector` 核心用法总结

### 一、常见构造方式

```cpp
vector<int> v1;              // 空向量
vector<int> v2(5);           // 含 5 个元素，值默认为 0
vector<int> v3(5, 10);       // 含 5 个元素，值都为 10
vector<int> v4(v3);          // 拷贝构造
vector<int> v5(v3.begin(), v3.end()); // 用迭代器范围构造
```

---

### 二、常用成员函数（核心）

* **大小/容量**

  * `size()` 当前元素个数
  * `empty()` 是否为空
  * `resize(n, val)` 调整大小（不足则填充 `val`）
  * `capacity()` 容量（底层数组大小）
  * `reserve(n)` 预留容量

* **增删改**

  * `push_back(x)` 尾部插入
  * `pop_back()` 尾部删除
  * `insert(it, x)` 在迭代器 `it` 位置插入
  * `erase(it)` 删除指定位置元素
  * `clear()` 清空

* **访问元素**

  * `operator[]` 随机访问，不检查越界
  * `at(i)` 随机访问，会检查越界
  * `front()` 第一个元素
  * `back()` 最后一个元素

* **迭代器**

  * `begin()` / `end()`
  * `rbegin()` / `rend()`

---

### 三、简单示例

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    // 构造
    vector<int> v(3, 100); // [100, 100, 100]

    // 增
    v.push_back(200);       // [100,100,100,200]

    // 查
    cout << "size=" << v.size() << " capacity=" << v.capacity() << endl;
    cout << "first=" << v.front() << " last=" << v.back() << endl;

    // 改
    v[1] = 50;              // [100,50,100,200]

    // 插入
    v.insert(v.begin()+2, 300); // [100,50,300,100,200]

    // 删除
    v.pop_back();           // [100,50,300,100]

    // 遍历
    for (int x : v) cout << x << " ";
    cout << endl;
}
```

输出示例：

```
size=4 capacity=6
first=100 last=200
100 50 300 100
```

list
---

## 1. 基本概念

`std::list` 是 **双向链表**，每个节点都保存一个元素，并指向前后节点。

* 插入/删除操作在任意位置 **O(1)**（只要有迭代器）。
* 不支持随机访问（不能用下标 `[]`）。

常用于频繁插入删除、不需要随机访问的场景。

---

## 2. 构造函数

```cpp
std::list<T> lst;                // 空链表
std::list<T> lst(n);             // n 个默认元素
std::list<T> lst(n, val);        // n 个初始值为 val
std::list<T> lst(other_list);    // 拷贝构造
std::list<T> lst(begin, end);    // 迭代器范围构造
```

---

## 3. 常用成员函数

| 功能        | 成员函数示例                                                                        |
| --------- | ----------------------------------------------------------------------------- |
| **大小和状态** | `size()` / `empty()` / `max_size()`                                           |
| **插入**    | `push_back(x)` / `push_front(x)` / `insert(pos, x)` / `emplace(pos, args...)` |
| **删除**    | `pop_back()` / `pop_front()` / `erase(pos)` / `clear()`                       |
| **访问**    | `front()` / `back()`                                                          |
| **排序和合并** | `sort()` / `merge()` / `reverse()` / `unique()`                               |
| **迭代器**   | `begin()` / `end()` / `rbegin()` / `rend()`                                   |

---

## 4. 遍历方法

```cpp
std::list<int> lst = {1,2,3,4,5};

// 1. 范围 for
for (int x : lst) {
    std::cout << x << " ";
}

// 2. 迭代器
for (auto it = lst.begin(); it != lst.end(); ++it) {
    std::cout << *it << " ";
}

// 3. 反向迭代器
for (auto it = lst.rbegin(); it != lst.rend(); ++it) {
    std::cout << *it << " ";
}
```

---

## 5. 插入和删除示例

```cpp
std::list<int> lst = {1,2,3};

// 头部插入
lst.push_front(0); // 0 1 2 3

// 尾部插入
lst.push_back(4);  // 0 1 2 3 4

// 中间插入
auto it = lst.begin();
std::advance(it, 2); // 移动到第3个位置
lst.insert(it, 99);  // 0 1 99 2 3 4

// 删除
lst.pop_front(); // 删除头部
lst.pop_back();  // 删除尾部
lst.erase(it);  // 删除迭代器指向的元素
```

---

### ⚡ 核心特点总结

1. **双向链表**，插入删除 O(1)。
2. **不支持随机访问**（不能用 `[]` 或 `at()`）。
3. 提供丰富的 **迭代器操作** 和 **链表专用函数**（sort、merge、splice）。
4. 适合在中间频繁插入删除的场景。

---



kmp字符串匹配 时间复杂度 O(m+n)。
```
    int kmp(string text, string pattern) {
        int n = text.size(), m = pattern.size();
        if (m == 0) {
            return 0;
        }
        vector<int> next(m);
        for (int i = 1, j = 0; i < m; i++) {
            while (j > 0 && pattern[i] != pattern[j]) {
                j = next[j - 1];
            }
            if (pattern[i] == pattern[j]) {
                j++;
            }
            next[i] = j;
        }
        for (int i = 0, j = 0; i < n; i++) {
            while (j > 0 && text[i] != pattern[j]) {
                j = next[j - 1];
            }
            if (text[i] == pattern[j]) {
                j++;
            }
            if (j == m) {
                return i - m + 1;
            }
        }
        return -1;
    }//https://blog.csdn.net/m0_66459368/article/details/136081819
```



| 类型                   | `scanf` | `printf` | 示例                                     |
| -------------------- | ------- | -------- | -------------------------------------- |
| `int`                | `%d`    | `%d`     | `scanf("%d", &a); printf("%d", a);`    |
| `long`               | `%ld`   | `%ld`    |                                        |
| `long long`          | `%lld`  | `%lld`   |                                        |
| `unsigned int`       | `%u`    | `%u`     |                                        |
| `unsigned long long` | `%llu`  | `%llu`   |                                        |
| `char`               | `%c`    | `%c`     |                                        |
| `char[]` (字符串)       | `%s`    | `%s`     | `scanf("%s", str); printf("%s", str);` |
| `float`              | `%f`    | `%f`     |                                        |
| `double`             | `%lf`   | `%lf`    |                                        |
| `long double`        | `%Lf`   | `%Lf`    |                                        |

| 说明        | 格式   | 示例                         |
| --------- | ---- | -------------------------- |
| 十进制 (int) | `%d` | `123`                      |
| 无符号十进制    | `%u` | `123`                      |
| 八进制       | `%o` | `printf("%o", 10); // 12`  |
| 十六进制 (小写) | `%x` | `printf("%x", 255); // ff` |
| 十六进制 (大写) | `%X` | `printf("%X", 255); // FF` |

```
char c;
scanf("%c", &c);
printf("%c\n", c);

char str[100];
scanf("%s", str);      // 读到空格结束
printf("%s\n", str);
```

| 控制      | 说明            | 示例                                        |
| ------- | ------------- | ----------------------------------------- |
| `%5d`   | 占 5 个宽度，右对齐   | `printf("%5d", 42); // "   42"`           |
| `%-5d`  | 占 5 个宽度，左对齐   | `printf("%-5d", 42); // "42   "`          |
| `%05d`  | 占 5 个宽度，前面补 0 | `printf("%05d", 42); // "00042"`          |
| `%.2f`  | 保留 2 位小数      | `printf("%.2f", 3.14159); // "3.14"`      |
| `%8.2f` | 占 8 宽度，2 位小数  | `printf("%8.2f", 3.14159); // "    3.14"` |

C++ 里读取字符串有几种常见方法，每种都有不同的特点：

---

### **1. `cin >> str`**

* 读入一个**单词**（遇到空格、换行就结束）。
* 常用来读没有空格的字符串。

```cpp
string s;
cin >> s;   // 输入 "hello world" → s = "hello"
```

---

### **2. `getline(cin, str)`**

* 读取一整行（直到 `\n`）。
* 可以包含空格。

```cpp
string s;
getline(cin, s);   // 输入 "hello world" → s = "hello world"
```

⚠️ 注意：如果之前用过 `cin >>`，要清理掉缓冲区里的 `\n`，否则 `getline` 可能读到空串。常见做法：

```cpp
cin.ignore(numeric_limits<streamsize>::max(), '\n');
```

---

### **3. `scanf("%s", char_array)`**

* 读入一个单词（不包含空格）。
* 用于 `char[]`。

```cpp
char s[100];
scanf("%s", s);   // 输入 "hello world" → s = "hello"
```

---

### **4. `gets(char_array)`（⚠️ 已废弃，不推荐）**

* 读入一行（包含空格）。
* 但是 **没有边界检查**，容易缓冲区溢出，所以 C++11 后已废弃。

---

### **5. `fgets(char_array, size, stdin)`**

* 读一行（包括空格，直到 `\n` 或 `EOF`）。
* 更安全，推荐替代 `gets`。

```cpp
char s[100];
fgets(s, 100, stdin);  // 输入 "hello world" → s = "hello world\n"
```

⚠️ 注意：会保留换行符 `\n`，如果不想要，需要手动去掉。

---

✅ **总结：**

* **单词**：`cin >> str` / `scanf("%s", s)`
* **整行**：`getline(cin, str)` / `fgets(s, size, stdin)`
* **别用**：`gets`

---

01背包
```
int knapsack(vector<int>& w, vector<int>& v, int W) {
    int n = w.size();
    vector<vector<int>> dp(n + 1, vector<int>(W + 1, 0)); // 定义状态

    for(int i = 1; i <= n; i++) {
        for(int j = 1; j <= W; j++) {
            if(j < w[i - 1]) { // 当前物品不能装入背包
                dp[i][j] = dp[i - 1][j];
            } else { // 当前物品可以装入背包
                dp[i][j] = max(dp[i - 1][j], dp[i - 1][j - w[i - 1]] + v[i - 1]); // 状态转移方程
            }
        }
    }

    return dp[n][W]; // 返回前n个物品，容量为W时的最大价值
}
```

完全背包
```
int knapsack(vector<int>& w, vector<int>& v, int W) {
    int n = w.size();
    vector<vector<int>> dp(n + 1, vector<int>(W + 1, 0)); // 定义状态

    for(int i = 1; i <= n; i++) {
        for(int j = 1; j <= W; j++) {
            if(j < w[i - 1]) { // 当前物品不能装入背包
                dp[i][j] = dp[i - 1][j];
            } else { // 当前物品可以装入背包
                dp[i][j] = max(dp[i - 1][j], dp[i][j - w[i - 1]] + v[i - 1]); // 状态转移方程
            }
        }
    }

    return dp[n][W]; // 返回前n个物品，容量为W时的最大价值
}
```

多重背包
```
int knapsack(vector<int>& w, vector<int>& v, vector<int>& k, int W) {
    int n = w.size();
    vector<vector<int>> dp(n + 1, vector<int>(W + 1, 0)); // 定义状态

    for(int i = 1; i <= n; i++) {
        for(int j = 1; j <= W; j++) {
            for(int t = 0; t <= k[i - 1] && t*w[i - 1] <= j; t++) { // 列举每一种可能的数量情况
                dp[i][j] = max(dp[i][j], dp[i - 1][j - t*w[i - 1]] + t*v[i - 1]); // 状态转移方程
            }
        }
    }

    return dp[n][W]; // 返回前n个物品，容量为W时的最大价值
}
```

最长上升子序列
```
#include<cstdio>
#include<algorithm>    //这个头文件可以使用max(,),*max_element(,)
using namespace std;    //它们的含义分别是：求两者最大；求数组最大
int n,a[1002],f[1002];
int main()
{
    scanf("%d",&n);
    for(int i=1;i<=n;i++)
    {
        scanf("%d",&a[i]);   //输入
        f[i]=1;              //以第i个数为末尾的上升序列最初长度为1
    }
    for(int i=1;i<=n;i++)         //枚举i的位置
        for(int j=1;j<i;j++)   //在i的前面找j的位置
            if(a[i]>a[j]) //如果满足条件，则第i个数可以放在j后边
                f[i]=max(f[j]+1,f[i]);//取较大的一种再放
    printf("%d",*max_element(f+1,f+n+1));//从 F[1]到F[n] 找最大值
    return 0;
}
```

最长公共子序列
```
 for(int i=1;i<=n;i++){
    for(int j=1;j<=m;j++)
     {
     	dp[i][j]=max(dp[i-1][j],dp[i][j-1]);
     	if(A[i]==B[j])
     	dp[i][j]=max(dp[i][j],dp[i-1][j-1]+1);
     }
 }


二分优化
 int a[105]={1,6,3,2,7,4,3,3,2};
int b[105];
int m=9;
int len=1;
b[1]=a[1];
int find(int x){//二分查找
	int L=1,R=len,mid;
	while(L<=R){
		mid=(l+r)>>1;
		if(x>b[mid])L=mid+1;
		else R=mid-1;
	}
	return L;
}
 
for(int i=2;i<=n;i++){
	if(a[i]>b[len]){//大则添加
		b[++len]=a[i];
	}else{//小则替换
		j=find(a[i]);
		b[j]=a[i];
	}
}
printf("%d\n",len);
```

最长回文子序列 
```
	int longestPalindromeSubseq(string s) {
        int n = s.length();
        vector<vector<int>> dp(n,vector<int>(n,0));
        for(int i=0; i<n; i++)
            dp[i][i] = 1;
        for(int i=n-2; i>=0; i--){
            for(int j=i+1; j<n; j++){
                if(s[i]==s[j])
                    dp[i][j] = dp[i+1][j-1] + 2;
                else
                    dp[i][j] = max(dp[i+1][j],dp[i][j-1]);   
            }
        }
        return dp[0][n-1];
    }

```

石子合并区间dp
```
#include <iostream>
#include <algorithm>

using namespace std;

const int N = 310;
int n;
int s[N];
int f[N][N];

int main(){
    cin >> n;

    for (int i = 1; i <= n; i ++) {
        cin >> s[i];
        s[i] += s[i - 1];
    }

    // 区间 DP 枚举套路：长度+左端点 
    for (int len = 1; len < n; len ++) { // len表示i和j堆下标的差值
        for (int i = 1; i + len <= n; i ++) {
            int j = i + len; // 自动得到右端点
            f[i][j] = 1e8;
            for (int k = i; k <= j - 1; k ++) { // 必须满足k + 1 <= j
                f[i][j] = min(f[i][j], f[i][k] + f[k + 1][j] + s[j] - s[i - 1]);
            }
        }
    }

    cout << f[1][n] << endl;

    return 0;
}
状态表示f(i,j):所有将第i堆石子到第j堆石子合并成一堆石子的合并方式
			属性:Min
状态计算f(i,j) --  [1|2|3|……|k-2|k-1]

一堆石子   i———————————j
可以分成   [i,k],[k+1,j]
f[i,j] = min{f[i,k] + f[k+1,j] + s[j] - s[i-1]}k:[l,j-1]

```



参考了https://hytu99.github.io/code-template/