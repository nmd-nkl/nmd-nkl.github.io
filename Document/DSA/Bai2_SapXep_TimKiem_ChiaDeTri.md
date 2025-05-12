
# Buổi 3: Sắp xếp và tìm kiếm, chia để trị

## Sắp xếp:

### Nhắc lại sắp xếp thông thường: (độ phức tạp O(n^2))
- Sắp xếp đổi chỗ trực tiếp.
- Sắp xếp chọn.
- Sắp xếp chèn.
- Sắp xếp nổi bọt.

### Các loại sắp xếp tối ưu hơn:

#### Quick Sort: 
- Độ phức tạp trung bình / tốt nhất: O(nlogn).
- Độ phức tạp tệ nhất: O(n^2).

```cpp
#include<bits/stdc++.h>
using namespace std;
#define ll long long
int M = 1e9 + 7;

int Partition(int a[], int l, int r)
{
    int x = a[r], pos = l - 1;
    for (int i = l; i < r; i++)
    {
        if (a[i] <= x)
        {
            pos++;
            swap(a[pos], a[i]);
        }
    }
    swap(a[pos + 1], a[r]);
    return pos + 1;
}

void QuickSort(int a[], int l, int r)
{
    if (l < r)
    {
        int pivot = Partition(a, l, r);
        QuickSort(a, l, pivot - 1);
        QuickSort(a, pivot + 1, r);
    }
}

int main ()
{
    int n;
    cin >> n;
    int a[n];
    for (int i = 0; i < n; i++) cin >> a[i];

    QuickSort(a, 0, n - 1);
    for (int i = 0; i < n; i++) cout << a[i] << " ";
}
```

#### Merge Sort:
- Độ phức tạp trung bình / tốt nhất/ tệ nhất: O(nlogn).

```cpp
#include<bits/stdc++.h>
using namespace std;
#define ll long long
int M = 1e9 + 7;

void Combine(int a[], int l, int m, int r)
{
    int n1 = m - l + 1;
    int n2 = r - m;

    int L[n1], R[n2];
    for (int i = 0; i < n1; i++) L[i] = a[l + i];
    for (int i = 0; i < n2; i++) R[i] = a[m + i + 1];

    int i = 0, j = 0, pos = l;
    while (i < n1 && j < n2)
    {
        if (L[i] <= R[j]) a[pos++] = L[i++];
        else a[pos++] = R[j++];
    }

    while (i < n1) a[pos++] = L[i++];
    while (j < n2) a[pos++] = R[j++];
}

void MergeSort(int a[], int l, int r)
{
    if (l < r)
    {
        int m = (l + r) / 2;
        MergeSort(a, l, m);
        MergeSort(a, m + 1, r);
        Combine(a, l, m, r);
    }
}

int main ()
{
    int n;
    cin >> n;
    int a[n];
    for (int i = 0; i < n; i++) cin >> a[i];

    MergeSort(a, 0, n - 1);
    for (int i = 0; i < n; i++) cout << a[i] << " ";
}
```

**Bài tập**: Code lại 2 thuật toán sắp xếp trên.

## Tìm kiếm:

### Tìm kiếm tuần tự: O(n)

### Tìm kiếm nhị phân:
- Độ phức tạp: O(log(n))

```cpp
#include<bits/stdc++.h>
using namespace std;
#define ll long long
int M = 1e9 + 7;

int Binary_Search(int a[], int n, int x)
{
    int l = 0, r = n - 1;
    while (l < r)
    {
        int m = (l + r) / 2;
        if (x == a[m]) return m + 1;
        else if (x > a[m]) l = m + 1;
        else r = m - 1;
    }
    return -1;
}

int main ()
{
    int n, k;
    cin >> n >> k;

    int a[n];
    for (int i = 0; i < n; i++) cin >> a[i];
    sort(a, a + n);

    cout << Binary_Search(a, n, k) << endl;
}
```

**Bài tập**: Code lại thuật toán

### Lower_bound, Upper_bound: (nhắc lại)
- `Lower_bound(begin, end, value)` → Trả về iterator trỏ tới phần tử đầu tiên `>= value`  
- `Upper_bound(begin, end, value)` → Trả về iterator trỏ tới phần tử đầu tiên `> value`  

## Chia để trị:

### Khái niệm:
- **Mục tiêu**: giảm thời gian chạy.
- **Ý tưởng**: áp dụng đệ quy theo 3 bước:
  1. **Divide (chia)**: chia bài toán lớn thành các bài toán con có cùng kiểu.
  2. **Conquer (trị)**: giải bài toán con.
  3. **Combine (tổng hợp)**: tổng hợp lại kết quả của bài toán con → kết quả của bài toán lớn.

- **Áp dụng**: Khi có thể chia bài toán lớn thành các bài toán con giống với bài toán gốc nhưng với kích thước nhỏ hơn.

### Các bài toán áp dụng:
- Tìm kiếm nhị phân.
- Merge Sort, Quick Sort.

### Nhân số nguyên lớn:

**Đặt bài toán**: Cho 2 số nguyên `a` và `b`, trong đó (0 < a, b < 10^18). Tính `a * b (mod 19^12 + 19)`.

**Cách làm**: Biến phép nhân `a * b` thành tổng của 2 phép nhân `a * (b / 2)`.

```cpp
#include <bits/stdc++.h>
using namespace std;
#define ll long long

ll M = 1e12 + 19;

ll PowNum(ll a, ll b)
{
    if (b == 0) return 0;

    ll tmp = PowNum(a, b / 2);
    tmp = (tmp + tmp) % M;

    if (b % 2 == 1) tmp = (tmp + a) % M;
    return tmp;
}

int main ()
{
    ll a, b;
    cin >> a >> b;
    cout << PowNum(a, b);
}
```

### Tính lũy thừa:

**Đặt bài toán**: Tính lũy thừa `a^n` với độ phức tạp tối ưu hơn `O(n)`.

**Cách làm**: Giải các bài toán con:
- `a^n = 1` nếu `n = 0`
- `a^n = a^(n/2) * a^(n/2)` nếu `n` chẵn
- `a^n = a * a^(n/2) * a^(n/2)` nếu `n` lẻ

```cpp
#include <bits/stdc++.h>
using namespace std;
#define ll long long

int Power(int a, int n)
{
    if (n == 0) return 1;

    int tmp = Power(a, n / 2);
    tmp = tmp * tmp;

    if (n % 2 == 1) tmp = a * tmp;
    return tmp;
}

int main ()
{
    int a, n;
    cin >> a >> n;
    cout << Power(a, n);
}
```

## Xâu Fibonacci:
**Cho các em về tự tìm hiểu**.

**Đặt bài toán**: Cho trước 2 xâu `g(1)` và `g(2)`  
(với `g(1) = A`, `g(2) = B`, `g(n) = g(n - 2) + g(n - 1)`)  
→ Cho `n` và `k`. Xác định ký tự thứ `k` trong xâu `g(n)`.
