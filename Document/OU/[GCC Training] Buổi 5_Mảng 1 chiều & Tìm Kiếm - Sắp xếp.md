# BUỔI 5: MẢNG 1 CHIỀU - TÌM KIẾM VÀ SẮP XẾP

  - [Mảng 1 chiều](#mảng-1-chiều)
    - [1. Định nghĩa, cách khai báo và các tính chất của mảng 1 chiều](#1-định-nghĩa-cách-khai-báo-và-các-tính-chất-của-mảng-1-chiều)
    - [2. Cách khai báo mảng 1 chiều](#2-cách-khai-báo-mảng-1-chiều)
    - [3. Tính chất của mảng 1 chiều](#3-tính-chất-của-mảng-1-chiều)
  - [Cách sử dụng mảng 1 chiều](#cách-sử-dụng-mảng-1-chiều)
    - [1. Chỉ số mảng](#1-chỉ-số-mảng)
    - [2. Duyệt mảng](#2-duyệt-mảng)
    - [3. Sử dụng mảng làm tham số](#3-sử-dụng-mảng-làm-tham-số)
    - [4. Mối quan hệ giữa con trỏ và mảng](#4-mối-quan-hệ-giữa-con-trỏ-và-mảng)
  - [Sắp xếp và tìm kiếm](#sắp-xếp-và-tìm-kiếm)
    - [1. Các thuật toán sắp xếp cơ bản](#1-các-thuật-toán-sắp-xếp-cơ-bản)
    - [2. Các thuật toán tìm kiếm](#2-các-thuật-toán-tìm-kiếm)
- [Các bài tập và ví dụ](#các-bài-tập-và-ví-dụ)

---
## Nội dung buổi học
- Giới thiệu mảng 1 chiều (cách khai báo và sử dụng).
- Tìm hiểu về các thuật toán tìm kiếm và sắp xếp liên quan đến mảng 1 chiều.
---

## Yêu cầu kiến thức cần chuẩn bị

- Tìm hiểu sơ qua về cách khai báo mảng 1 chiều và các thuật toán tìm kiếm - sắp xếp cơ bản.

---

## Chi tiết bài giảng

### Mảng 1 chiều

#### 1. Định nghĩa, cách khai báo và các tính chất của mảng 1 chiều

- **Định nghĩa:** Mảng 1 chiều là cấu trúc dữ liệu (*data structure*) dùng để lưu trữ nhiều phần tử có cùng kiểu dữ liệu. Các phần tử trong mảng được lưu trữ tại các ô nhớ cạnh nhau trong bộ nhớ.
- **Lý do sử dụng:** Giúp lưu trữ n số một cách gọn gàng, tránh việc phải khai báo nhiều biến riêng lẻ.

#### 2. Cách khai báo mảng 1 chiều

**Cú pháp:**
```cpp
<kiểu dữ liệu> <tên mảng>[<số các phần tử của mảng>];
```

**Ví dụ:**
```cpp
int a[100];
char s[100];
```

**Hoặc khai báo và khởi tạo giá trị ban đầu:**
```cpp
int a[5] = {1, 2, 3, 4, 5};
char s[4] = {'g', 'c', 'c'};
```

**Lưu ý:** 
- Kích thước tối đa của mảng 1 chiều dạng cục bộ là \(1e5\).
- Để khai báo mảng kích thước \(1e6\) hoặc \(1e7\), nên khai báo toàn cục.

#### 3. Tính chất của mảng 1 chiều:
- Đơn giản và dễ sử dụng.
- Thuận tiện truy xuất giá trị qua chỉ số.
- Sử dụng nhiều nhất trong lập trình.
- Kích thước cố định, không thể mở rộng.

---

### Cách sử dụng mảng 1 chiều

#### 1. Chỉ số mảng
- Chỉ số bắt đầu từ 0.
- Với mảng có kích thước \(n\), chỉ số chạy từ 0 đến \(n-1\).

**Truy cập phần tử:**
```cpp
<tên mảng>[<chỉ số>];
```

**Ví dụ:**
```cpp
int a[5] = {1, 2, 3, 4, 5};
cout << a[2]; // In ra phần tử thứ 3 của mảng (giá trị: 3)
```

**Lưu ý:** 
Khi truy cập phần tử ngoài phạm vi, chương trình không báo lỗi nhưng sẽ trả về giá trị rác.

#### 2. Duyệt mảng

**Ví dụ nhập giá trị cho các phần tử:**
```cpp
void nhap() {
    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }
}
```

#### 3. Sử dụng mảng làm tham số

**Ví dụ:**
```cpp
void tinhtong(int a[], int n) {
    int sum = 0;
    for (int i = 0; i < n; i++) {
        sum += a[i];
    }
}
```

#### 4. Mối quan hệ giữa con trỏ và mảng

- Giá trị của mảng là địa chỉ phần tử đầu tiên.
- Tên mảng là hằng con trỏ.

**Ví dụ:**
```cpp
int a[] = {1, 2, 3, 4, 5};
int* p = &a[0]; // p trỏ đến địa chỉ của phần tử đầu tiên
for (int i = 0; i < 5; i++) {
    cout << *(p + i) << " "; // In ra: 1 2 3 4 5
}
```

---

### Sắp xếp và tìm kiếm

#### 1. Các thuật toán sắp xếp cơ bản

- **Mục đích:** Sắp xếp các phần tử theo thứ tự tăng/giảm.
- **Thuật toán cơ bản:** 
  - Đổi chỗ trực tiếp.
  ```cpp
    void Sort(vector<int>& a) {
    for (int i = 0; i < a.size() - 1; ++i)
        for (int j = i + 1; j < a.size(); ++j)
            if (a[i] > a[j]) swap(a[i], a[j]);
    }
  ```
  - Sắp xếp chọn.
  ```cpp
    void Sort(vector<int>& a) {
        for (int i = 0; i < a.size() - 1; ++i) {
            int minIdx = i;
            for (int j = i + 1; j < a.size(); ++j)
                if (a[j] < a[minIdx]) minIdx = j;
            swap(a[i], a[minIdx]);
        }
    }
  ```
  - Sắp xếp nổi bọt.
  ```cpp
    void Sort(vector<int> a, int n){	
	    bool check;
        int buoc = 1;
	    for (int i=0; i < n; i++){ 
		    check = false;
		    for (int j=0; j<n-i-1; j++ ) {
			    if (a[j] > a[j+1] ) { 
			    	check = true;
				    swap(a[j], a[j+1]);
			    }
		    }
            if(!check) break; 
	    }
    }
  ```
  - Sắp xếp chèn.
  ```cpp
    void Sort(vector<int>& a) {
        for (int i = 1; i < a.size(); ++i) {
            int key = a[i], j = i - 1;
            while (j >= 0 && a[j] > key) a[j + 1] = a[j--];
            a[j + 1] = key;
        }
    }
  ```

#### 2. Các thuật toán tìm kiếm

**Tìm kiếm tuyến tính:**
```cpp
bool timKiemTuyenTinh(int a[], int n, int k) {
    for (int i = 0; i < n; i++) {
        if (a[i] == k) return true;
    }
    return false;
}
```

- Độ phức tạp: \(O(n)\).

**Tìm kiếm nhị phân:**
Áp dụng khi mảng đã sắp xếp.

```cpp
bool timKiemNhiPhan(int a[], int n, int k) {
    int left = 0, right = n - 1;
    while (left <= right) {
        int mid = (left + right) / 2;
        if (a[mid] == k) return true;
        else if (a[mid] < k) left = mid + 1; //tìm kiếm ở nửa sau
        else right = mid - 1; //tìm kiếm ở nửa trước
    }
    return false;
}
```

- Độ phức tạp: \(O(log n)\).

---

### Các bài tập và ví dụ

1. Tìm phần tử lớn nhất hoặc nhỏ nhất của mảng.
2. Đếm số phần tử có giá trị bằng **k**.