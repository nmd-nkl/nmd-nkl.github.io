# QUY HOẠCH ĐỘNG - DYNAMIC PROGRAMMING (DP)

## Quy hoạch động là gì?
Quy hoạch động là một phương pháp giải bài toán bằng cách chia bài toán đó thành các bài toán con nhỏ hơn.

## Nguyên lý hoạt động của quy hoạch động
- Chia bài toán lớn thành các bài toán con nhỏ hơn.
- Lưu trữ kết quả của các bài toán con.
- Sử dụng lại các kết quả đã lưu.

## Các bước thực hiện quy hoạch động
1.  **Bước 1:** Hiểu được cách mà bài toán lớn được chia thành các bài toán con và việc kết hợp các bài toán con để giải bài toán lớn.
2.  **Bước 2:** Xác định được công thức truy hồi (Đây là bước quan trọng nhất).
3.  **Bước 3:** Đi tính giá trị của các bài toán con lần lượt từ nhỏ đến lớn, đồng thời lưu lại kết quả tính được (thường dùng mảng hoặc ma trận).
4.  **Bước 4:** Sử dụng các kết quả vừa tính được để giải bài toán lớn.

## Điều kiện áp dụng quy hoạch động
- Bài toán lớn ban đầu có thể được chia thành các bài toán con nhỏ hơn.
- Phải có đủ không gian lưu trữ cho kết quả của các bài toán con.
- Việc tính toán giá trị của các bài toán con để giải bài toán lớn phải được thực hiện sau hữu hạn các bước.

## Ưu và nhược điểm của quy hoạch động

### Ưu điểm:
- Giảm thời gian tính toán và tránh các bước tính toán lặp lại không cần thiết. 
- Giải quyết được các bài toán phức tạp mà các thuật toán khác khó và không thể thực hiện được.

### Nhược điểm:
- Tốn bộ nhớ và tốn thời gian trong việc lưu trữ và truy xuất kết quả từ bộ nhớ.
- Phức tạp trong việc triển khai, yêu cầu phải hiểu được rõ bài toán và tìm được công thức truy hồi chính xác.

## Các dạng toán quy hoạch động
Có 2 dạng chính:
- Bài toán tối ưu (tìm giá trị nhỏ nhất hoặc lớn nhất).
- Bài toán tổ hợp (tìm số cách thực hiện của một việc nào đó).

Các loại hình quy hoạch động mà chúng ta đã từng dùng trước đây đó là tính số Fibonacci thứ n và mảng cộng dồn. Chúng đều có các công thức truy hồi và bài toán cơ sở.
- Với việc tính số Fibonacci thứ n, thì công thức của nó là $f_n = f_{n-1} + f_{n-2}$ với $f_0 = 0, f_1 = 1$ và $n \ge 2$.
- Với mảng cộng dồn thì công thức là $sum[i] = sum[i - 1] + a[i]$ với $sum[0] = 0$ và $i \ge 1$.

## Một số bài tập điển hình

### Bài toán cái túi

**Đề bài:**
Một người có cái túi thể tích V (V<1000). Anh ta có N đồ vật cần mang theo (N≤1000), mỗi đồ vật có thể tích là A[i] (A[i]≤100) và giá trị là C[i] (C[i]≤100). Hãy xác định tổng giá trị lớn nhất của các đồ vật mà người đó có thể mang theo, sao cho tổng thể tích không vượt quá V.

**Input:**
Dòng đầu ghi số bộ test T (T<10)
Mỗi bộ test gồm ba dòng.
Dòng đầu ghi 2 số N và V. Dòng tiếp theo ghi N số của mảng A. Sau đó là một dòng ghi N số của mảng C.
Dữ liệu vào luôn đảm bảo không có đồ vật nào có thể tích lớn hơn V.

**Output:**
Với mỗi bộ test, ghi trên một dòng giá trị lớn nhất có thể đạt được.

**Ví dụ:**
| Input                                       | Output |
| :------------------------------------------ | :----- |
| 1                                           | 15     |
| 15 10                                       |        |
| 5 2 1 3 5 2 5 8 9 6 3 1 4 7 8               |        |
| 1 2 3 5 1 2 5 8 7 4 1 2 3 2 1               |        |

**Giải:** [Implementation Cái Túi](https://onlinegdb.com/XeCWWzKLP)

(Tất cả đã được giải thích rõ ràng ở trong code)

### Bài toán xâu con chung dài nhất (Longest Common Substring - LCS)

**Đề bài:**
Cho 2 xâu S1 và S2. Hãy tìm xâu con chung dài nhất của 2 xâu này (các phần tử không nhất thiết phải liên tiếp nhau).

**Input:** Dòng đầu tiên là số lượng bộ test T (T ≤ 20). Mỗi test gồm hai dòng, mô tả xâu S1 và S2, mỗi xâu có độ dài không quá 1000 và chỉ gồm các chữ cái in hoa.

**Output:** Với mỗi test, in ra độ dài dãy con chung dài nhất trên một dòng.

**Ví dụ:**
| Input          | Output |
| :------------- | :----- |
| 2              | 4      |
| AGGTAB         | 0      |
| GXTXAYB        |        |
| AA             |        |
| BB             |        |

**Giải:** [Implementation LCS](https://onlinegdb.com/LgND38d1a)

(Tất cả đã được giải thích rõ ràng ở trong code)

### Bài toán tổ hợp - Con ếch

**Đề bài:**
Một con ếch có thể nhảy 1, 2, 3 bước để có thể lên đến một đỉnh cần đến. Hãy đếm số các cách con ếch có thể nhảy đến đỉnh.

**Input:**
Dòng đầu tiên đưa vào số lượng bộ test T.
Những dòng kế tiếp đưa vào các bộ test.
Mỗi bộ test là số n là số bước con ếch có thể lên được đỉnh. 
T, n thỏa mãn ràng buộc: 1≤T≤100; 1≤n ≤50.

**Output:**
Đưa ra kết quả mỗi test theo từng dòng.

**Ví dụ:**
| Input | Output |
| :---- | :----- |
| 2     | 1      |
| 1     | 13     |
| 5     |        |

**Giải:** [Implementation Con ếch](https://onlinegdb.com/rx_6rXUJw)

(Tất cả đã được giải thích rõ ràng ở trong code)