# Buổi 2: Toán tử logic, cấu trúc rẽ nhánh
## Mục lục

- [1. Toán tử logic và quan hệ](#1-toán-tử-logic-và-quan-hệ)
  - [1.1 Toán tử quan hệ](#11-toán-tử-quan-hệ)
  - [1.2 Toán tử logic](#12-toán-tử-logic)
- [2. Cấu trúc rẽ nhánh](#2-cấu-trúc-rẽ-nhánh)
  - [2.1 Lệnh `if...else`](#21-lệnh-ifelse)
  - [2.2 Lệnh `switch case`](#22-switch-case)
- [3. Thư viện `math.h`](#3-thư-viện-mathh)
- [4. Luyện tập](#4-luyện-tập)
---


### 1. Toán tử logic và quan hệ

#### 1.1 Toán tử quan hệ:

Bảng dưới đây chỉ ra tất cả các toán tử quan hệ được hỗ trợ bởi ngôn ngữ C++. Giả sử rằng biến `A` có giá trị 10 và biến `B` có giá trị 20, ta có:

| Toán tử | Miêu tả                                                                 | Ví dụ            |
|---------|-------------------------------------------------------------------------|------------------|
| `==`    | Kiểm tra nếu 2 toán hạng bằng nhau hay không. Nếu bằng thì điều kiện là `true`. | `(A == B)` là `false`. |
| `!=`    | Kiểm tra 2 toán hạng có giá trị khác nhau hay không. Nếu không bằng thì điều kiện là `true`. | `(A != B)` là `true`. |
| `>`     | Kiểm tra nếu toán hạng bên trái có giá trị lớn hơn toán hạng bên phải hay không. Nếu lớn hơn thì điều kiện là `true`. | `(A > B)` là `false`. |
| `<`     | Kiểm tra nếu toán hạng bên trái nhỏ hơn toán hạng bên phải hay không. Nếu nhỏ hơn thì là `true`. | `(A < B)` là `true`. |
| `>=`    | Kiểm tra nếu toán hạng bên trái có giá trị lớn hơn hoặc bằng giá trị của toán hạng bên phải hay không. Nếu đúng là `true`. | `(A >= B)` là `false`. |
| `<=`    | Kiểm tra nếu toán hạng bên trái có giá trị nhỏ hơn hoặc bằng toán hạng bên phải hay không. Nếu đúng là `true`. | `(A <= B)` là `true`. |

---

#### 1.2 Toán tử logic

Bảng dưới đây chỉ rõ tất cả các toán tử logic được hỗ trợ bởi ngôn ngữ C++. Giả sử biến `A` có giá trị 1 và biến `B` có giá trị 0:

| Toán tử | Miêu tả                                                                 | Ví dụ                |
|---------|-------------------------------------------------------------------------|----------------------|
| `&&`    | Được gọi là toán tử logic AND (và). Nếu cả hai toán tử đều có giá trị khác `0` thì điều kiện trở nên `true`. | `(A && B)` là `false`. |
| `\|\|`    | Được gọi là toán tử logic OR (hoặc). Nếu một trong hai toán tử khác `0`, thì điều kiện là `true`. | `(A \|\| B)` là `true`. |
| `!`     | Được gọi là toán tử NOT (phủ định). Sử dụng để đảo ngược lại trạng thái logic của toán hạng đó. Nếu điều kiện toán hạng là `true` thì phủ định nó sẽ là `false`. | `!(A && B)` là `true`. |

---

### 2. Cấu trúc câu lệnh rẽ nhánh

#### 2.1 `if ... else`:

- Mệnh đề `if else` trong C++ được sử dụng để kiểm tra xem một biểu thức điều kiện nào đó có đúng hay không. Nếu đúng thì thực hiện các câu lệnh trong khối lệnh `if`. Nếu sai thì thực hiện câu lệnh trong khối lệnh `else` (nếu có).

**Ví dụ**:
```cpp
int x = 10;
if (x % 2 == 0) {
    cout << "x là số chẵn" << endl;
} else {
    cout << "x là số lẻ" << endl;
}
```
- Nếu muốn mở rộng khối lệnh rẽ nhánh, ta có thể thêm điều kiện và câu lệnh bằng cách sử dụng `else if`.


**Ví dụ**:
```cpp
int diem = 85;

if (diem >= 90) {
    cout << "Xếp loại: Xuất sắc" << endl;
} else if (diem >= 75) {
    cout << "Xếp loại: Giỏi" << endl;
} else if (diem >= 50) {
    cout << "Xếp loại: Trung bình" << endl;
} else {
    cout << "Xếp loại: Yếu" << endl;
}
```

---

#### 2.2 Switch Case:

Lệnh `switch case` là một cấu trúc rẽ nhánh hoàn toàn có thể thay thế bằng cấu trúc `if-else`. Tuy nhiên, việc dùng `switch case` sẽ giúp mã nguồn dễ viết, dễ đọc hơn và tối ưu hơn.

**Cú pháp**:
```cpp
switch(expression) {
    case value1:
        // Các câu lệnh;
        break;
    case value2:
        // Các câu lệnh;
        break;
    ...
    default:
        // Các câu lệnh mặc định;
}
```

Trong đó:
- `Expression` là giá trị hằng số và được so sánh với các giá trị của các `case`.
- Nếu có một `case` nào đó khớp giá trị thì thực hiện khối lệnh tương ứng cho đến khi gặp lệnh `break`.
- `Case default` sẽ được thực hiện nếu không có `case` nào khớp với giá trị `Expression`.

### 3. Thư viện `math.h`

1. **`sqrt(x)`**: Trả về căn bậc 2 của `x`.  
   *Ví dụ*:  
   ```cpp
   cout << sqrt(16); // Kết quả: 4
   ```

2. **`abs(x)`**: Trả về giá trị tuyệt đối của số nguyên `x`.  
   *Ví dụ*:  
   ```cpp
   cout << abs(-10); // Kết quả: 10
   ```

3. **`fabs(x)`**: Trả về giá trị tuyệt đối của số thực `x`.  
   *Ví dụ*:  
   ```cpp
   cout << fabs(-10.5); // Kết quả: 10.5
   ```
---

## 4. Luyện tập:

- Kiểm tra tính chẵn lẻ của một số
- Tìm max trong 3 số
- kiểm tra số chính phương để tận dụng được cả 2 kiến thức vừa học.
- Cho ba số a, b, c đọc vào từ bàn phím. Hãy in ra màn hình theo thứ tự tăng dần các số.
- Viết chương trình tính tiền điện với chỉ số mới và chỉ số cũ Được nhập vào từ bàn phím. In ra màn hình chỉ số cũ, chỉ số mới và số tiền phải trả. Biết rằng 100 kWh đầu giá 1000, từ kWh 101 – 150 giá 1200, từ kWh 151 – 200 giá 2000, từ 201 trở lên giá 2500.
  

