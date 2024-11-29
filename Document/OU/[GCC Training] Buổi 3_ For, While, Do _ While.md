# BUỔI 3: FOR, WHILE, DO _ WHILE
## MỤC LỤC
  - [1. Vòng lặp là gì?](#1-vòng-lặp-là-gì)
  - [2. Các loại vòng lặp trong C](#2-các-loại-vòng-lặp-trong-c)
    - [a) Vòng lặp While](#a-vòng-lặp-while)
    - [b) Vòng lặp For](#b-vòng-lặp-for)
    - [c) Vòng lặp Do-While](#c-vòng-lặp-do-while)
  - [3. Điều khiển trong các vòng lặp (`break`, `continue`)](#3-điều-khiển-trong-các-vòng-lặp-break-continue)
    - [a) Lệnh Break](#a-lệnh-break)
    - [b) Lệnh Continue](#b-lệnh-continue)
  - [4. Luyện tập](#4-luyện-tập)
---
## I. MỤC TIÊU KIẾN THỨC
- Nắm vững được 3 kiểu lặp (chú trọng về vòng for).
- Có thể vẽ được các hình cơ bản (Hình tam giác).
- Giới thiệu một chút về cách vẽ hình dùng thêm `if` để chương trình sạch đẹp hơn.

## II. YÊU CẦU CHUẨN BỊ
- Ôn tập lại kiến thức cũ về `break`, `continue`.
- Tìm hiểu trước kiến thức về vòng lặp: `for`, `while`, `do while`.

## III. CHI TIẾT BÀI GIẢNG

### 1. Vòng lặp là gì?
**Khái niệm**:
- Một câu lệnh vòng lặp cho phép chúng ta thực hiện một câu lệnh hoặc một khối câu lệnh nhiều lần cho đến khi gặp điều kiện dừng của vòng lặp.
- Ví dụ: 

```cpp
// In ra "tôi yêu ptit" 10 lần
for (int i = 0; i < 10; i++) {
    std::cout << "Tôi yêu PTIT" << std::endl;
}
```

---

### 2. Các loại vòng lặp trong C:

#### a) Vòng lặp While
- **Khái niệm**: Vòng lặp `while` thường được sử dụng để lặp đi lặp lại một khối lệnh không biết trước số lần lặp.

```cpp
while (điều_kiện) {
    // Các câu lệnh
}
```

- **Bài tập**:
  1. In ra các số lẻ (<10) dùng `while`.
  2. Viết chương trình lặp n lần nhập giá trị k nguyên dương và hiển thị giá trị đảo của số vừa lặp.

---

#### b) Vòng lặp For
- **Khái niệm**: Vòng lặp `for` là một cấu trúc điều khiển lặp lại cho phép bạn viết một cách hiệu quả một vòng lặp mà cần phải thực hiện một số cụ thể.

```cpp
for (khởi_tạo; điều_kiện; cập_nhật) {
    // Các câu lệnh
}
```

- **Bài tập**:
  1. In ra 3 lần "Tôi yêu PTIT".
  2. Tính tổng từ 0 đến n.

```cpp
for (int i = 0; i < 3; i++) {
    std::cout << "Tôi yêu PTIT" << std::endl;
}
```

---

#### c) Vòng lặp Do-While
- **Khái niệm**: Không giống như vòng lặp `for` và `while`, vòng lặp `do ... while` kiểm tra điều kiện ở cuối vòng lặp. Do đó, nó luôn được thực hiện ít nhất một lần.

```cpp
do {
    // Các câu lệnh
} while (điều_kiện);
```

- **Bài tập**: In ra 3 lần "Tôi yêu PTIT lần i" với `i` là số lần lặp.

---

### 3. Điều khiển trong các vòng lặp (`break`, `continue`)

#### a) Lệnh Break
- Lệnh `break` sẽ làm vòng lặp lập tức kết thúc và không chạy khối lệnh phía sau.

```cpp
for (int i = 0; i < 1000; i++) {
    if (i == 500) {
        break;
    }
}
```

#### b) Lệnh Continue
- Lệnh `continue` lập tức dừng khối lệnh đang chạy lại, cập nhật điều kiện chạy và tiếp tục vòng lặp với biến điều kiện tiếp theo.

### Vòng lặp vô hạn
```cpp
// Vòng lặp vô hạn với for
for (; ;) {
    // code
}

// Vòng lặp vô hạn với while
while (true) {
    // code
}

// Vòng lặp vô hạn với do-while
do {
    // code
} while (true);
```
- Trường hợp vận dụng: yêu cầu nhập dữ liệu đầu vào đến hết file.
```cpp
int main() {
    int input;
    while (cin >> input) { // Đọc cho đến khi EOF
        cout << input << endl;
    }
    return 0;
}
```

---

### 4. Luyện tập
- **Bài tập 1**: Nhập số nguyên dương `n`. Vẽ các hình dưới định dạng sau:
  
Dưới đây là nội dung sửa lại đầy đủ, với các hình tam giác được đảm bảo cân đối theo yêu cầu:

---
### Bài 1: Nhập số nguyên dương `n`. Vẽ các hình dưới định dạng sau:
#### a)
n = 5
```
*****
*****
*****
*****
*****
```
#### b)
n = 5
```
*****    
*   *     
*   *      
*   *     
*****       
```
#### c)
n = 5
```
*****    
** **     
* * *      
** **     
***** 
```
#### d)
n = 5
```
*****    
**  *     
* * *      
*  **     
*****
```
#### e)
n = 5
```
*****    
*  **     
* * *      
**  *     
*****
```

### Bài 2: Nhập số nguyên dương `n`. Vẽ các hình dưới định dạng sau:

#### a)
n = 5
```
*
**
***
****
*****
```
#### b)
n = 5
```
*****    
****     
***      
**       
*        
```
#### c)
n = 5
```
*********
 *******
  *****
   ***
    *
```
#### d)
n = 5
```
    *
   ***
  *****
 *******
*********
```
### Bài 3: Nhập số nguyên dương `n`. Vẽ các hình dưới định dạng sau:

#### a)
n = 5
```
*
**
* *
*  *
*****
```
#### b)
n = 5
```
*****    
*  *     
* *      
**       
*        
```
#### c)
n = 5
```
*********
 *     *
  *   *
   * *
    *
```
#### d)
n = 5
```
    *
   * *
  *   *
 *     *
*********
```
### Bài 4: Nhập số nguyên dương `n`. Vẽ các hình dưới định dạng sau:

n = 5
```
    * *    
   ** **   
  * * * *    
 *  * *  *   
***** *****
```
---
## Bài tập
CB:
1) Liệt kê các số  chẵn, lẻ, nguyên tố, chính phương bé hơn 1000 bằng for/ while (có thể in ngược)
2) Tính tổng bằng for/while 

NC:
1) Tìm các số Fibonacci bé hơn 100
2) Vẽ bảng cửu chương
3) Vẽ tam giác cân, đều, vẽ hình vuông, hình chữ nhật
