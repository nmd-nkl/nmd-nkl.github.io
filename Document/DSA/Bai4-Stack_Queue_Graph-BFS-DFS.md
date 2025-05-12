Stack, Queue & Đồ thị (BFS, DFS)
# Mục lục

- [1. Stack & Queue](#1-stack--queue)
  - [1.1. Stack (Ngăn xếp)](#11-stack-ngăn-xếp)
  - [1.2. Queue (Hàng đợi)](#12-queue-hàng-đợi)
- [2. Tổng quan lí thuyết đồ thị](#2-tổng-quan-lí-thuyết-đồ-thị)
  - [2.1. Đồ thị là gì?](#21-đồ-thị-là-gì)
  - [2.2. Các dạng đồ thị](#22-các-dạng-đồ-thị)
    - [2.2.1. Đơn đồ thị](#221-đơn-đồ-thị)
    - [2.2.2. Đa đồ thị](#222-đa-đồ-thị)
    - [2.2.3. Đồ thị vô hướng](#223-đồ-thị-vô-hướng)
    - [2.2.4. Đồ thị có hướng](#224-đồ-thị-có-hướng)
  - [2.3. Các cách biểu diễn đồ thị](#23-các-cách-biểu-diễn-đồ-thị)
    - [2.3.1. Ma trận kề (Adjacency matrix)](#231-ma-trận-kề-adjacency-matrix)
    - [2.3.2. Danh sách kề (Adjacency list)](#232-danh-sách-kề-adjacency-list-hay-dùng-nhất)
    - [2.3.3. Danh sách cạnh (Edge list)](#233-danh-sách-cạnh-edge-list)
- [3. BFS (Breadth-First Search - Tìm kiếm theo chiều rộng)](#3-bfs-breadth-first-search---tìm-kiếm-theo-chiều-rộng)
- [4. DFS (Depth-First Search - Tìm kiếm theo chiều sâu)](#4-dfs-depth-first-search---tìm-kiếm-theo-chiều-sâu)
- [5. Xác định thành phần liên thông (Connected Components)](#5-xác-định-thành-phần-liên-thông-connected-components)
----
## 1. Stack & Queue

### 1.1. Stack (Ngăn xếp)

* **Lý thuyết:** Hoạt động theo nguyên tắc **LIFO (Last-In, First-Out)** 
* **Các thao tác chính (Độ phức tạp thời gian O(1) cho mỗi thao tác):**
    * `push(val)`: Thêm phần tử vào đỉnh stack.
    * `pop()`: Xóa phần tử ở đỉnh stack.
    * `top()`: Trả về phần tử ở đỉnh stack (không xóa).
    * `empty()`: Kiểm tra stack có rỗng không.
    * `size()`: Trả về số lượng phần tử.
* **Độ phức tạp không gian:** O(N) với N là số phần tử trong stack.

### 1.2. Queue (Hàng đợi)

* **Lý thuyết:** Hoạt động theo nguyên tắc **FIFO (First-In, First-Out)** 
* **Các thao tác chính (Độ phức tạp thời gian O(1) cho mỗi thao tác):**
    * `push(val)`: Thêm phần tử vào cuối queue.
    * `pop()`: Xóa phần tử ở đầu queue.
    * `front()`: Trả về phần tử ở đầu queue (không xóa).
    * `back()`: Trả về phần tử ở cuối queue (không xóa).
    * `empty()`: Kiểm tra queue có rỗng không.
    * `size()`: Trả về số lượng phần tử.
* **Độ phức tạp không gian:** O(N) với N là số phần tử trong queue.

## 2. Tổng quan lí thuyết đồ thị

### 2.1. Đồ thị là gì?

**Web hay để học đồ thị - biểu diễn đồ thị:** [https://csacademy.com/app/graph_editor/](https://csacademy.com/app/graph_editor/)

<img src="https://i.imgur.com/ZikFiky.png" alt="Graph Sample" width="800" height="400"/>

_Đây là một đồ thị vô hướng, Đồ thị có 6 đỉnh được đánh số từ 0 đến 5._

Một đồ thị gồm: các **đỉnh (Vertices)** hoặc được gọi là **nút (nodes)**, và những đường thẳng/cong nối các đỉnh - gọi là các **cạnh (edges)**.

* Kí hiệu: **G = (V, E)** với V là tập đỉnh (Vertices), E là tập cạnh (Edges).

### 2.2. Các dạng đồ thị

#### 2.2.1. Đơn đồ thị

<img src="https://i.imgur.com/njd1AQ8.png" alt="Đơn đồ thị" width="300" height="300"/>

_Đơn đồ thị: Không có cạnh song song (nhiều hơn 1 cạnh nối cùng 1 cặp đỉnh) và không có khuyên (cạnh nối 1 đỉnh với chính nó)._

#### 2.2.2. Đa đồ thị

![Đa đồ thị](https://i.imgur.com/d4YC54E.png)

_Đa đồ thị: Có thể có cạnh song song hoặc khuyên._

#### 2.2.3. Đồ thị vô hướng

<img src="https://i.imgur.com/QK6dHRt.png" alt="Đồ thị vô hướng" width="300" height="300"/>

_Các cạnh không có hướng (ví dụ: cạnh nối A và B là như nhau dù đi từ A->B hay B->A)._

#### 2.2.4. Đồ thị có hướng

<img src="https://i.imgur.com/mN01UPA.png" alt="Đồ thị có hướng" width="300" height="300"/>

_Các cạnh có hướng xác định (ví dụ: cạnh đi từ A đến B khác với cạnh đi từ B đến A)._

### 2.3. Các cách biểu diễn đồ thị

Gọi |V| là số đỉnh và |E| là số cạnh của đồ thị.

#### 2.3.1. Ma trận kề (Adjacency matrix)

<img src="https://i.imgur.com/qtmpEgd.png" alt="Ví dụ" width="400" height="300"/>

**Ma trận kề của đồ thị:**

Để biểu diễn đồ thị **G=(V, E)** trong ma trận kề, ta xây dựng ma trận vuông **A** kích thước |V|x|V| với:

* **A[u][v] = 1** nếu có cạnh nối đỉnh u và đỉnh v.
* **A[u][v] = 0** nếu không có cạnh nối trực tiếp giữa u và v.

Dưới đây là ma trận kề của đồ thị ví dụ (vô hướng, không trọng số):

|       | 0 | 1 | 2 | 3 |
| :---- | :-: | :-: | :-: | :-: |
| **0** | 0 | 1 | 0 | 0 |
| **1** | 1 | 0 | 1 | 1 |
| **2** | 0 | 1 | 0 | 1 |
| **3** | 0 | 1 | 1 | 0 |

**Lưu ý:**

* Nếu đồ thị **có trọng số**, thay `1` bằng trọng số cạnh w(u, v). Nếu không có cạnh, có thể dùng giá trị đặc biệt (ví dụ: vô cùng hoặc 0 tùy ngữ cảnh).
* Nếu đồ thị **vô hướng**, ma trận kề là ma trận đối xứng (A[u][v] = A[v][u]).
* Nếu đồ thị **có hướng**, A[u][v] = 1 chỉ biểu thị có cạnh từ u *đến* v.

```cpp
#include <vector>
#include <iostream>

using namespace std;

const int MAXN = 1000; // Giới hạn số đỉnh tối đa
int adj[MAXN][MAXN];
int n, m; // n: số đỉnh, m: số cạnh

int main() {
    cin >> n >> m;
    // Khởi tạo ma trận kề với giá trị 0 (hoặc vô cùng nếu có trọng số âm)
    for(int i = 0; i < n; ++i) {
        for(int j = 0; j < n; ++j) {
            adj[i][j] = 0; // Giả sử không có cạnh nối
        }
    }

    for(int i = 0; i < m; ++i){
        int u, v; // Đọc cạnh nối giữa đỉnh u và v
        // Giả sử đỉnh được đánh số từ 0 đến n-1
        cin >> u >> v;
        // int w; cin >> u >> v >> w; // Nếu có trọng số
        adj[u][v] = 1; // Có cạnh từ u đến v
        // adj[u][v] = w; // Nếu có trọng số
        adj[v][u] = 1; // Nếu đồ thị vô hướng
        // adj[v][u] = w; // Nếu đồ thị vô hướng và có trọng số
    }
    return 0;
}
```

* **Độ phức tạp không gian:** O(|V|^2).
* **Kiểm tra cạnh (u, v):** O(1).
* **Liệt kê các đỉnh kề của u:** O(|V|).
* **Phù hợp:** Đồ thị dày đặc (số cạnh |E| xấp xỉ |V|^2).

#### 2.3.2. Danh sách kề (Adjacency list) **`[Hay dùng nhất]`**

Lưu trữ một mảng gồm |V| danh sách. Mỗi danh sách `adj[u]` chứa các đỉnh kề với đỉnh `u`.

**Danh sách kề của đồ thị ví dụ:**

| Node     | Adj Nodes   |
| :------- | :---------- |
| adj[0]   | {1}         |
| adj[1]   | {0, 2, 3}   |
| adj[2]   | {1, 3}      |
| adj[3]   | {1, 2}      |

```cpp
#include <vector>
#include <iostream>
#include <utility> // Để dùng pair

using namespace std;

const int N = 1e5 + 10; // Giới hạn số đỉnh
int n, m;
vector<int> adj_no_weight[N];         // Danh sách kề không trọng số
vector<pair<int, int>> adj_weight[N]; // Danh sách kề có trọng số {đỉnh kề, trọng số}

int main() {
    cin >> n >> m;
    // Ví dụ cho đồ thị không trọng số, vô hướng
    for(int i = 0; i < m; ++i){
        int u, v; cin >> u >> v; // Đỉnh từ 0 đến n-1
        adj_no_weight[u].push_back(v);
        adj_no_weight[v].push_back(u); // Bỏ dòng này nếu đồ thị có hướng
    }

    // Ví dụ cho đồ thị có trọng số, có hướng
    // for(int i = 0; i < m; ++i){
    //     int u, v, w; cin >> u >> v >> w; // Cạnh từ u đến v, trọng số w
    //     adj_weight[u].push_back({v, w});
    //     // Nếu vô hướng thì thêm: adj_weight[v].push_back({u, w});
    // }

    // In danh sách kề của đỉnh 1 (ví dụ không trọng số)
    cout << "Cac dinh ke voi dinh 1: ";
    for(int neighbor : adj_no_weight[1]) {
        cout << neighbor << " ";
    }
    cout << endl;

    return 0;
}
```

* **Độ phức tạp không gian:** O(|V| + |E|).
* **Kiểm tra cạnh (u, v):** O(deg(u)), với deg(u) là bậc của đỉnh u (số cạnh nối với u).
* **Liệt kê các đỉnh kề của u:** O(deg(u)).
* **Phù hợp:** Đồ thị thưa (số cạnh |E| nhỏ hơn nhiều so với |V|^2), đây là trường hợp phổ biến.

#### 2.3.3. Danh sách cạnh (Edge list)

Lưu trữ tất cả các cạnh của đồ thị trong một danh sách.

```cpp
#include <vector>
#include <iostream>
#include <algorithm> // Để sort

using namespace std;

struct Edge {
    int u, v, w; // u: đỉnh bắt đầu, v: đỉnh kết thúc, w: trọng số
    // Constructor để dễ tạo Edge
    Edge(int start_node, int end_node, int weight) : u(start_node), v(end_node), w(weight) {}

    // Nạp chồng toán tử so sánh để có thể sort theo trọng số (hữu ích cho một số thuật toán như Kruskal)
    bool operator<(const Edge &other) const {
        return w < other.w;
    }
};

int main() {
    int n, m; cin >> n >> m; // n: số đỉnh, m: số cạnh
    vector<Edge> edges;
    cout << "Nhap " << m << " canh (u v w):" << endl;
    for(int i = 0; i < m; ++i) {
        int u, v, w; cin >> u >> v >> w; // Đọc cạnh từ u đến v với trọng số w
        edges.push_back(Edge(u, v, w));
        // Nếu đồ thị vô hướng và cần biểu diễn 2 chiều, có thể thêm:
        // edges.push_back(Edge(v, u, w));
    }

    // Sắp xếp các cạnh theo trọng số tăng dần (ví dụ)
    sort(edges.begin(), edges.end());

    cout << "Danh sach canh da sap xep:" << endl;
    for(const auto& edge : edges) {
        cout << edge.u << " -> " << edge.v << " (w=" << edge.w << ")" << endl;
    }

    return 0;
}
```

* **Độ phức tạp không gian:** O(|E|).
* **Kiểm tra cạnh (u, v):** O(|E|) nếu chưa sắp xếp, hoặc O(log|E|) nếu đã sắp xếp và dùng tìm kiếm nhị phân (ít hiệu quả).
* **Liệt kê các đỉnh kề của u:** O(|E|).
* **Phù hợp:** Khi cần duyệt qua tất cả các cạnh một cách dễ dàng, ví dụ trong thuật toán Kruskal hoặc Bellman-Ford.

## 3. BFS (Breadth-First Search - Tìm kiếm theo chiều rộng)

* **Ý tưởng:** Duyệt đồ thị theo từng lớp (level). Bắt đầu từ đỉnh nguồn `s`, thăm tất cả các đỉnh kề với `s` (lớp 1), sau đó thăm tất cả các đỉnh kề với các đỉnh ở lớp 1 (mà chưa được thăm - lớp 2), và cứ thế tiếp tục.
* **Cấu trúc dữ liệu sử dụng:** Hàng đợi (Queue) để lưu các đỉnh cần thăm theo thứ tự FIFO.
* **Ứng dụng:** Tìm đường đi ngắn nhất trên đồ thị không trọng số, kiểm tra tính liên thông, ...
* **Độ phức tạp:** O(|V| + |E|) khi dùng danh sách kề; O(|V|^2) khi dùng ma trận kề.

**Các thành phần phụ trợ:**

* **Mảng** `visited[]`: Đánh dấu các đỉnh đã thăm (boolean).
* **Mảng** `parent[]` (hoặc `par[]`): Lưu đỉnh cha của một đỉnh trong cây BFS, dùng để truy vết đường đi. `parent[s] = -1` (hoặc giá trị đặc biệt khác).
* **Hàng đợi** `q`: Lưu các đỉnh sẽ được thăm.

```cpp
#include <vector>
#include <queue>
#include <iostream>
#include <algorithm> // Cho reverse

using namespace std;

const int N = 1e5 + 10; // Max số đỉnh
vector<int> adj[N];     // Danh sách kề (không trọng số)
vector<bool> visited;
vector<int> parent;
int n; // Số đỉnh

void bfs(int s) { // s là đỉnh bắt đầu
    // Khởi tạo
    visited.assign(n + 1, false); // Giả sử đỉnh từ 1->n
    parent.assign(n + 1, -1);

    queue<int> q;

    q.push(s);
    visited[s] = true;
    parent[s] = -1; // Đỉnh nguồn không có cha

    while (!q.empty()) {
        int u = q.front(); // Lấy đỉnh đầu hàng đợi
        q.pop();

        // cout << "Dang tham dinh: " << u << endl; // Debug

        // Duyệt các đỉnh kề v của u
        for (int v : adj[u]) {
            if (!visited[v]) { // Nếu đỉnh v chưa được thăm
                visited[v] = true;
                parent[v] = u; // Ghi nhận u là cha của v
                q.push(v);     // Thêm v vào hàng đợi để thăm sau
                // cout << "  Phat hien dinh moi: " << v << ", cha la: " << u << endl; // Debug
            }
        }
    }
}

// Hàm truy vết và in đường đi từ s đến u
void printPath(int s, int u) {
    if (!visited[u]) { // Kiểm tra xem có đến được u từ s không
        cout << "Khong co duong di tu " << s << " den " << u << "!" << endl;
    } else {
        vector<int> path;
        // Lần ngược từ u về s thông qua mảng parent
        for (int v = u; v != -1; v = parent[v]) {
            path.push_back(v);
        }
        // Vì lần ngược nên cần đảo lại để có thứ tự từ s -> u
        reverse(path.begin(), path.end());

        cout << "Duong di tu " << s << " den " << u << ": ";
        for (size_t i = 0; i < path.size(); ++i) {
            cout << path[i] << (i == path.size() - 1 ? "" : " -> ");
        }
        cout << endl;
    }
}

// int main() {
//     // Giả sử đã nhập n, m và xây dựng adj[]
//     int start_node = 1; // Ví dụ bắt đầu từ đỉnh 1
//     int end_node = 5;   // Ví dụ muốn tìm đường đến đỉnh 5
//     bfs(start_node);
//     printPath(start_node, end_node);
//     return 0;
// }
```

## 4. DFS (Depth-First Search - Tìm kiếm theo chiều sâu)

* **Ý tưởng:** Ưu tiên đi "sâu" nhất có thể theo một nhánh trước khi quay lại và thử nhánh khác. Bắt đầu từ đỉnh nguồn `s`, chọn một đỉnh kề `v` chưa thăm, đệ quy gọi DFS(v). Khi không còn đỉnh kề nào chưa thăm từ đỉnh hiện tại, quay lui (backtrack).
* **Cấu trúc dữ liệu sử dụng:** Ngăn xếp (Stack), có thể là stack hệ thống (thông qua đệ quy) hoặc stack tự tạo.
* **Ứng dụng:** Kiểm tra chu trình, tìm thành phần liên thông, tô màu đồ thị, sắp xếp topo (cho đồ thị có hướng, không chu trình), ...
* **Độ phức tạp:** O(|V| + |E|) khi dùng danh sách kề; O(|V|^2) khi dùng ma trận kề.

**Các thành phần phụ trợ:**

* **Mảng** `visited[]`: Đánh dấu các đỉnh đã thăm.

```cpp
#include <vector>
#include <iostream>

using namespace std;

const int N = 1e5 + 10;
vector<int> adj[N];
vector<bool> visited;
int n;

void dfs(int u) {
    visited[u] = true;
    for (int v : adj[u]) {
        if (!visited[v]) {
            dfs(v);
        }
    }
}

int main() {
    // Giả sử đã nhập n, m và xây dựng adj[]
    visited.assign(n + 1, false);
    int start_node = 1;
    dfs(start_node);
    return 0;
}
```

## 5. Xác định thành phần liên thông (Connected Components)

* **Khái niệm:** Một tập con các đỉnh của đồ thị vô hướng sao cho có đường đi giữa hai đỉnh bất kỳ trong tập con đó, và không có đường đi nào nối một đỉnh trong tập con với một đỉnh bên ngoài tập con.

```cpp
int cnt = 0;
for (int i = 1; i <= n; ++i) {
    if (!visit[i]) {
        cnt++;
        bfs(i); //bfs(i)
    }
}
cout << cnt; //Số thành phần liên thông
```