# Bài 2

|[P1](#hằng-số)|[P2](#ép-kiểu)|[P3](#parse-và-tryparse)|[P4](#convert)|[P5](#câu-lệnh-rẽ-nhánh-if-else)|[P6](#switch-case)|[P7](#kiểu-dữ-liệu-object)|[P8](#boxing-và-unboxing)|
|-|-|-|-|-|-|-|-|

## Hằng số

- Hằng số là các giá trị không thể thay đổi trong suốt quá trình thực thi chương trình. 
- Trong C#, hằng số được khai báo với từ khóa `const`.

``` C#
const double PI = 3.14159;
const int MAX_VALUE = 100;
```

## Ép Kiểu

- Ép kiểu (type casting) trong C# là việc chuyển đổi một giá trị từ kiểu dữ liệu này sang kiểu dữ liệu khác. C# hỗ trợ hai loại ép kiểu chính: ép kiểu ngầm định và ép kiểu tường minh.

     + Ép kiểu ngầm định: Xảy ra khi không có nguy cơ mất dữ liệu (chuyển từ kiểu nhỏ sang kiểu lớn).
    + Ép kiểu tường minh: Yêu cầu lập trình viên chỉ định rõ (chuyển từ kiểu lớn sang kiểu nhỏ).


Ép kiểu ngầm định
```C#
int a = 10;
double b = a; // int chuyển thành double
``` 


Ép kiểu tường minh
```C#
double c = 9.8;
int d = (int)c; // double chuyển thành int (mất phần thập phân)

```
## Parse và TryParse

- `Parse` và `TryParse` dùng để chuyển đổi chuỗi (string) thành các kiểu dữ liệu số.

    + `Parse`: Chuyển đổi chuỗi sang kiểu dữ liệu khác, nhưng nếu chuỗi không hợp lệ, nó sẽ gây ra ngoại lệ (Exception).
    + `TryParse`: Tương tự Parse, nhưng nó không gây ngoại lệ mà trả về true hoặc false để kiểm tra thành công.

Parse

```C#
string numberString = "123";
int number = int.Parse(numberString); // number = 123
```

TryParse

```C#
string invalidString = "abc";
bool success = int.TryParse(invalidString, out int result); // success = false, result = 0
```

## Convert
- Lớp `Convert` cung cấp các phương thức để chuyển đổi các kiểu dữ liệu khác nhau.

```C#
string numberString = "456";
int number = Convert.ToInt32(numberString); // number = 456
double decimalNumber = 12.34;
int roundedNumber = Convert.ToInt32(decimalNumber); // roundedNumber = 12
```

- `Convert` cũng hỗ trợ chuyển đổi từ kiểu số thành chuỗi và ngược lại, cũng như giữa các kiểu dữ liệu khác.

## Câu lệnh rẽ nhánh If-Else

- Câu lệnh `if-else` cho phép bạn thực thi các đoạn mã khác nhau dựa trên điều kiện.

```C#
int age = 20;

if (age >= 18)
{
    Console.WriteLine("Bạn là người trưởng thành.");
}
else
{
    Console.WriteLine("Bạn chưa đủ tuổi.");
}
```

## Switch-Case

- `Switch-case` là một câu lệnh điều kiện khác thay thế cho if-else khi bạn cần kiểm tra nhiều giá trị của một biến.

```C#
int day = 3;

switch (day)
{
    case 1:
        Console.WriteLine("Thứ Hai");
        break;
    case 2:
        Console.WriteLine("Thứ Ba");
        break;
    case 3:
        Console.WriteLine("Thứ Tư");
        break;
    default:
        Console.WriteLine("Không hợp lệ");
        break;
}
```

- `Lưu ý`: Mỗi case cần có break để thoát khỏi câu lệnh switch khi một điều kiện thỏa mãn.

## Kiểu dữ liệu Object

- `object` là kiểu dữ liệu gốc của tất cả các kiểu dữ liệu trong C#. Mọi kiểu dữ liệu đều có thể được gán cho biến kiểu `object`.

```C#
object myObject;
myObject = 100;     // int
myObject = "Hello"; // string
myObject = 12.34;   // double
```

- Bạn có thể lưu bất kỳ kiểu dữ liệu nào vào object, nhưng khi truy xuất giá trị, bạn cần thực hiện ép kiểu tường minh về kiểu dữ liệu cụ thể.

## Boxing và Unboxing

- `Boxing`: Chuyển đổi một giá trị kiểu dữ liệu giá trị (value type) thành object.
- `Unboxing`: Chuyển đổi ngược từ object về kiểu giá trị ban đầu.

Boxing
```C#
int number = 123;
object boxed = number; // Boxing: Chuyển int thành object
```
Unboxing

```C#
object obj = 123;
int unboxed = (int)obj; // Unboxing: Chuyển object về int
```
