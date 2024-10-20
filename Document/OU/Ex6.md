# Bài 6


|[P1](#collection)|[P2](#arraylist)|[P3](#phương-thức-sort)|[P4](#hashtable)|[P5](#sortedlist)|[P6](#stack)|[P7](#queue)|[P8](#generic)|[P9](#list)|[P10](#dictionary)|[P11](#delegate)|[P12](#event)|[P13](#lambda)|[P14](#linq)|
|-|-|-|-|-|-|-|-|-|-|-|-|-|-|


## Collection
- `Collections` trong C# là một nhóm các lớp và giao diện được sử dụng để lưu trữ và quản lý một tập hợp các đối tượng. Các `collection` cung cấp nhiều phương thức để thêm, xóa, tìm kiếm và truy cập các phần tử trong tập hợp. Các `collection` thường được sử dụng thay cho mảng khi bạn cần khả năng linh hoạt hơn trong việc quản lý dữ liệu.

- Một số loại collection phổ biến trong C# bao gồm:

   + `ArrayList`
    + `HashTable`
   +  `List<T>`
    + `Dictionary<TKey, TValue>`
    + `SortedList<TKey, TValue>`

## ArrayList

- `ArrayList` là một collection có khả năng thay đổi kích thước, cho phép bạn thêm và xóa các phần tử mà không cần phải xác định kích thước trước. `ArrayList` có thể chứa các đối tượng của bất kỳ kiểu dữ liệu nào.

```C#
ArrayList arrayList = new ArrayList();
arrayList.Add("Hello");
arrayList.Add(10);
arrayList.Add(3.14);
```
```C#
using System;
using System.Collections;

class Program
{
    static void Main()
    {
        ArrayList arrayList = new ArrayList();
        arrayList.Add("Apple");
        arrayList.Add("Banana");
        arrayList.Add("Cherry");

        Console.WriteLine("ArrayList elements:");
        foreach (var item in arrayList)
        {
            Console.WriteLine(item);
        }

        // Xóa một phần tử
        arrayList.Remove("Banana");

        Console.WriteLine("After removing Banana:");
        foreach (var item in arrayList)
        {
            Console.WriteLine(item);
        }
    }
}
```

## Phương thức Sort

- `Sort` là một phương thức có sẵn trong nhiều collection để sắp xếp các phần tử. Khi sử dụng `Sort` trên `ArrayList`, các phần tử sẽ được sắp xếp theo thứ tự tăng dần.

```C#

using System;
using System.Collections;

class Program
{
    static void Main()
    {
        ArrayList arrayList = new ArrayList() { 5, 2, 8, 1, 3 };

        Console.WriteLine("Before sorting:");
        foreach (var item in arrayList)
        {
            Console.WriteLine(item);
        }

        // Sắp xếp ArrayList
        arrayList.Sort();

        Console.WriteLine("After sorting:");
        foreach (var item in arrayList)
        {
            Console.WriteLine(item);
        }
    }
}
```

## HashTable
- `HashTable` là một `collection` lưu trữ các cặp `key-value` (khóa-giá trị), cho phép truy cập nhanh chóng dựa trên khóa. Mỗi khóa trong `HashTable` là duy nhất và không thể trùng lặp.

```C#

Hashtable hashtable = new Hashtable();
hashtable.Add("key1", "value1");
hashtable.Add("key2", "value2");

```
```C#

using System;
using System.Collections;

class Program
{
    static void Main()
    {
        Hashtable hashtable = new Hashtable();
        hashtable.Add("A", 1);
        hashtable.Add("B", 2);
        hashtable.Add("C", 3);

        Console.WriteLine("Hashtable elements:");
        foreach (DictionaryEntry entry in hashtable)
        {
            Console.WriteLine($"Key: {entry.Key}, Value: {entry.Value}");
        }

        // Truy cập giá trị theo khóa
        Console.WriteLine($"Value for key 'B': {hashtable["B"]}");
    }
}

```
## SortedList

-` SortedList` là một `collection` kết hợp giữa `ArrayList` và `HashTable`. Nó lưu trữ các cặp `key-value`, nhưng các phần tử được sắp xếp theo thứ tự tăng dần của khóa. `SortedList` cho phép bạn truy cập các phần tử thông qua khóa và có hiệu suất tốt trong việc truy cập dữ liệu.

```C#

SortedList sortedList = new SortedList();
sortedList.Add("B", 2);
sortedList.Add("A", 1);
sortedList.Add("C", 3);

```

```C#
using System;
using System.Collections;

class Program
{
    static void Main()
    {
        SortedList sortedList = new SortedList();
        sortedList.Add("C", 3);
        sortedList.Add("A", 1);
        sortedList.Add("B", 2);

        Console.WriteLine("SortedList elements:");
        foreach (DictionaryEntry entry in sortedList)
        {
            Console.WriteLine($"Key: {entry.Key}, Value: {entry.Value}");
        }

        // Truy cập giá trị theo khóa
        Console.WriteLine($"Value for key 'A': {sortedList["A"]}");
    }
}
```



## Stack
- `Stack` là một cấu trúc dữ liệu theo nguyên tắc LIFO (Last In, First Out), tức là phần tử được thêm vào sau cùng sẽ được lấy ra trước tiên. Bạn có thể sử dụng `Stack` để quản lý các đối tượng mà bạn muốn truy cập theo thứ tự ngược lại.

```C#

using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        Stack<int> stack = new Stack<int>();
        
        // Thêm phần tử vào stack
        stack.Push(1);
        stack.Push(2);
        stack.Push(3);

        Console.WriteLine("Stack elements:");
        foreach (var item in stack)
        {
            Console.WriteLine(item);
        }

        // Lấy phần tử ra khỏi stack
        Console.WriteLine($"Pop: {stack.Pop()}"); // Lấy ra 3
        Console.WriteLine($"Peek: {stack.Peek()}"); // Xem phần tử trên cùng (2)
    }
}
```



## Queue

- `Queue` là một cấu trúc dữ liệu theo nguyên tắc FIFO (First In, First Out), tức là phần tử được thêm vào đầu tiên sẽ được lấy ra đầu tiên. `Queue` thường được sử dụng trong các ứng dụng như xử lý sự kiện hoặc các tác vụ cần quản lý theo thứ tự.

```C#

using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        Queue<string> queue = new Queue<string>();
        
        // Thêm phần tử vào queue
        queue.Enqueue("Apple");
        queue.Enqueue("Banana");
        queue.Enqueue("Cherry");

        Console.WriteLine("Queue elements:");
        foreach (var item in queue)
        {
            Console.WriteLine(item);
        }

        // Lấy phần tử ra khỏi queue
        Console.WriteLine($"Dequeue: {queue.Dequeue()}"); // Lấy ra Apple
        Console.WriteLine($"Peek: {queue.Peek()}"); // Xem phần tử đầu tiên (Banana)
    }
}
```

## Generic

- `Generic` cho phép bạn định nghĩa các lớp, phương thức, và cấu trúc mà không cần chỉ định kiểu dữ liệu cụ thể. Điều này giúp tăng tính linh hoạt và tái sử dụng mã.

```C#

using System;

class GenericClass<T>
{
    public T GenericMethod(T param)
    {
        return param;
    }
}

class Program
{
    static void Main()
    {
        GenericClass<int> intObj = new GenericClass<int>();
        Console.WriteLine(intObj.GenericMethod(5)); // 5

        GenericClass<string> stringObj = new GenericClass<string>();
        Console.WriteLine(stringObj.GenericMethod("Hello")); // Hello
    }
}
```

## List

- `List<T>` là một `collection` có khả năng thay đổi kích thước, tương tự như `ArrayList`, nhưng chỉ có thể chứa các đối tượng cùng kiểu `T`. Điều này giúp bảo vệ dữ liệu và cải thiện hiệu suất.

```C#
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        List<string> list = new List<string> { "Apple", "Banana", "Cherry" };

        Console.WriteLine("List elements:");
        foreach (var item in list)
        {
            Console.WriteLine(item);
        }

        // Thêm phần tử
        list.Add("Date");

        // Xóa phần tử
        list.Remove("Banana");

        Console.WriteLine("After modification:");
        foreach (var item in list)
        {
            Console.WriteLine(item);
        }
    }
}
```

## Dictionary

- `Dictionary<TKey, TValue>` là một `collection` lưu trữ các cặp `key-value`, cho phép truy cập nhanh chóng theo khóa. Các khóa là duy nhất và không thể trùng lặp.

```C#
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        Dictionary<string, int> dictionary = new Dictionary<string, int>
        {
            { "Apple", 1 },
            { "Banana", 2 },
            { "Cherry", 3 }
        };

        Console.WriteLine("Dictionary elements:");
        foreach (var kvp in dictionary)
        {
            Console.WriteLine($"Key: {kvp.Key}, Value: {kvp.Value}");
        }

        // Truy cập giá trị theo khóa
        Console.WriteLine($"Value for key 'Banana': {dictionary["Banana"]}");
    }
}
```

## Delegate

- `Delegate` là một kiểu dữ liệu cho phép bạn lưu trữ tham chiếu đến các phương thức. Bạn có thể sử dụng `delegate` để gọi phương thức một cách gián tiếp, làm cho việc xử lý sự kiện trở nên dễ dàng hơn.

```C#
using System;

delegate void DisplayMessage(string message);

class Program
{
    static void Main()
    {
        DisplayMessage msg = ShowMessage;
        msg("Hello, World!");
    }

    static void ShowMessage(string message)
    {
        Console.WriteLine(message);
    }
}
```

## Event

- `Sự kiện (Event)` trong C# được sử dụng để xử lý thông báo khi một hành động xảy ra. Sự kiện thường kết hợp với `delegate` để cho phép một lớp thông báo cho các lớp khác về các hành động cụ thể.

```C#

using System;

class Publisher
{
    public event Action<string> Notify;

    public void RaiseEvent(string message)
    {
        Notify?.Invoke(message);
    }
}

class Subscriber
{
    public void Subscribe(Publisher publisher)
    {
        publisher.Notify += OnNotify;
    }

    private void OnNotify(string message)
    {
        Console.WriteLine($"Received message: {message}");
    }
}

class Program
{
    static void Main()
    {
        Publisher publisher = new Publisher();
        Subscriber subscriber = new Subscriber();

        subscriber.Subscribe(publisher);
        publisher.RaiseEvent("Hello, Event!");
    }
}
```

## Lambda

- `Lambda expressions` là một cách ngắn gọn để định nghĩa các phương thức ẩn danh. Chúng thường được sử dụng với `delegate` và các phương thức `LINQ`.

```C#

using System;

class Program
{
    static void Main()
    {
        Func<int, int> square = x => x * x;
        Console.WriteLine($"Square of 5: {square(5)}");
    }
}

```
## Linq

- `LINQ` (Language Integrated Query) cho phép bạn sử dụng cú pháp truy vấn trực tiếp trong C#. Nó hỗ trợ việc truy xuất dữ liệu từ các nguồn khác nhau như mảng, danh sách, cơ sở dữ liệu, v.v.

```C#

using System;
using System.Collections.Generic;
using System.Linq;

class Program
{
    static void Main()
    {
        List<int> numbers = new List<int> { 1, 2, 3, 4, 5, 6 };

        // Sử dụng LINQ để lọc các số chẵn
        var evenNumbers = from n in numbers
                          where n % 2 == 0
                          select n;

        Console.WriteLine("Even numbers:");
        foreach (var number in evenNumbers)
        {
            Console.WriteLine(number);
        }
    }
}
```