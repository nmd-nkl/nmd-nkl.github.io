### **BUỔI 8: STRUCT**

---
## Mục lục

- [**Khái niệm**](#khái-niệm)
- [**Khai báo**](#khai-báo)
  - [**Khai Báo Cơ Bản**](#khai-báo-cơ-bản)
  - [**Khai Báo & Khởi tạo biến cùng lúc**](#khai-báo--khởi-tạo-biến-cùng-lúc)
- [**Truy cập các thuộc tính của struct**](#truy-cập-các-thuộc-tính-của-struct)
- [**Nhập xuất với struct**](#nhập-xuất-với-struct)
- [**Mảng Struct**](#mảng-struct)
- [**Bài toán**](#bài-toán)
---
# **KHÁI NIỆM**
Struct hay cấu trúc là một kiểu dữ liệu mà tự bạn định nghĩa ra bằng cách gộp nhiều kiểu dữ liệu có sẵn.
# **KHAI BÁO**
### **Khai Báo Cơ Bản:**           
Gán giá trị cho một biến cấu trúc
```cpp
int main() {
    // Ngoài ra, cũng có thể khai báo
    // biến cấu trúc ở bất kỳ đâu trong chương trình
    sv a, b, c;
    return 0;
}
```
```cpp
int main() {
    sv a;
    a.age = 18;
    a.ten = "Hai";
    a.ads = "HN";
    return 0;
}
```

### **Khai Báo & Khởi tạo biến cùng lúc:**
```cpp
/* để tạo các biến struct đồng thời truyền vào kiểu dữ liệu
ta có thể sử dụng các hàm khởi tạo có tham số:
<Tên_struct>(<Danh_sách_tham_số_truyền_vào>)
{
    <Khởi_tạo_các_trường_bằng_tham_số_tương_ứng>;
}
*/

struct sv{
    int age;
    string ten, ads;

    sv(){} /* khi sử dụng hàm khởi tạo có tham số nên
    khai báo 1 hàm khởi tạo mặc định riêng */

    sv(int Age, string Ten, string Ads){
        age = Age;
        ten = Ten;
        ads = Ads;
    }
};

int main(){
    sv a; // sử dụng hàm khởi tạo mặc định (riêng)
    sv b = {18, "Hai", "HN"}; // sử dụng hàm khởi tạo có tham số
}
```
### **Truy cập các thuộc tính của struct:**     
```cpp
int main() {
// {Tên_biến_cấu_trúc}.{Tên_Thuộc_Tính}
int main(){
    sv a;
    cin >> a.age;
    cout << a.age;
    return 0;
}
```
### **Nhập xuất với struct**
```cpp
Struct lồng nhau

struct TacGia{
    char hoten[100];
    char quoctich[100];
}

struct Sach{
    TacGia tg;
    char tensach[100];
    int giaban;
}
```
```cpp
struct sv{
    int age;
    string ten;
    string ads;
};
void nhap(){
    cin >> age >> ten >> ads;
}

void in(){
    cout << age << " " << ten << " " << ads << endl;
}
};

// hoặc có thể khai báo bên ngoài struct
void Nhap(sv &a){
      cin >> a.age >> a.ten >> a.ads;
}
```
### **Mảng Struct:**

```cpp
struct sv {
    int age;
    string ten;
    string ads;
};

// Hàm nhập dữ liệu cho mảng sv
void nhap(sv a[], int n) {
    for (int i = 0; i < n; i++) {
        cin >> a[i].age >> a[i].ten >> a[i].ads;
    }
}

// Hàm in dữ liệu của mảng sv
void in(sv a[], int n) {
    for (int i = 0; i < n; i++) {
        cout << a[i].age << " " << a[i].ten << " " << a[i].ads << endl;
    }
}

// Hàm hoán đổi hai đối tượng sv
void swap(sv &a, sv &b) {
    sv temp = a;
    a = b;
    b = temp;
}

// Hàm sắp xếp mảng sv theo tuổi tăng dần
void Sort(sv a[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = i + 1; j < n; j++) {
            if (a[i].age > a[j].age) {
                swap(a[i], a[j]);
            }
        }
    }
}

int main() {
    sv a[50];
    int n;
    cin >> n;
    nhap(a, n);
    Sort(a, n);
    in(a, n);
    return 0;
}

```

# **Bài toán**:  

- Cho một mảng gồm n phần tử. Nhập vào n số nguyên a[i], là các phần tử của mảng. Yêu cầu của bài toán là đếm số lần xuất hiện của mỗi phần tử trong mảng và in ra các phần tử cùng với số lần xuất hiện của chúng. Kết quả cần được sắp xếp theo thứ tự tăng dần của tần suất xuất hiện. 
- Trong trường hợp hai phần tử có cùng tần suất xuất hiện, phần tử có giá trị lớn hơn sẽ được xếp trước.

    - Giới hạn: a[i] thuộc [0, 10^7]

        | Input                 | Output                 |
        |-----------------------|------------------------|
        | 13                    | 2 xuat hien 2 lan     |
        | 5 3 5 2 8 3 5 2 8 8 5 3 5 | 8 xuat hien 3 lan     |
        |                       | 3 xuat hien 3 lan     |
        |                       | 5 xuat hien 5 lan     |


```cpp
#include <bits/stdc++.h>
using namespace std;
struct Ghep {
    int val, freq;
};
bool cmp(Ghep a, Ghep b) {
    if(a.freq != b.freq) return a.freq < b.freq; // tăng dần
    return a.val > b.val; //lớn hơn xếp trước
}
int main() {
    // Nhập xuất
    int n; cin >> n;
    Ghep A[n];
    for(auto &a: A) cin >> a.val;
    //Mảng tần số
    int tanSo[(int)1e5] = {0};
    // đếm số lần xuất hiện
    for(auto it: A) tanSo[it.val]++;
    //Gán tần số cho kiểu dữ liệu Struct Ghep
    for(int i = 0; i < n; i++)
        A[i].freq = tanSo[A[i].val];

    //Sort doi cho truc tiep
    for(int i = 0; i < n-1; i++) {
        for(int j = i + 1; j < n; j++) {
            if(!cmp(A[i], A[j])) //nếu sai sẽ swap
                swap(A[i], A[j]);
        }
    }

    for(int i = 0; i < n; i++) {
        if(tanSo[A[i].val] !=0) {
            cout << A[i].val << " xuat hien " << A[i].freq << " lan\n"; 
            tanSo[A[i].val] = 0; //NOTE
        }
    }

    return 0;
}
```