### **BUỔI 7: MẢNG ĐÁNH DẤU, TẦN SỐ, MẢNG CỘNG DỒN, MẢNG HIỆU**

---

## Mục lục

- [MẢNG ĐÁNH DẤU & TẦN SỐ](#mảng-đánh-dấu--tần-số)
  - [Bài toán](#bài-toán)
  - [Cách làm bằng mảng đánh dấu](#cách-làm-bằng-mảng-đánh-dấu)
  - [Ưu & Nhược điểm của mảng đánh dấu](#ưu--nhược-điểm-của-mảng-đánh-dấu)
- [MẢNG CỘNG DỒN 1 CHIỀU](#mảng-cộng-dồn-1-chiều)
  - [Bài toán mảng cộng dồn](#bài-toán-mảng-cộng-dồn)
  - [Cách làm bằng mảng cộng dồn](#cách-làm-bằng-mảng-cộng-dồn)
  - [Ưu & Nhược điểm của mảng cộng dồn](#ưu--nhược-điểm-của-mảng-cộng-dồn)
- [Lưu ý Mảng đánh dấu & Cộng dồn](#lưu-ý-mảng-đánh-dấu--cộng-dồn)
- [BÀI TẬP](#bài-tập)
  - [1. Mảng cộng dồn](#1-mảng-cộng-dồn)
  - [2. Mảng cộng dồn 1 chiều](#2-mảng-cộng-dồn-1-chiều)

---
# **MẢNG ĐÁNH DẤU & TẦN SỐ**
### **Bài toán:**  
Cho 1 mảng có **n** phần tử, nhập vào **n** số **a[i]** là phần tử của mảng. Cho **Q** truy vấn, mỗi truy vấn nhập số **X**. In ra “Yes” nếu số X có trong mảng và “No” nếu không có trong mảng.
### **Cách làm Ngây thơ:**
```cpp
int q; cin >> q;
while (q--) {
    int so, timThay = 0;
    cin >> so;
    for (int i = 0; i < n; i++) {
        if (a[i] == so) {
            timThay = 1;
            break;
        }
    }
    if (timThay == 1) cout << "Yes\n";
    else cout << "No\n";
}

```

Với cách làm này, nếu phần tử không có trong mảng, với mỗi truy vấn đều tốn N câu lệnh **(O(n))**
### **Cách làm bằng mảng đánh dấu:**

Lấy giá trị của mảng **a[i]** làm chỉ số của mảng đánh dấu freq[]. 

Mỗi truy vấn chỉ mất 1 phép tính.
```cpp
int freq[maxVal + 5];

// Khởi tạo mảng
for (int i = 0; i <= maxVal + 5; i++)
    freq[i] = 0;

for (int i = 0; i < n; i++)
    freq[a[i]]++; // Đánh dấu

int q; cin >> q;

while (q--) {
    int x;
    cin >> x;

    if (freq[x]) cout << "Yes\n";
    else cout << "No\n";
}
```

### **`Ưu & Nhược điểm của mảng đánh dấu:`**
**`Ưu`:** Nhanh hơn, mỗi truy vấn chỉ mất O(1)

**`Nhược`:** Tốn thêm bộ nhớ để lưu trữ mảng freq[] (không cần thiết nếu Q = 1)

**[Nói thêm về: Khai báo mảng ngoài hàm main]**

Cách xử lý khi bạn muốn khai báo mảng cỡ $10^6$ hoặc $10^7$ phần tử mà không bị tràn stack đó là khai báo mảng ở **phạm vi toàn cục**

Khi bạn khai báo trong main thì vùng nhớ cấp phát để lưu mảng là vùng nhớ `stack` (tương đối nhỏ) còn khi bạn khai báo mảng ngoài main thì vùng nhớ cấp phát cho mảng là vùng nhớ `Uninitialized data segment`. 

---
# **MẢNG CỘNG DỒN 1 CHIỀU**
### **Bài toán mảng cộng dồn:**  
Cho 1 mảng có **n** phần tử, nhập vào **n** số **a[i]** là phần tử của mảng. Cho **Q** truy vấn, mỗi truy vấn nhập 2 số **L, R**. In ra tổng của dãy **a[L] + a[L+1] + … a[R]** với mỗi truy vấn.

### **Cách làm Ngây thơ:** 
Mỗi truy vấn thực hiện L-R+1 câu lệnh

```cpp
int Q;

cin >> Q;
while (Q--) {
    int L, R;

    cin >> L >> R;

    int sum = 0;

    for (int i = L; i <= R; i++) {
        sum += a[i];
    }

    cout << sum << '\n';
}
```
### **Cách làm bằng mảng cộng dồn:**
Ta sẽ tạo một mảng **Sum[]** với công thức truy hồi sau O(n):

```cpp
// Lưu ý: Mảng a[] nhập từ idx 1
for (int i = 1; i <= n; i++) {
    Sum[i] = Sum[i - 1] + a[i];
}
int Q;
cin >> Q;
while (Q--) {
    int L, R;
    cin >> L >> R;
    cout << Sum[R] - Sum[L - 1] << '\n';
}
```
- **Sum[0] = 0**
- **Sum[i] = Sum[i-1] + a[i]**

**Khi đó, ta nhận thấy với mảng**

`a1, a2, a3, a4, a5`

**Thì mảng Sum là:**

- vị trí 1: a1

- vị trí 2: a1+ a2

- vị trí 3: a1+a2+a3

- vị trí 4: a1 + a2 + a3 + a4

- vị trí 5: a1 + a2 + a3 + a4 + a5

Như vậy, ví dụ ta cần lấy tổng từ 2 -> 5, nó sẽ bằng 

|b[5] - b[1] = a1+a2+a3+a4+a5 - a1 = a2+a3+a4+a5 |
|-|

### **Ưu & Nhược điểm của mảng cộng dồn:**
**Ưu:** Nhanh hơn, mỗi truy vấn chỉ mất O(1)

**Nhược:** Tốn thêm bộ nhớ để lưu trữ mảng Sum[]

### **`Lưu ý Mảng đánh dấu & Cộng dồn:`**
|1. Không sử dụng được với **số âm**, vì chỉ số trong mảng không thể là số âm|
|-|
|2. Chỉ áp dụng được cho mảng có  giá trị phần tử **`[0, 10^7]`**|
---
# **BÀI TẬP**
### **1. Mảng cộng dồn:** 
#### **`Bài Toán 1` :** 
|Cho mảng A[] gồm N phần tử là số nguyên trong đoạn $[0, 10^6]$, hãy liệt kê các giá trị khác nhau trong mảng theo thứ tự từ nhỏ tới lớn.|
|-|
#### **`Bài Toán 2` :** 
|Cho mảng A[] gồm N phần tử là số nguyên trong đoạn $[0, 10^6]$, hãy liệt kê các giá trị khác nhau trong mảng theo thứ tự xuất hiện trong mảng, mỗi giá trị chỉ liệt kê 1 lần|
|-|
###### Ý tưởng: Sau khi in ra giá trị thì bạn bỏ đánh dấu giá trị đó để tránh in trùng.
#### **`Bài Toán 3` :** 
|Liệt kê các phần tử xuất hiện ít nhất 2 lần trong mảng theo thứ tự xuất hiện trong mảng, mỗi phần tử chỉ liệt kê 1 lần|
|-|
#### **`Bài Toán 4` :** 
|Cho mảng A[] và B[], hãy liệt kê các giá trị thuộc giao, hợp của hai mảng, mỗi giá trị liệt kê 1 lần theo thứ tự tăng dần. Dòng 1, 2 output lần lượt in giao, hợp của 2 mảng.|
|-|
### **2. Mảng cộng dồn 1 chiều:**
#### **`Bài Toán`:** 
|Cho mảng số nguyên **A[]** gồm **N** phần tử, hãy liệt kê các chỉ số i trong mảng thỏa mãn : Tổng các phần tử bên trái i và tổng các phần tử bên phải i là các số nguyên tố|
|-|

###### Gợi ý : Đối với mỗi chỉ số i xây dựng 1 vòng for duyệt từ 0 tới i - 1 để tính tổng các số bên trái của i, 1 vòng for duyệt từ i + 1 tới N - 1 để tính tổng các phần tử nằm bên phải của i => Kiểm tra cả 2 tổng là số nguyên tố thì in ra chỉ số i, chú ý reset biến tổng trái và phải tại mỗi vòng lặp. Và TRƯỜNG HỢP i = 0 và i = n - 1.
