# CS112
# Chủ đề 2 - Phân tích độ phức tạp thời gian của đệ quy
- Hanoi Tower : chơi game tìm ra đường đi tối ưu và lời giải.

> Đặt câu hỏi để mọi người cùng ghi ý ra trong vòng 5 phút, sau đó nhờ mọi người tìm hiểu sau đó tổng hợp lại.

**Đệ quy là gì? (3 phút)**
- Là một kỹ thuật trong lập trình và toán học, trong đó một hàm số được định nghĩa,**tính toán thông qua chính hàm đó.** Nói cách khác, đó chính là ta **chia bài toán lớn thành các bài toán nhỏ** cho tới khi chạm vào bài toán cơ sở rồi tính toán ngược ra.
- Có 2 khái niệm quan trọng nhất cần được nhắc tới là **công thức truy hồi** (recurrence relation), **trường hợp cơ sở** (base-case).

**So sánh: đệ quy vs vòng lặp**
> Chỉ ra 3 đặc điểm khác nhất
- Khi nào đệ quy tiện lợi, khi nào nên tránh.
- Có phải đệ quy lúc nào cũng kém hiệu quả hơn lặp?
- Có nên thay mọi thuật toán đệ quy thành lặp?

> Tại sao nhiều thuật toán lại viết bằng đệ quy? 
- Tương đồng với các bài toán (Như tổng N số, giai thừa, dãy số fibonacci)
- Dễ mô tả(bằng cây phân cấp), dễ thực hiện và ngắn gọn.
- Tạo tư duy chia nhỏ bài toán để xử lý

# Quy trình chung để phân tích thời gian của đệ quy

- Phân tích N giai thừa, cho ví dụ minh hoạ.

> Cho các bước theo từng cell, rồi các bạn sắp xếp (nối các bước) và suy ra quy trình.

Quy trình chung để phân tích thời gian của đệ quy:
- Xác định tham số kích thước input
- Xác định phép toán cơ bản của thuật toán
- Với các input có cùng độ lớn thì số lần thực hiện phép toán có thay đổi dựa theo input không. Nếu có, cần phân tích riêng ba trường hợp: tốt nhất, trung bình và xấu nhất.
- Thiết lập công thức truy hồi và trường hợp cơ sở cho hàm $M(i)$,  với $M(i)$ là độ phức tạp thời gian để tính toán ra hàm $F(i)$.
- Giải phương trình truy hồi 



# Phân tích đệ quy (Cách giải hệ thức truy hồi)
**Câu hỏi:** 
Brainstorm những phương pháp để giải công thức truy hồi.
- Phương pháp đó có thể giải những công thức dạng như thế nào ? 
- Giải bằng cách nào? 

## Phương pháp thế (Substitution Method) (tiến + lùi)

## Phương pháp cây đệ qui (Recurrence Tree Method) 

## Phương pháp Master Theorem
**Dạng tổng quát**: $T(n) = aT(\frac{n}{b}) + f(n)$
> Trong đó:
> n là kích thước của bài toán
> a là số lượng bài toán con
> $\frac{n}{b}$ là kích thước mỗi bài toán con
> f(n) là chi phí để chia bài toán và gộp bài toán

Để sử dụng phương pháp, chỉ cần so sánh $f(n)$ với $n ^{log_b{a}}$.
- Trường hợp 1: Nếu $f(n)$ nhỏ hơn $n^{\log_b{a}}$ một cách đáng kể thì $T(n) = O(n^{\log_b{a}})$.
- Trường hợp 2: Nếu $f(n)$ cùng bậc tăng trưởng với $n^{\log_b{a}}$ thì $T(n) = O(n^{\log_b{a}}\log{n})$
- Trường hợp 3: Nếu $f(n)$ lớn hơn $n^{\log_b{a}}$ một cách đáng kể thì $T(n) = O(f(n))$

## Phương pháp hệ thức truy hồi bậc hai với hệ số hằng  

### 1. Dạng tổng quát
Hệ thức có dạng:

\[
aT(n) + bT(n-1) + cT(n-2) = f(n)
\]

- Nếu \(f(n) = 0\) → gọi là **thuần nhất**.  
- Nếu \(f(n) \neq 0\) → gọi là **phi đồng chất**.  

Mục tiêu: tìm **công thức dạng đóng** cho \(T(n)\).  

### 2. Cách giải hệ thuần nhất (\(f(n)=0\))

#### **Bước 1:** Lập phương trình đặc trưng  
\[
ar^2 + br + c = 0
\]

#### **Bước 2:** Giải phương trình để tìm nghiệm \(r_1, r_2\).  

#### **Bước 3:** Viết nghiệm tổng quát tùy theo trường hợp  

- **Trường hợp 1:** Hai nghiệm thực phân biệt \(r_1, r_2\)  
  \[
  T(n) = \alpha r_1^n + \beta r_2^n
  \]

- **Trường hợp 2:** Nghiệm kép \(r_1 = r_2 = r\)  
  \[
  T(n) = (\alpha + \beta n) r^n
  \]

- **Trường hợp 3:** Nghiệm phức liên hợp \(r_{1,2} = u \pm iv\)  
  Gọi:  
  \[
  \gamma = \sqrt{u^2+v^2}, \quad \theta = \arctan\left(\tfrac{v}{u}\right)
  \]  
  Khi đó:  
  \[
  T(n) = \gamma^n \left[ \alpha \cos(n\theta) + \beta \sin(n\theta) \right]
  \]

#### **Bước 4:** Thay điều kiện đầu (ví dụ \(T(0), T(1)\)) để tìm hằng số \(\alpha, \beta\).  

---

**Các bài toán kinh điển**
- Fibonacci O(n) - thế
- Hanoi Tower O($2^n$) - cây
- Segment Tree O(nlogn) - master theorem


#**Bài tập về nhà**:

**BÀI 1**:
Cho một ma trận vô hạn ô vuông màu trắng. Bắt đầu với một ô vuông bị tô đen ở giữa ma trận, với mỗi một đơn vị thời gian nó sẽ tự loan màu sang các ô khác theo 4 hướng Đông-Tây-Nam-Bắc, hỏi sau $n$ đơn vị thời gian thì có bao nhiêu ô bị loan màu. 

Hãy giải bài toán bằng thuật toán đệ quy.

Tìm ra công thức truy hồi thời gian và giải công thức truy hồi đó để tìm được độ phức tạp thuật toán.

**BÀI 2**: 
Một đầu bếp cần nấu n chiếc hamburger trên một chiếc chảo nhỏ có sức chứa tối đa 2 chiếc cùng lúc. Mỗi chiếc hamburger cần được nấu cả hai mặt, và thời gian để nấu một mặt (cho 1 hoặc 2 chiếc) là 1 phút.

Một thuật toán đệ quy được đề xuất như sau:
Trường hợp cơ sở (n ≤ 2): Nếu có 1 hoặc 2 chiếc, nấu tuần tự 2 mặt của chúng.
Đệ quy (n > 2): Chọn 2 chiếc bất kỳ, nấu cả 2 mặt của chúng. Sau đó, giải quyết bài toán còn lại cho n - 2 chiếc.

Yêu cầu:
- a. Xây dựng và giải hệ thức truy hồi:
Thiết lập và giải hệ thức truy hồi T(n) để xác định tổng thời gian nấu n chiếc hamburger theo thuật toán đã cho.
- b. Phân tích tính tối ưu của thuật toán:
Giải thích tại sao thuật toán đệ quy trên không phải là chiến lược tối ưu để giảm thiểu tổng thời gian nấu.
- c. Đề xuất thuật toán tối ưu:
Xây dựng một thuật toán khác để hoàn thành công việc trong thời gian ngắn nhất có thể và chứng minh tính hiệu quả của nó.

**BÀI 3**: Cho đoạn code
```python=
def countPairs(n):
    if n <= 1:
        return 1
    total = 0
    for i in range(n):
        total += countPairs(i) * countPairs(n - 1 - i)
    return total
```
Hãy phân tích độ phức tap thời gian thuật toán theo quy trình chung. 

Link drive các file liên quan khác: https://drive.google.com/drive/folders/1IuP9MwowUDMST8vLPuAkoKHCV9SJwEW_?usp=sharing

