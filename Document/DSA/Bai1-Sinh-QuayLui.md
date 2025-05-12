# Buổi 1:
### Mục lục
1. [Thuật toán sinh](#1-thuật-toán-sinh)

    1.1 [Giới thiệu](#11-giới-thiệu)

    1.2 [Sinh xâu nhị phân](#12-sinh-xâu-nhị-phân)

    1.3 [Tổ hợp chập K của N](#13-sinh-tổ-hợp-chập-k-của-n-phần-tử)

    1.4 [Sinh Hoán vị](#14-sinh-hoán-vị)

2. [Đệ quy và Quay lui](#2-đệ-quy-và-quay-lui)

    2.1 [Đệ Quy](#21-đệ-quy)

    2.2 [Quay lui](#22-quay-lui)
3. [Bài tập luyện tập](#3-bài-tập-luyện-tập)

---
# 1. Thuật toán sinh
## **1.1 Giới thiệu**
- `Thuật toán sinh` là một phương pháp vét cạn được dùng với các bài toán liệt kê hoặc đếm cấu hình, thỏa các yêu cầu sau:
    * Có thể xác định được cấu hình đầu tiên và cấu hình cuối cùng.
    * Tìm được thuật toán để từ cấu hình hiện tại sinh ra cấu hình kế tiếp.

- **Các bài toán phổ biến**  sử dụng phương pháp sinh:

    * Liệt kê xâu nhị phân
    * Liệt kê tập con
    * Liệt kê hoán vị 
    * ...

- Giả mã:
```
Bước 1 (Khởi tạo):
    <Thiết lập cấu hình đầu tiên>;
Bước 2 (Bước lặp):
    while (<Lặp khi cấu hình chưa phải cuối cùng>)
    {
        <Đưa ra cấu hình hiện tại>;
        <Sinh ra cấu hình kế tiếp>;
    }
    <Đưa ra cấu hình cuối cùng>;
```

## **1.2 Sinh xâu nhị phân**
## 🧠 Phân tích bài toán
### 📘**Đề bài:** Liệt kê xâu nhị phân có độ dài N

| OUTPUT (N=3) | |
|--------------|-|
| **000**          | ← Cấu hình đầu tiên: N bit 0
| **001**          |  
| **010**          |  
| **011**          |  
| **100**          |  
| **101**          |  
| **110**          |  
| **111**          | ← Cấu hình cuối cùng: N bit 1

## Các biến toàn cục và hàm khởi tạo cấu hình đầu tiên

```cpp
int n, X[100];          // lưu cấu hình
bool final = false;     // check cấu hình cuối

void init(){
    for(int i = 1; i <= n; i++){ // Khởi tạo cấu hình đầu tiên
        X[i] = 0; // n số 0
    }
}
```

## Hàm sinh cấu hình kế tiếp:

```cpp
void sinh(){
    int i = n; // Xét từ phải sang
    while(i >= 1 && X[i] == 1){ // Lặp cho đến khi gặp số 0 đầu tiên
        // Tìm bit 0 đầu tiên từ phải sang trái. 
        // Tất cả các bit 1 đứng trước nó (bên phải nó) sẽ được đổi thành 0.
        X[i] = 0; 
        --i;
    }
    if(i == 0){ // cấu hình cuối cùng
        final = true;
    }
    else{ 
        // Đổi bit 0 tìm được thành 1 để tạo cấu hình kế tiếp nhỏ nhất.
        X[i] = 1;
    }
}
```
## 🧩 Hàm main:

```cpp
int main(){
    n = 3;
    init();
    while(!final){
        for(int i = 1; i <= n; i++){
            cout << X[i];
        }
        cout << endl;
        sinh();
    }
}
```

## **1.3 Sinh tổ hợp chập K của N phần tử**
## 🧠 Phân tích bài toán

### 📘 Đề bài:
Cho các số tự nhiên từ 1 đến N, nhiệm vụ của bạn là liệt kê các tập con có K phần tử của tập N phần tử này theo thứ tự từ điển tăng dần.

| OUTPUT (N=5, K=3) | | | |
|---|---|---|---|
|**Cấu hình đầu tiên: 123...K** → | **123** | **145** | |
| | **124** | **234** | |
| | **125** | **235** | |
| | **134** | **245** | |
| | **135** | **345** |→ **Cấu hình cuối cùng: N-K+1, N-K+2,...N** |

## 🧮 Các biến toàn cục và hàm khởi tạo cấu hình đầu tiên

```cpp
int n, k, X[100];          // lưu cấu hình
bool final = false;     // check cấu hình cuối

void init(){
    for(int i = 1; i <= k; i++){
        X[i] = i; // cấu hình đầu tiên
    }
}
```

## 🛠️ Hàm sinh cấu hình kế tiếp:

```cpp
void sinh(){
    int i = k;
    // Tìm phần tử X[i] đầu tiên từ phải sang trái chưa đạt giá trị lớn nhất có thể.
    // Giá trị lớn nhất mà X[i] có thể nhận là n - k + i 
    while(i >= 1 && X[i] == n - k + i){
        --i; 
    }
    if(i == 0){ // cấu hình cuối
        final = true;
    }
    else{ 
        // Tăng giá trị của X[i] lên 1.
        X[i]++; 
        // Đặt các phần tử từ X[i+1] trở đi bằng giá trị nhỏ nhất có thể (bằng  phần tử đứng trước + 1).
        for(int j = i + 1; j <= k; j++){
            X[j] = X[j - 1] + 1; 
        }
    }
}
```
## 🧩 Hàm main:

```cpp
int main(){
    n = 5, k = 3;
    init();
    while(!final){
        for(int i = 1; i <= k; i++){
            cout << X[i];
        }
        cout << endl;
        sinh();
    }
}
```

## **1.4 Sinh hoán vị**

## 🧠 Phân tích bài toán

### **Đề bài:** Sinh ra các hoán vị của các số tự nhiên từ 1 đến N

| OUTPUT (N=3) | |
|--------------|-|
| **123**          | ← Cấu hình đầu tiên: 123...N
| **132**          |  
| **213**          |  
| **231**          |  
| **312**          |  
| **321**          | ← Cấu hình cuối cùng: N,N-1,N-2…1

## 🧮 Các biến toàn cục và hàm khởi tạo cấu hình đầu tiên

```cpp
int n, X[100];          // lưu cấu hình
bool final = false;     // check cấu hình cuối

void init(){
    for(int i = 1; i <= n; i++){
        X[i] = i;
    }
}
```

## 🛠️ Hàm sinh cấu hình kế tiếp:

```cpp
void sinh(){
    // Bước 1: Tìm i lớn nhất sao cho X[i] < X[i+1] (tính từ n-1 về 1)
    int i = n - 1; 
    while(i >= 1 && X[i] > X[i + 1]){
        --i;
    }

    if(i == 0){
        // Nếu không tìm thấy i (i về 0), tức là dãy đã sắp xếp giảm dần -> cấu hình cuối cùng.
        final = true; 
    }
    else{
        // Bước 2: Tìm j lớn nhất từ n về i+1 sao cho X[j] > X[i]
        int j = n;
        while(X[i] > X[j]) { // Hoặc while(X[j] < X[i])
             --j;
        }

        // Bước 3: Đổi chỗ X[i] và X[j]
        swap(X[i], X[j]);

        // Bước 4: Đảo ngược đoạn từ X[i+1] đến X[n] để được cấu hình nhỏ nhất tiếp theo
        // Có thể dùng reverse(X + i + 1, X + n + 1); hoặc vòng lặp
        int left = i + 1, right = n;
        while(left < right){
            swap(X[left], X[right]);
            left++; right--;
        }
        // Hoặc #include <algorithm> rồi dùng:
        // reverse(X + i + 1, X + n + 1); 
    }
}
```
## 🧩 Hàm main:

```cpp
int main(){
    n = 3;
    init();
    while(!final){
        for(int i = 1; i <= n; i++){
            cout << X[i];
        }
        cout << endl;
        sinh();
    }
}
```

> **Mở Rộng:** Trong C++ cũng cung cấp 2 hàm **next_permutation** để
sinh ra cấu hình kế tiếp và **prev_permutation** để sinh ra cấu hình liền trước. Các bạn có thể sử dụng nó và kết hợp với mảng hoặc vector để sinh hoán vị.

### 📌 Hàm `next_permutation`

**Hàm `next_permutation`** áp dụng với mảng, đối với `vector` và `string` các bạn thay bằng iterator `begin()` và `end()`.

---

<div align="center">

### 🔷 Ví dụ:

</div>

```cpp
int main(){
    int a[] = {1, 2, 3, 4};
    do {
        for(int i = 0; i < 4; i++){
            cout << a[i];
        }
        cout << endl;
    } while(next_permutation(a, a + 4));
}
```

✅ Gợi ý:  
- `next_permutation(begin, end)` sẽ hoán vị mảng (hoặc vector/string) sang cấu hình kế tiếp theo thứ tự từ điển.
- Khi không còn hoán vị tiếp theo, nó trả về `false`.

### 📌 Hàm `prev_permutation`

**Hàm `prev_permutation`** để sinh hoán vị theo thứ tự ngược.

---

<div align="center">

### 🔷 Ví dụ:

</div>

```cpp
int main(){
    int a[] = {4, 3, 2, 1};
    do {
        for(int i = 0; i < 4; i++){
            cout << a[i];
        }
        cout << endl;
    } while(prev_permutation(a, a + 4));
}
```

# 2. Đệ quy và Quay lui
## **2.1 Đệ quy**
### Định Nghĩa Hàm Đệ Quy

- **Hàm đệ quy** là hàm tự gọi lại chính nó để giải bài toán bằng cách chia nhỏ thành các bài toán con giống hệt, cho đến khi gặp điều kiện dừng (base case).được định nghĩa là hàm gọi lại chính nó. 
- Điều kiện:
+ Điều kiện dừng (base case)
+ công thức truy hồi
- **Cú Pháp**:
```cpp
void recursive(){
    ......
    recursive();
    ......
}

int main(){
    ......
    recursive();
    ......
}
```
### Ví dụ:
Tính tổng tự nhiên từ 1 tới N bằng đệ quy 
```cpp
#include <stdio.h>

int sum(int n){
   if(n == 0){
      return 0;
   }
   else{
      return n + sum(n - 1);
   }
}

int main(){
   cout<<sum(3);
   return 0;
}
```
Giải thích:
![alt](https://cdn-blog.28tech.com.vn/media/c%20tutorial/de_quy/de_quy_2.png)

### Ví dụ 2: Tính giai thừa N!
Công thức: N! = N * (N-1)! với điều kiện dừng 0! = 1.
```cpp
long long giaiThua(int n) {
    // Điều kiện dừng (base case)
    if (n == 0) {
        return 1;
    } 
    // Công thức truy hồi
    else {
        return n * giaiThua(n - 1);
    }
}
```
Lưu ý: Gọi đệ quy quá sâu (ví dụ: tính tổng 1 tỷ số) có thể dẫn đến lỗi tràn bộ nhớ stack (Stack Overflow) do mỗi lần gọi hàm đệ quy sẽ tạo một khung nhớ mới trên stack.

## **2.2 Quay Lui**
### Khái niệm
**Thuật toán quay lui (backtracking)** là một kĩ thuật thiết kế giải thuật dựa trên đệ quy. Ý tưởng của quay lui là tìm lời giải từng bước, mỗi bước chọn một trong số các lựa chọn khả dĩ và đệ quy. 

### Tư tưởng
- Dùng để giải bài toán liệt kê các cấu hình. Mỗi cấu hình được xây dựng bằng từng phần tử. Mỗi phần tử lại được chọn bằng cách thử tất cả các khả năng.

- Các bước trong việc liệt kê cấu hình dạng X[1...n]:

    - Xét tất cả các giá trị X[1] có thể nhận, thử X[1] nhận các giá trị đó. Với mỗi giá trị của X[1] ta sẽ:
    - Xét tất cả giá trị X[2] có thể nhận, lại thử X[2] cho các giá trị đó. Với mỗi giá trị X[2] lại xét khả năng giá trị của X[3]...tiếp tục như vậy cho tới bước:
    - ...
    - ....
    - Xét tất cả giá trị X[n] có thể nhận, thử cho X[n] nhận lần lượt giá trị đó.
    - Thông báo cấu hình tìm được.

### Mô hình thuật toán

```cpp 
Backtracking(k) {
	for([Mỗi phương án chọn i(thuộc tập D)]) {
		if ([Chấp nhận i]) {
			[Chọn i cho X[k]];
			if ([Thành công]) {
				[Đưa ra kết quả];
			} else {
				Backtracking(k+1);
				[Bỏ chọn i cho X[k]];
			}
		}
	}
}
```

> Việc thêm giá trị mới vào tập đang xét rồi cuối cùng xoá bỏ nó ra khỏi tập giải thích cho tên gọi "quay lui" của thuật toán. Đó là việc khôi phục lại trạng thái cũ của tập hợp sau khi kết thúc việc gọi đệ quy.

### Ví dụ:
**Bài toán:** Liệt kê tất cả các dãy nhị phân độ dài n, là dãy có tất cả n ký tự và gồm toàn các ký 0 tự 1 và .
Ví dụ, với ta có các dãy với n = 3, 000, 001, 010, 011, 100, 101, 110, 111.

Phân tích:
Ở ví dụ phía trên, chúng ta đã nói về việc xét mọi trường hợp để xây dựng các dãy này như thế nào. Khi cài đặt đệ quy, sử dụng tư duy quy nạp "xây tập sau từ tập trước", thuật toán sẽ hoạt động như sau:

![alt text](image.png)

**CODE:**
```cpp
#include <bits/stdc++.h>
using namespace std;
int a[100001]={};
int n;

void in(){
	for (int i = 1; i <= n; i++){
		cout << a[i] << " ";
	}
	cout << endl;
}
void Gen(int i){
	for (int j = 0; j <= 1; j++){
        a[i] = j;
        if(i == n) {
            in();
        }
        else{
            Gen(i+1);
        }
		
	}
}
int main(){

	cin >> n;

	Gen(1);

}

```

## **[*] Kĩ thuật nhánh cận**

### 1. 🌟 Ý tưởng tổng quát
**Nhánh cận (Branch and Bound)** là kỹ thuật giải các bài toán tối ưu hóa khó (NP-hard) bằng cách:

- Phân nhánh bài toán thành các bài toán con nhỏ hơn.

- Tính cận trên / cận dưới cho mỗi nhánh (ước lượng tốt nhất có thể đạt).

- Cắt bỏ (Bound) các nhánh không thể dẫn tới lời giải tốt hơn lời giải tốt nhất hiện tại.

- Chìa khóa: Không xét hết mọi trường hợp như vét cạn, mà chỉ xét những nhánh có tiềm năng!

### 2. 🌟 Quy trình cơ bản
**Bước 1:** Xác định bài toán tối ưu
- Cần tối ưu (tối thiểu hóa hoặc tối đa hóa) một hàm mục tiêu.

**Bước 2:** Phân nhánh (Branching)
- Từ trạng thái hiện tại, tạo các trạng thái con bằng cách:

    - Quyết định chọn / không chọn một đối tượng.

    - Quyết định gán / không gán một giá trị.

    - Đi tiếp đến một đỉnh mới.

**Bước 3:** Tính cận (Bounding)
- Với mỗi nhánh con, ước lượng:

    - Cận trên (nếu là tối đa hóa).

    - Cận dưới (nếu là tối thiểu hóa).

    - Cận phải lạc quan, tức là giả định trường hợp thuận lợi nhất.

**Bước 4:** Cắt nhánh (Pruning)
- Nếu cận của một nhánh kém hơn lời giải tốt nhất hiện tại ➔ loại bỏ nhánh (không mở rộng tiếp).

**Bước 5:** Cập nhật lời giải tốt nhất
- Khi gặp lời giải hoàn chỉnh (chấp nhận được) tốt hơn lời giải hiện tại ➔ cập nhật.

**Bước 6:** Lặp lại đến khi:
- Không còn nhánh nào mở rộng được nữa.

### Giả mã

```cpp
void branch_and_bound(i)
{
    // Đánh giá các nghiệm mở rộng
    if ({Các_nghiệm_mở_rộng_đều_không_tốt_hơn_best_solution})
        return;
	
    for (value in S[i])
    {
        x[i] = value; // Ghi nhận thành phần thứ i.
		
        if ({Tìm_thấy_nghiệm})
            best_solution = X; // Cập nhật lại best_solution bằng nghiệm vừa tìm được.
        else 
            branch_and_bound(i + 1); // Chưa tìm thấy nghiệm thì xây dựng tiếp.
		
        {Loại_bỏ_thành_phần_thứ_i}
    }
}

```


# 3. Bài tập luyện tập
## Bài 1: Sinh xâu nhi phân thỏa mãn điều kiện

Hãy liệt kê tất cả các xâu nhị phân có độ dài 𝑛 sao cho
mỗi xâu nhị phân có duy nhất một dãy 𝑘 bít 1 liên tiếp.

**Input**
```
n = 5
k = 3
```

**Output**

```
0 0 1 1 1
0 1 1 1 0
1 0 1 1 1
1 1 1 0 0
1 1 1 0 1
```
**Giải**
```cpp
#include <bits/stdc++.h>
using namespace std;
int a[100001]={};

void inCustom(int n, int k) {
    int count_streak = 0; // Đếm số lượng dãy k bit 1 liên tiếp
    int current_streak = 0; // Độ dài dãy 1 liên tiếp hiện tại
    for (int i = 1; i <= n + 1; i++) { // Duyệt thêm 1 phần tử để xử lý dãy 1 ở cuối
        if (i <= n && a[i] == 1) {
            current_streak++;
        } else { // Gặp số 0 hoặc kết thúc xâu
            if (current_streak == k) {
                count_streak++;
            }
            current_streak = 0; // Reset streak
        }
    }

    // Nếu chỉ có đúng 1 dãy k bit 1 liên tiếp
    if (count_streak == 1) {
        for (int i = 1; i <= n; i++) {
            cout << a[i] << " ";
        }
        cout << endl;
    }
}

bool final = false;
void sinh(int n){
    int i = n; 
    while(i >= 1 && a[i] == 1){
        a[i] = 0; 
        --i;
    }
    if(i == 0){ 
        final = true;
    }
    else{ 
        a[i] = 1;
    }
}

// Hàm chính để chạy
void lietKeXauNhiPhan(int n, int k){
    // Khởi tạo cấu hình đầu tiên (toàn số 0)
    for(int i = 1; i <= n; i++) a[i] = 0;
    final = false; 

    while(!final){
        inCustom(n, k); // Kiểm tra và in cấu hình hiện tại
        sinh(n);        // Sinh cấu hình kế tiếp
    }
}

int main(){
    ios_base::sync_with_stdio(0);
    cin.tie(0); cout.tie(0);
    int n, k; // Sửa s thành k
    cin >> n >> k; // Đọc n và k
    lietKeXauNhiPhan(n, k); // Gọi hàm xử lý chính
    return 0;
}

```

## Bài 2: liệt kê tập hợp
Liệt kê tất cả các tập hợp khác rỗng chứa các số từ 1 đến n, theo thứ tự từ điển.

Input
```
3
```
Output
```
1
1 2
1 2 3
1 3
2
2 3
3
```
Code:
```cpp
#include <bits/stdc++.h>
using namespace std;
int n;
vector<vector<int>> res;
vector<int> a;
void backtrack(int i){
  if(i > n){
    if (!a.empty()) { 
        res.push_back(a);
    }
    return;
  }

  backtrack(i + 1);

  a.push_back(i);
  backtrack(i + 1);
  a.pop_back();
}
int main(){
    cin >> n;
    backtrack(1);
    sort(res.begin(), res.end());
    for(auto i: res){
        for(auto j: i){
            cout << j << " ";
        }
        cout << "\n";
    }
}
```
## Bài 3: phân tích số thành tổng các số
Cho số nguyên dương n (n≤50). Liệt kê tất cả các cách phân tích n thành tổng các số nguyên nhỏ hơn n, theo thứ tự từ điển.

Input
```
5
```
Output
```
1 1 1 1 1
1 1 1 2
1 1 3
1 2 2
1 4
2 3
```

Code:
```cpp
#include <bits/stdc++.h>
using namespace std;
int n;
vector<vector<int>> res;
vector<int> a;
void backtrack(int s){
  if(s == n){
    res.push_back(a);
    return;
  }
  int mina;
  if (a.size() == 0) mina = 1;
  else mina = a.back();
  // Chỉ cần i <= n - s vì các số hạng phải dương
  for(int i = mina; i <= n - s; i++){ 
    a.push_back(i);
    backtrack(s + i);
    a.pop_back();
  }
}
int main(){
    cin >> n;
    backtrack(0);
    sort(res.begin(), res.end());
    for(auto i: res){
        for(auto j: i){
            cout << j << " ";
        }
        cout << "\n";
    }
}
```