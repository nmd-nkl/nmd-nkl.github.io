# Bài 1


|[P1](#sử-dụng-git)|[P2](#tìm-hiểu-về-biến)|[P3](#tìm-hiểu-về-kiểu-dữ-liệu)|[P4](#stack-và-heap)|[P5](#một-số-kiểu-dữ---liệu-dựng-sẵn)|[P6](#tìm-hiểu-về-toán-tử---toán-tử-toán-học)|[P7](#toán-tử-logic)|[P8](#toán-tử-quan-hệ)|[P9](#thứ-tự-ưu-tiên-của-toán-tử)|
| -|-|-|-|-|-|-|-|-|


## Sử dụng Git

 - `git init` Khởi tạo một repository Git mới trong thư mục hiện tại.
 - `git clone <url>` Sao chép một repository từ URL.
 - `git add <file>` Thêm file vào vùng staging để chuẩn bị commit.
- `git commit -m "message"` Commit thay đổi với một thông điệp ngắn.
- ` git push` Đẩy commit từ local repository lên remote repository.
 - `git pull` Lấy và hợp nhất thay đổi từ remote repository về local.
 - `git status` Kiểm tra trạng thái của các file trong repository.
- `git log` Xem lịch sử commit.

## Tìm hiểu về Biến

```C#
        int age = 25;
        string name = "John";
        bool isStudent = true;
```

## Tìm hiểu về kiểu dữ liệu

- Kiểu dữ liệu trong C# xác định loại giá trị mà một biến có thể lưu trữ. C# chia kiểu dữ liệu thành hai loại chính: `Value types` và `Reference types`.
        
    + `Value types`: Lưu trữ giá trị trực tiếp. Ví dụ: int, float, bool, char.
    + `Reference types`: Lưu trữ tham chiếu tới một địa chỉ bộ nhớ. Ví dụ: string, array, class.

## Stack Và Heap
 - Trong C#, bộ nhớ chia thành hai vùng: `Stack` và `Heap`.

     + `Stack`: Lưu trữ các biến kiểu giá trị (value types) và có cơ chế quản lý tự động (LIFO - Last In, First Out).
    + `Stack` có kích thước nhỏ và nhanh.
    + `Heap`: Lưu trữ các biến kiểu tham chiếu (reference types) như đối tượng hoặc chuỗi. Khi một đối tượng được tạo, nó nằm trên heap, và hệ thống sẽ quản lý bộ nhớ thông qua cơ chế garbage collection.

## Một số kiểu dữ - liệu dựng sẵn

- C# cung cấp nhiều kiểu dữ liệu sẵn có. Dưới đây là một số kiểu dữ liệu thường dùng:
        
    + `int`: Số nguyên (32-bit), phạm vi từ -2,147,483,648 đến 2,147,483,647.
    + `float`: Số thực dấu phẩy động (32-bit).
    + `double`: Số thực dấu phẩy động độ chính xác gấp đôi (64-bit).
    + `bool`: Biểu diễn giá trị logic true hoặc false.
     + `char`: Một ký tự Unicode (16-bit).
    + `string`: Chuỗi ký tự Unicode.

## Tìm hiểu về toán tử - Toán tử toán học
        
- Toán tử toán học:
    + `+`: Cộng
    + `-`: Trừ
    + `*`: Nhân
    + `/`: Chia
     + `%`: Lấy phần dư

## Toán tử Logic
        
- Toán tử logic được sử dụng để kết hợp các biểu thức điều kiện.

    + `&&`: Phép và (logical AND), trả về true nếu cả hai điều kiện đều đúng.
    + `||`: Phép hoặc (logical OR), trả về true nếu một trong hai điều kiện đúng.
    + `!`: Phép phủ định (logical NOT), đảo ngược giá trị boolean.

## Toán tử quan hệ
- Các toán tử quan hệ được sử dụng để so sánh hai giá trị:

    + `==`: Bằng
    + `!=`: Không bằng
    + `>`: Lớn hơn
    + `<`: Nhỏ hơn
    + `>=`: Lớn hơn hoặc bằng
    + `<=`: Nhỏ hơn hoặc bằng 

## Thứ tự ưu tiên của toán tử 

- Trong C#, thứ tự ưu tiên của toán tử ảnh hưởng đến cách biểu thức được đánh giá. Toán tử có ưu tiên cao sẽ được thực hiện trước. 
- Thứ tự ưu tiên: 
    + Toán tử số học (*, /, %) có ưu tiên cao hơn toán tử cộng/trừ (+, -). 
    + Toán tử quan hệ (<, <=,>, >=) được thực hiện sau toán tử số học.
     + Toán tử logic (&&, ||) có ưu tiên thấp hơn so với toán tử so sánh.
    + Phép gán (=) có ưu tiên thấp nhất.


