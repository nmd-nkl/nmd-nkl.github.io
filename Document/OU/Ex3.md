# Bài 3


|[P1](#từ-khóa-var)|[P2](#từ-khóa-dynamic)|[P3](#vòng-lặp)|[P4](#vòng-lặp-for)|[P5](#vòng-lặp-while)|[P6](#switch-case)|[P7](#vòng-lặp-do-while)|[P8](#tìm-hiểu-về-hàm)|[P9](#biến-toàn-cục-biến-cục-bộ)|[P10](#từ-khóa-ref-và-out)|
|-|-|-|-|-|-|-|-|-|-|

## Từ Khóa Var

- Từ khóa `var` cho phép trình biên dịch suy ra kiểu của biến dựa trên giá trị được gán cho nó. Nó chỉ có thể được sử dụng khi giá trị gán cho biến đã xác định rõ kiểu

```C#
var number = 10;  // Kiểu của number là int
var text = "Hello";  // Kiểu của text là string
```
- `Lưu ý`: Khi sử dụng `var`, kiểu dữ liệu của biến được xác định tại thời điểm biên dịch và không thể thay đổi sau đó.


## Từ khóa Dynamic
- Từ khóa `dynamic` cho phép một biến thay đổi kiểu dữ liệu trong quá trình thực thi (runtime). Không giống `var`, kiểu của `dynamic` không được xác định tại thời điểm biên dịch mà chỉ tại thời gian chạy.

```C#
dynamic data = 10;
Console.WriteLine(data);  // In ra 10 (kiểu int)
data = "Hello";
Console.WriteLine(data);  // In ra Hello (kiểu string)
```

- `Lưu ý`: Sử dụng `dynamic` có thể dẫn đến lỗi chỉ được phát hiện tại thời gian chạy, vì vậy cần thận trọng khi dùng.

## Vòng lặp
- Vòng lặp cho phép thực thi một đoạn mã nhiều lần dựa trên điều kiện nhất định.

## Vòng lặp for
- `Vòng lặp for` thường được sử dụng khi bạn biết trước số lần lặp. Cấu trúc của vòng lặp for bao gồm 3 phần: khởi tạo biến, điều kiện lặp, và thay đổi biến sau mỗi lần lặp.

```C#
for (int i = 0; i < 5; i++)
{
    Console.WriteLine(i);  // In ra 0, 1, 2, 3, 4
}
```

## Vòng lặp while
- `Vòng lặp while` thực hiện một đoạn mã khi điều kiện kiểm tra là true. Nếu điều kiện không thỏa mãn ngay từ đầu, vòng lặp sẽ không thực hiện lần nào.

```C#
int i = 0;
while (i < 5)
{
    Console.WriteLine(i);  // In ra 0, 1, 2, 3, 4
    i++;
}
```
## Vòng lặp do-while

- `Vòng lặp do-while` luôn thực hiện ít nhất một lần, sau đó mới kiểm tra điều kiện. Nếu điều kiện đúng, vòng lặp tiếp tục; nếu sai, vòng lặp kết thúc.

```C#
int i = 0;
do
{
    Console.WriteLine(i);  // In ra 0, 1, 2, 3, 4
    i++;
} while (i < 5);
```
## Tìm hiểu về Hàm
- `Hàm` (hay phương thức) là một khối mã thực hiện một chức năng cụ thể. Hàm có thể nhận các tham số và trả về giá trị (hoặc không).

```C#
int AddNumbers(int a, int b)
{
    return a + b;
}

// Gọi hàm
int result = AddNumbers(5, 10);  // result = 15
```


## Biến toàn cục, biến cục bộ

- `Biến cục bộ`: Chỉ có thể truy cập trong một phạm vi nhất định như trong một hàm, vòng lặp hoặc khối mã.
- `Biến toàn cục`: Là biến khai báo trong phạm vi lớp, có thể được truy cập từ bất kỳ phương thức nào trong lớp.

```C#
class Program
{
    // Biến toàn cục
    static int globalVar = 100;

    static void Main(string[] args)
    {
        int localVar = 10;  // Biến cục bộ
        Console.WriteLine(globalVar);  // Truy cập biến toàn cục
        Console.WriteLine(localVar);   // Truy cập biến cục bộ
    }
}
```
## Từ khóa ref và out

- `ref`: Dùng để truyền tham chiếu đến biến, cho phép hàm thay đổi giá trị của biến đó.
- `out`: Cũng truyền tham chiếu, nhưng biến được yêu cầu phải được gán giá trị bên trong hàm trước khi trả về.

Ref
```C#
void Increase(ref int number)
{
    number += 10;
}

int value = 5;
Increase(ref value);
Console.WriteLine(value);  // In ra 15
```



Out
```C#
void GetValues(out int x, out int y)
{
    x = 5;
    y = 10;
}

int a, b;
GetValues(out a, out b);
Console.WriteLine(a);  // In ra 5
Console.WriteLine(b);  // In ra 10
```

- `Lưu ý`: Sử dụng từ khóa `ref` và `out` giúp truyền giá trị tham chiếu thay vì giá trị, có thể làm việc hiệu quả hơn khi xử lý dữ liệu lớn hoặc cần trả về nhiều giá trị từ hàm.

