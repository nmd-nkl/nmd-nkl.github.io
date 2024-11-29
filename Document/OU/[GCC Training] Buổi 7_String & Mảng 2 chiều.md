# **BUỔI 6: STRING & MẢNG 2 CHIỀU**
---
  - [**STRING**](#string)
    - [Cách khai báo](#cách-khai-báo)
    - [Các thao tác cơ bản](#các-thao-tác-cơ-bản)
    - [Các thao tác với hàm](#các-thao-tác-với-hàm)
    - [Luyện tập 1](#luyện-tập-1)
  - [**MẢNG 2 CHIỀU**](#mảng-2-chiều)
    - [Khởi Tạo Mảng 2 Chiều](#khởi-tạo-mảng-2-chiều)
    - [Lưu ý, bổ sung](#lưu-ý-bổ-sung)
    - [Luyện tập 2](#luyện-tập-2)
---
## **STRING**
### **Khái niệm:** 
- Là 1 mảng gồm các ký tự kiểu char được lưu giữ dưới dạng mã ASCII. 
- Dùng để chứa và xử lý văn bản như tên, số điện thoại, email.
### Cách khai báo: 
```cpp
//Khởi tạo
string ten_String;
//Khởi tạo và gán giá trị
string ten = "Thông";
```
### Các thao tác cơ bản
#### **`Nhập xâu`**
```cpp
string s;
//Nhập xâu, không bao gồm dấu cách
cin >> s;
//Nhập xâu, bao gồm cả dấu cách
getline(cin, s);
```
`Note`: Nếu dùng `cin` trước `getline`
```cpp
int t; cin >> t; //Ví dụ: nhập testcase
//LƯU Ý:
scanf("\n"); //xoá dấu '\n' trong buffer
//Or:
cin.ignore(); //ignore 1 lần cin
//rồi mới getline nếu không getline tiếp theo sẽ bị nhập vào '\n'
```
```cpp
//Truy xuất các ký tự của chuỗi: Đếm từ index 0
cout << s[0]; //in ra kí tự đầu tiên

//Ghép các chuỗi vào với nhau
cout << s1 + s2;

//Copy chuỗi này sang chuỗi khác
s1 = s2;
```
|**So sánh 2 chuỗi** (dùng trực tiếp các toán tử so sánh): `==`, `!=`, `>`, `<`, ...|
|-|

### Các thao tác với hàm
```cpp
//Hàm trả về độ dài của string
str.length(); //chỉ riêng cho xâu kí tự
str.size(); //dùng cho nhiều loại khác như vector

//Thêm vào sau hoặc xóa sau của chuỗi 1 ký tự
str.push_back();
str.pop_back();

//Trích xuất 1 phần của chuỗi
str.substr(7, 5); // Trích xuất 5 ký tự từ vị trí 7

// Tìm kiếm
size_t pos = s.find("World");
if (pos != string::npos) {
  cout << "Tim thay 'World' tại: " << pos; //trả về vị trí tìm thấy đầu tiên
} else {
  cout << "khong tim thay";
}
```
**Hàm `str.erase(vị trí, chiều dài)`:** 
```cpp
string s = "Hello, world!";

// Xóa 7 ký tự bắt đầu từ vị trí 7
s.erase(7, 7);
cout << s; // Output: "Hello, "

// Xóa từ vị trí 5 đến hết chuỗi
s.erase(5);
cout << s; // Output: "Hello"
```

**Hàm `str.insert(vị trí, chuỗi con)`:** 
```cpp
string s = "Hello!";

// Chèn một chuỗi con
s.insert(5, ", world");
cout << s << endl; // Output: "Hello, world!"
```

**Hàm `str.replace(vị trí, chiều dài, chuỗi con):** 
```cpp
// Thay thế chuỗi con
string s = "Hello, world!";
s.replace(7, 5, "everyone");
cout << s; // Output: "Hello, everyone!"
```
**Hàm đổi từ string sang số & ngược lại:** 
```cpp
string s = "123";
int n = stoi(s); // n = 123 (int)
//Hoặc stoll: long long
//stof: float
```
```cpp
int n = 123;
string s = to_string(n); // s = "123"

string repeat = string(5, '*'); // repeat = "*****"
```
**Hàm `reverse(s.begin(), s.end())`:** Đảo ngược chuỗi.

```cpp
string s = "abc";
reverse(s.begin(), s.end()); // "cba"
```
### **Luyện tập 1**
#### Bài 1: 
|Kiểm tra xem số đó có phải là số đẹp (thuận nghịch và chỉ toàn chữ số chẵn).|
|-|
#### Bài 2: 
|Kiểm tra xem 1 xâu có phải là xâu Pangram không (xâu có đầy đủ ký tự từ a-z, không phân biệt hoa thường). (không dùng set, mảng đánh dấu, các kiến thức chưa học)|
|-| 

## **MẢNG 2 CHIỀU**
### **Khái niệm mảng 2 chiều:** 
Mảng nhiều chiều trong C++ là một trong các khái niệm cơ bản trong lập trình. Mảng nhiều chiều còn được coi là mảng kiểu hình chữ nhật trong C ++. Nó có thể là hai chiều, ba chiều, hoặc nhiều hơn ba chiều. Dữ liệu được lưu trữ dưới dạng bảng (hàng và cột), còn được coi là một ma trận.

### **Khởi Tạo Mảng 2 Chiều:** 

|**<Kiểu Dữ Liệu> \_TênMảng [số hàng] [số cột]**|
| - |

```cpp
int a[n][m]; //mảng a có n hàng, m cột
```
#### Nhập và xuất: dùng 2 vòng for lồng nhau
```cpp
for(int i = 0; i < n; i++) {
  for(int j = 0; j < m; j++) {
    cin >> a[i][j];
  }
}
```
### **Lưu ý, bổ sung:**
Muốn truyền mảng 2 chiều vào hàm con phải xác định trước số hàng số cột.
### **Luyện tập 2**
#### Bài 1: 
|Cho 1 ma trận n*m in ra ma trận chuyển vị của ma trận đó.|
|-|
#### Bài 2: 
|Tìm tổng lớn nhất của 1 hàng hoặc cột bất kỳ.|
|-|



