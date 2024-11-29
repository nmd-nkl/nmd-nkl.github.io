# HÀM CON
## MỤC LỤC
  - [Cách sử dụng hàm](#cách-sử-dụng-hàm)

    - [Truyền tham số, tham trị](#truyền-tham-số-tham-trị)

  - [Khái niệm về con trỏ](#khái-niệm-về-con-trỏ)
    - [Gán giá trị cho con trỏ](#gán-giá-trị-cho-con-trỏ)
    - [Một số lưu ý quan trọng cho con trỏ](#một-số-lưu-ý-quan-trọng)
  - [Bài tập luyện tập](#bài-tập-luyện-tập)
---
## MỤC TIÊU KIẾN THỨC
Nắm vững cách sử dụng hàm con, dùng hàm con để viết chương trình tốt hơn.

## YÊU CẦU CHUẨN BỊ
- Tìm hiểu trước các hàm.
- Chuẩn bị thiết bị.

## CHI TIẾT BÀI GIẢNG

### CÁCH SỬ DỤNG HÀM

**Khái niệm:**  
Hàm là một tập hợp các câu lệnh sẽ được thực thi nối tiếp vào chương trình khi ta gọi nó. Một chương trình có ít nhất 1 hàm là hàm `main()`.

Ví dụ: Hành động bật máy tính sẽ chạy các việc như bật wifi, bật ánh sáng màn hình, kết nối đến pin,...

**Ưu điểm:**
- Hàm con có tính sử dụng lại nhiều lần, giúp chương trình sạch và gọn gàng hơn, góp phần dễ dàng sử dụng và quản lý về sau (một câu lệnh thay cho nhiều câu lệnh).

# Cách khai báo & sử dụng

```cpp
(Kiểu trả về) tên hàm (Danh sách biến tham số) {
    Lệnh thực thi;
}
```

`Kiểu trả về`

    - void
    - float, double, string, ...

#### Ví dụ:
Viết một hàm kiểm tra số nguyên tố:

```cpp
bool isPrime(int number) {
    if (number < 2) return false;
    for (int i = 2; i <= sqrt(number); ++i) {
        if (number % i == 0) return false;
    }
    return true;
}
```

**Lưu ý, bổ sung:**  
- Xác định kiểu trả về là gì và trả về phù hợp. Nếu không trả về thì dùng hàm `void`.
- Mỗi hàm nên thực thi các hành động duy nhất để tối ưu chương trình.
- Đặt tên hàm dễ nhớ, có ý nghĩa để dễ tái sử dụng.

---

### TRUYỀN THAM SỐ, THAM TRỊ

Cách khai báo và sử dụng hàm:

```cpp
(Kiểu trả về) tên hàm (Danh sách biến tham số) {
    Lệnh thực thi;
}
```

#### Truyền tham trị (Pass by Value)

Truyền tham trị là truyền cho đối số một bản sao.

**Ví dụ:**

```cpp
void changeValue(int n) {
    n += 100;
    std::cout << "Giá trị của n trong hàm thay đổi: " << n << std::endl;
}
```

**Giải thích:**  
Khi truyền tham trị, đối số và tham số là hai biến độc lập. Việc thay đổi giá trị tham số trong hàm không ảnh hưởng đến đối số.

---

#### Truyền tham chiếu (Pass by Reference)

Truyền tham chiếu là truyền bản gốc thông qua địa chỉ `&`.

**Ví dụ:**

```cpp
void changeValue(int &n) {
    n += 100;
    std::cout << "Giá trị của n sau khi thay đổi: " << n << std::endl;
}
```

**Giải thích:**  
Khi truyền tham chiếu, tham số và đối số cùng quản lý một ô nhớ. Việc thay đổi giá trị tham số sẽ ảnh hưởng trực tiếp đến đối số.

---

# Khái niệm về con trỏ

- **Con trỏ** là một biến đặc biệt dùng để lưu trữ địa chỉ của một biến khác. Con trỏ có kiểu dữ liệu giống với biến mà nó trỏ tới.  
  Cách khai báo:

```cpp
<Kiểu dữ liệu> *<Tên con trỏ>;
```

- **Lấy địa chỉ của biến để gán cho con trỏ:**  
  Con trỏ được gán địa chỉ của một biến bằng cách sử dụng toán tử `&`.

```cpp
<Tên con trỏ> = &<Tên biến>;
```

- **Lấy giá trị tại địa chỉ mà con trỏ trỏ đến:**  
  Sử dụng toán tử `*` để truy cập giá trị tại địa chỉ mà con trỏ trỏ tới.

```cpp
cout << *<Tên con trỏ>;
```

- **Phép gán giữa các con trỏ:**  
  Gán địa chỉ từ con trỏ này sang con trỏ khác bằng cách gán trực tiếp.

```cpp
<Tên con trỏ 1> = <Tên con trỏ 2>;
```
# Gán giá trị cho con trỏ

- **Khái niệm:** Con trỏ (pointer) là một biến chứa địa chỉ bộ nhớ của một biến khác. Do đó, khi gán giá trị cho con trỏ, giá trị đó phải là một địa chỉ hợp lệ.

- **Cách sử dụng:**  
  Ví dụ sau minh họa việc gán giá trị cho con trỏ:

```cpp
#include <iostream>
using namespace std;

int main() {
    int value = 10;          // Khởi tạo biến value
    int *ptr = &value;       // Gán địa chỉ của biến value cho con trỏ ptr

    cout << &value << '\n';  // In địa chỉ của biến value
    cout << ptr << '\n';     // In địa chỉ mà con trỏ ptr đang giữ
    cout << *ptr << '\n';    // In giá trị tại địa chỉ mà ptr trỏ đến (tương đương value)

    return 0;
}
```

**Kết quả in ra màn hình:**
```
Địa chỉ của value (ví dụ): 0x7ffee4d091a4
Địa chỉ trong ptr: 0x7ffee4d091a4
Giá trị tại địa chỉ ptr: 10
```

---

## Một số lưu ý quan trọng:

1. **Con trỏ không được khởi tạo (dangling pointer):**
   - Nếu con trỏ không được gán địa chỉ ban đầu, giá trị của nó sẽ là ngẫu nhiên, dễ dẫn đến lỗi truy cập bộ nhớ.
   - Nên khởi tạo con trỏ bằng `nullptr` nếu chưa xác định địa chỉ cụ thể.

```cpp
int *ptr = nullptr; // Khởi tạo con trỏ rỗng
```

2. **Con trỏ với hàm:**
   - Con trỏ thường được sử dụng để truyền tham số kiểu tham chiếu trong các hàm, giúp thay đổi giá trị của đối số từ bên trong hàm.

```cpp
void changeValue(int *n) {
    *n += 100; // Thay đổi giá trị của biến n mà con trỏ trỏ đến
}

int main() {
    int num = 10;
    changeValue(&num); // Truyền địa chỉ của num vào hàm
    cout << num << endl; // Giá trị của num sẽ là 110
    return 0;
}
```
---

### BÀI TẬP LUYỆN TẬP

1. Viết hàm đổi chỗ 2 số tự nhiên `a` và `b`. <Bằng & và con trỏ *>
2. Viết hàm tìm số lớn nhất trong 3 số `a`, `b`, `c`.
3. Viết hàm tính giá trị tuyệt đối, giai thừa, lũy thừa, kiểm tra số chẵn/lẻ.
4. Viết chương trình sử dụng hàm con để:
    - Tính tổng 3 số nguyên nhập từ bàn phím.
    - Kiểm tra số nguyên tố, số chính phương.
    - Tìm ước chung lớn nhất, bội chung bé nhất của 2 số.
    - In ra màn hình các số chia hết cho 3 nhưng không chia hết cho 7 từ 1 đến 100.
5. Giải bài tập:
    - [BCPRIME trên SPOJ](https://www.spoj.com/PTIT/problems/BCPRIME/)
    - [BCFACT trên SPOJ](https://www.spoj.com/PTIT/problems/BCFACT/)
``` 