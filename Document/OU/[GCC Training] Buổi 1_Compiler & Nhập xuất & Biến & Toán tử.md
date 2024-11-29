# Buổi 1: Compiler, Nhập xuất, Biến, Toán tử

## Mục lục

- [1. Tổng quan về C++](#1-tổng-quan-về-c)
- [2. Cấu trúc chương trình C++](#2-cấu-trúc-chương-trình-c)
- [3. Biến trong C++](#3-biến-trong-c)
  - [3.1. Các kiểu dữ liệu](#31-các-kiểu-dữ-liệu)
  - [3.2. Biến toàn cục và cục bộ](#32-biến-toàn-cục-và-cục-bộ)
- [4. Toán tử trong C++](#4-toán-tử-trong-c)
- [5. Ép kiểu](#5-ép-kiểu)
- [6. Bài tập luyện tập](#6-bài-tập-luyện-tập)


---
## Nội dung buổi học

- Hướng dẫn cài đặt IDE (Dev C++) và sửa các lỗi trong Dev C++.
- Hướng dẫn sử dụng Codeforces (submit bài, chọn trình biên dịch, ...).
- Giới thiệu về:
  - Nhập xuất trong C++.
  - Biến và các kiểu dữ liệu.
  - Các toán tử trong C++ (1 ngôi, 2 ngôi).

---

## Yêu cầu kiến thức cần chuẩn bị

- Tạo tài khoản trên Codeforces và add nick của các bạn.
- Hiểu về các kiểu dữ liệu cơ bản trong C++.
- Nắm được cấu trúc của một chương trình C++.

---

## Bài giảng chi tiết

### 1. Tổng quan về C++
C++ là ngôn ngữ lập trình bậc trung, phát triển bởi **Bjarne Stroustrup** vào năm 1979. Đây là phần mở rộng của ngôn ngữ lập trình C, kết hợp các tính năng của ngôn ngữ cấp cao và cấp thấp.

- **Đặc điểm**: 
  - Đa nền tảng (Windows, macOS, Unix).
  - Hỗ trợ lập trình tổng quát, hướng đối tượng, và thủ tục.

---

### 2. Cấu trúc chương trình C++

**Ví dụ về chương trình C++:**
```cpp
// khai báo thư viện
#include <iostream>
using namespace std;
// hàm main
int main() {
    cout << "Hello, world!";
    return 0;
}
```

**Cấu trúc chính:**
- **Lệnh tiền xử lý**: `#include <iostream>` và `using namespace std`.
- **Hàm main**: Điểm bắt đầu của chương trình.
- **Câu lệnh và biểu thức**: `cout` để in ra màn hình.
- **Chú thích**: Sử dụng `//` hoặc `/* ... */`.

Nói về tự khóa `const` :

  Được sử dụng để định nghĩa hằng số trong C++.

  Vd : **const** **float** PI = 3.14;

  Và bây giờ biến PI không thể thay đổi, nếu cố gắng thay đổi sẽ gặp lỗi.

---

### 3. Biến trong C++

#### 3.1. Các kiểu dữ liệu

| Kiểu             | Kích thước       | Vùng giá trị                                                        |
|-------------------|------------------|--------------------------------------------------|
| `char`           | 1 byte           | -128 tới 127 hoặc 0 tới 255                                              |
| `unsigned char`  | 1 byte           | 0 tới 255                                                                   |
| `signed char`    | 1 byte           | -128 tới 127                                                    |
| `int`            | 2 hoặc 4 bytes   | -32,768 tới 32,767 hoặc -2,147,483,648 tới 2,147,483,647       |
| `unsigned int`   | 2 hoặc 4 bytes   | 0 tới 65,535 hoặc 0 tới 4,294,967,295               |
| `short`          | 2 bytes          | -32,768 tới 32,767                               |
| `unsigned short` | 2 bytes          | 0 tới 65,535                                        |
| `long`           | 4 bytes          | -2,147,483,648 tới 2,147,483,647                 |
| `unsigned long`  | 4 bytes          | 0 tới 4,294,967,295                              |
| `float`          | 4 bytes              | Khoảng 6-7 chữ số thập phân               |
| `double`         | 8 bytes            | Khoảng 15-16 chữ số thập phân             |
                            

#### 3.2. Biến toàn cục và cục bộ

| Đặc điểm                | Biến global                     | Biến local             |
|-------------------------|---------------------------------|-----------------------|
| **Vị trí khai báo**     | Ngoài `main`                   | Trong hàm hoặc khối lệnh |
| **Phạm vi sử dụng**     | Toàn chương trình              | Chỉ trong hàm hoặc khối đó |

### Toán tử nhập xuất trong C++ 
- Hàm  `cout <<` được sử dụng để in lệnh đã cho ra màn hình.
- Hàm `cin >>`  được dùng để đọc dữ liệu đầu vào từ bàn phím.

- Định dạng kiểu in (giới thiệu sơ qua, bảo các em về nhà tìm hiểu thêm)

Ví dụ để in ra giá trị số float, double với độ chính xác k chữ số sau dấu phẩy bạn thêm cụm `<< fixed << setprecision(k)` trước tên biến.(cần khai báo thư viện `"iomanip"` )
`setw()`,`setfill`,....

---

### 4. Toán tử trong C++

#### 4.1. Toán tử gán
| Toán tử | Ví dụ   | Tương đương           |
|---------|---------|-----------------------|
| `=`     | `C = A` | Gán giá trị của A vào C |
| `+=`    | `C += A`| `C = C + A`           |
| `-=`    | `C -= A`| `C = C - A`           |
| `*=`    | `C *= A`| `C = C * A`           |
| `/=`    | `C /= A`| `C = C / A`           |

#### 4.2. Toán tử số học
| Toán tử | Miêu tả                  
|---------|--------------------------|
| `+`     | Cộng                          |
| `-`     | Trừ                      |
| `/`     | Chia (phần nguyên nếu là số nguyên) & Không chia được cho 0| 
| `*`     | Nhân                   |
|  `%` |     Chia lấy dư|
| `++`| cộng 1 đơn vị : tương đương `A += 1` 
| `--`| cộng 1 đơn vị : tương đương `A -= 1` 

| Toán tử  | Ý nghĩa                          | Thứ tự thực hiện         |
|----------|----------------------------------|--------------------------|
| `a++`    | Hậu tố: Tăng giá trị sau khi sử dụng | Sử dụng giá trị ban đầu, sau đó tăng |
| `++a`    | Tiền tố: Tăng giá trị trước khi sử dụng | Tăng giá trị trước, sau đó sử dụng   |


### 5. Ép kiểu

Đôi khi chúng ta cần chuyển đổi giá trị một biểu thức sang kiểu dữ liệu khác. Ví dụ trong trường hợp ta muốn thực hiện phép toán chia lấy phần dư của 2 số nguyên, nhưng lại được lưu trong **2 biến kiểu `float`**, ta không thể áp dụng trực tiếp toán tử `%` cho 2 biến đó. Bạn chạy chương trình thế này sẽ báo lỗi:

```cpp
#include <iostream>
using namespace std;

int main()
{
    int a = 5, c;
    float b = 6;
    c = a % b;

    cout << c;
    return 0;
}
```

Vì thế cần ép kiểu theo cú pháp:

```
<kiểu dữ liệu> <biểu thức>
```

để lấy giá trị từ biến `b`, đổi sang số nguyên để thực hiện phép `%`. Code đúng như sau:

```cpp
#include <iostream>
using namespace std;

int main()
{
    int a = 5, c;
    float b = 6;
    c = a % (int)b;

    cout << c;
    return 0;
}
```
---

### 6. Bài tập luyện tập

- Nêu ví dụ về swap giá trị của hai biến

    - Có thể dùng biến thứ 3 tạm bằng toán tử gán

    - Có thể dùng toán tử toán học để thay đổi giá trị. VD = a = a + b, b = a - b, a = a - b


#### Bài 1: Chu vi và diện tích hình tròn
Nhập bán kính `r` (0 < r < \(10^9\)). Tính chu vi và diện tích:
**Example**:

| Input | Output       |
|-------|--------------|
| 3     | 18.85        |
|       | 28.27        |
```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
    int r;
    cin >> r;
    double pi = 3.14159;
    cout << fixed << setprecision(2);
    cout << "Chu vi: " << 2 * pi * r << endl;
    cout << "Dien tich: " << pi * r * r << endl;
    return 0;
}
```

#### Bài 2: Định dạng ngày tháng năm
Nhập 3 số `d, m, y` (ngày, tháng, năm) và in dưới dạng `dd/mm/yyyy`.
**Example**:

| Input      | Output    |
|------------|-----------|
| 5 12 2021  | 05/12/2021 |
```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
    int d, m, y;
    cin >> d >> m >> y;
    cout << setw(2) << setfill('0') << d << "/";
    cout << setw(2) << setfill('0') << m << "/";
    cout << y << endl;
    return 0;
}
```

#### Bài 3: Tính tổng trong đoạn `[l; r]`
Nhập 2 số `l, r`. Tính tổng các số nguyên trong đoạn `[l; r]`.

**Example**:

| Input  | Output |
|--------|--------|
| 5 10   | 45     |
