Ứng dụng DFS & BFS
---

## Bài 1: Biến đổi số

**Đề bài:** Cho hai số nguyên dương S và T (S, T <= 10000). Bạn có thể thực hiện hai thao tác với số hiện tại X:
1.  Nhân đôi: X = X * 2
2.  Giảm 1: X = X - 1
Tìm số thao tác ít nhất để biến đổi số S thành số T. Giả sử rằng kết quả luôn tồn tại và các giá trị trung gian không vượt quá một giới hạn nào đó (ví dụ: 20000).

**Input:**
* Dòng duy nhất chứa hai số nguyên S và T.

**Output:**
* In ra số thao tác ít nhất.

**Ví dụ:**
*Input:*
```
2 7
```
*Output:*
```
3
```
**Giải thích:** Sử dụng BFS. Coi mỗi số là một trạng thái (đỉnh). Từ trạng thái `u`, có thể chuyển đến trạng thái `u*2` và `u-1` (nếu hợp lệ). Tìm đường đi ngắn nhất từ S đến T trên đồ thị trạng thái này. Dùng mảng `dist` để lưu số bước và `visited` để tránh lặp lại trạng thái.

**Code (BFS):**
```cpp
#include <iostream>
#include <queue>
#include <vector>
#include <map>

using namespace std;

const int MAX_VAL = 20001; // Giới hạn giá trị số có thể đạt tới

int main() {
    int s, t;
    cin >> s >> t;

    if (s >= t) { // Nếu S >= T, chỉ có thể trừ đi 1
        cout << s - t << endl;
        return 0;
    }

    queue<pair<int, int>> q; // <số hiện tại, số bước>
    map<int, int> dist; // Lưu số bước tới mỗi số 

    q.push({s, 0});
    dist[s] = 0;

    while (!q.empty()) {
        int currVal = q.front().first;
        int curDist = q.front().second;
        q.pop();

        if (currVal == t) { // Đã tìm thấy T
            cout << curDist << endl;
            return 0;
        }

        // Thao tác 1: Nhân đôi
        int nxtVal1 = currVal * 2;
        // Kiểm tra nxtVal1 có hợp lệ và chưa thăm hoặc có đường đi tốt hơn
        if (nxtVal1 < MAX_VAL && dist.find(nxtVal1) == dist.end()) {
             dist[nxtVal1] = curDist + 1;
             q.push({nxtVal1, curDist + 1});
        }


        // Thao tác 2: Giảm 1
        int nxtVal2 = currVal - 1;
         // Kiểm tra nxtVal2 có hợp lệ (>0) và chưa thăm hoặc có đường đi tốt hơn
        if (nxtVal2 > 0 && dist.find(nxtVal2) == dist.end()) {
            dist[nxtVal2] = curDist + 1;
            q.push({nxtVal2, curDist + 1});
        }
    }

    return 0; // Trường hợp không tìm thấy (đề bài đảm bảo có)
}
```
---

## Bài 2: Tìm đường đi ngắn nhất trong mê cung

**Đề bài:** Cho một mê cung được biểu diễn bằng lưới ô vuông kích thước N x M. Một số ô là tường ('#'), một số ô là đường đi ('.'). Có một điểm bắt đầu 'S' và điểm kết thúc 'E'. Bạn chỉ có thể di chuyển lên, xuống, trái, phải tới các ô đường đi. Tìm độ dài đường đi ngắn nhất từ 'S' đến 'E'. Nếu không có đường đi, in ra -1.

**Input:**
* Dòng đầu tiên chứa hai số nguyên N và M (1 <= N, M <= 1000).
* N dòng tiếp theo, mỗi dòng chứa M ký tự mô tả mê cung.

**Output:**
* In ra độ dài đường đi ngắn nhất. Nếu không tồn tại, in -1.

**Ví dụ:**
*Input:*
```
5 5
S.#..
.#...
.#.##
..#E.
.....
```
*Output:*
```
9
```

**Giải thích:** Dùng BFS. Coi lưới ô vuông là đồ thị, mỗi ô là một đỉnh, các ô kề nhau (trên, dưới, trái, phải và không phải tường) có cạnh nối. BFS tìm đường đi ngắn nhất trên đồ thị không trọng số. Dùng một mảng `dist[N][M]` để lưu khoảng cách ngắn nhất từ 'S' đến ô (i, j).

**Code (BFS):**
```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <tuple> // Để dùng tuple hoặc pair

using namespace std;

const int MAXN = 1001;
char grid[MAXN][MAXN];
int dist[MAXN][MAXN]; // Lưu khoảng cách ngắn nhất
int n, m;
int start_r, start_c, end_r, end_c;

// Các hướng di chuyển: lên, xuống, trái, phải
int dr[] = {-1, 1, 0, 0};
int dc[] = {0, 0, -1, 1};

// Kiểm tra ô (r, c) có hợp lệ không (trong biên, không phải tường)
bool isValid(int r, int c) {
    return r >= 0 && r < n && c >= 0 && c < m && grid[r][c] != '#';
}

int bfs() {
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < m; ++j) {
            dist[i][j] = -1; // Khởi tạo khoảng cách là -1 (chưa tới)
        }
    }

    queue<pair<int, int>> q;

    q.push({start_r, start_c});
    dist[start_r][start_c] = 0; // Khoảng cách từ S đến chính nó là 0

    while (!q.empty()) {
        int r = q.front().first;
        int c = q.front().second;
        q.pop();

        if (r == end_r && c == end_c) { // Nếu đến được đích
            return dist[r][c];
        }

        // Thử di chuyển 4 hướng
        for (int i = 0; i < 4; ++i) {
            int nr = r + dr[i];
            int nc = c + dc[i];

            // Nếu ô mới hợp lệ và chưa được thăm (dist == -1)
            if (isValid(nr, nc) && dist[nr][nc] == -1) {
                dist[nr][nc] = dist[r][c] + 1; // Cập nhật khoảng cách
                q.push({nr, nc});           // Thêm vào hàng đợi
            }
        }
    }

    return -1; // Không tìm thấy đường đi
}

int main() {
    cin >> n >> m;
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < m; ++j) {
            cin >> grid[i][j];
            if (grid[i][j] == 'S') {
                start_r = i; start_c = j;
            } else if (grid[i][j] == 'E') {
                end_r = i; end_c = j;
            }
        }
    }

    cout << bfs() << endl;

    return 0;
}
```

---

## Bài 3: "Làm khô" vùng nước (Flood Fill)

**Đề bài:** Cho một bản đồ kích thước N x M, một số ô là đất liền ('L'), một số ô là nước ('W'). Chọn một ô nước (r, c), hãy "làm khô" tất cả các ô nước liên thông với ô (r, c) (bao gồm cả ô (r,c)) bằng cách chuyển chúng thành đất liền ('L'). Hai ô được coi là liên thông nếu chúng kề cạnh (chung cạnh). In ra bản đồ sau khi làm khô.

**Input:**
* Dòng đầu tiên chứa hai số nguyên N và M (1 <= N, M <= 100).
* Dòng tiếp theo chứa hai số nguyên r và c (0 <= r < N, 0 <= c < M) là tọa độ ô nước bắt đầu.
* N dòng tiếp theo, mỗi dòng chứa M ký tự mô tả bản đồ. Ô (r, c) được đảm bảo là 'W'.

**Output:**
* In ra N dòng, mỗi dòng M ký tự là bản đồ sau khi đã làm khô vùng nước liên thông.

**Ví dụ:**
*Input:*
```
5 5
1 1
LLLLL
LWWWL
LWWWL
LWWWL
LLLLL
```
*Output:*
```
LLLLL
LLLLL
LLLLL
LLLLL
LLLLL
```

**Giải thích:** Dùng DFS hoặc BFS bắt đầu từ ô (r, c). Mỗi khi thăm một ô nước, chuyển nó thành đất liền và gọi đệ quy/thêm vào hàng đợi các ô nước kề cạnh chưa được thăm.

**Code (DFS):**
```cpp
#include <iostream>
#include <vector>

using namespace std;

const int MAXN = 101;
char grid[MAXN][MAXN];
int n, m;

// Các hướng di chuyển: 4 hướng
int dr[] = {-1, 1, 0, 0};
int dc[] = {0, 0, -1, 1};

// Kiểm tra ô (r, c) có hợp lệ không
bool isValid(int r, int c) {
    return r >= 0 && r < n && c >= 0 && c < m;
}

// Hàm DFS Flood Fill
void dfsFill(int r, int c) {
    if (!isValid(r, c) || grid[r][c] != 'W') { // Nếu ra ngoài biên hoặc không phải nước
        return; // Dừng lại
    }

    grid[r][c] = 'L'; // "Làm khô" ô hiện tại

    // Gọi đệ quy cho 4 ô xung quanh
    for (int i = 0; i < 4; ++i) {
        dfsFill(r + dr[i], c + dc[i]);
    }
}

int main() {
    int start_r, start_c;
    cin >> n >> m >> start_r >> start_c;

    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < m; ++j) {
            cin >> grid[i][j];
        }
    }

    dfsFill(start_r, start_c); // Bắt đầu Flood Fill từ ô (start_r, start_c)

    // In ra bản đồ kết quả
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < m; ++j) {
            cout << grid[i][j];
        }
        cout << endl;
    }

    return 0;
}
```
---