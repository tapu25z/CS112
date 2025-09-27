# CS112
# Mở đầu: 
- Hanoi Tower : chơi game tìm ra đường đi tối ưu và lời giải.

> Đặt câu hỏi để mọi người cùng ghi ý ra trong vòng 5 phút, sau đó nhờ mọi người tìm hiểu sau đó tổng hợp lại.

**Đệ quy là gì? (3 phút)**
- Là một kỹ thuật trong lập trình và toán học, trong đó một hàm số được định nghĩa,**tính toán thông qua chính hàm đó.** Nói cách khác, đó chính là ta **chia bài toán lớn thành các bài toán nhỏ** cho tới khi chạm vào bài toán cơ sở rồi tính toán ngược ra.

- Có 2 khái niệm quan trọng nhất cần được nhắc tới là **công thức truy hồi** (recurrence relation), **trường hợp cơ sở** (base-case).

Công thức truy hồi: cách mô tả toán học cho thời gian chạy của thuật toán, viết thời gian chạy của bài toán kích thước n dưới dạng công thức phụ thuộc vào nó nhưng với kích thước nhỏ hơn. Biểu diễn đúng công thức truy hồi là chìa khoá để phân tích độ phức tạp của các thuật toán đệ qui.

Trường hợp cơ sở: là điểm dừng của đệ qui. Nếu không có bài toán chạy đến vô hạn việc phân tích thời gian chạy trở nên vô nghĩa.



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
- Với các input có cùng độ lớn thì số lần thực hiện phép toán có thay đổi dựa theo input không. Nếu có, cần phân tích riêng ba trường hợp: tốt nhất, trung bình và xấu nhất 
> Câu hỏi: Chỉ ra ví dụ khiến độ phức tạp của phép tính thay đổi
- Thiết lập công thức truy hồi và trường hợp cơ sở cho hàm $M(i)$,  với $M(i)$ là độ phức tạp thời gian để tính toán ra hàm $F(i)$.
- Giải phương trình truy hồi 
**(Câu hỏi: nếu không giải được chính xác hàm M(n) thì sao -> tìm bậc tăng trưởng của lời giải cho bài toán)**



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

**Dạng tổng quát**:  
$$ax(n) + bx(n-1) + cx(n-2) = f(n)$$  

**Mục tiêu phương pháp**: Tìm ra công thức dạng đóng của $f(n)$.  

---

### Cách giải với hệ thuần nhất ($f(n) = 0$)  
- Sử dụng phương trình đặc trưng:  
  $$ar^2 + br + c = 0$$  

- Giải phương trình trên cho ra 2 nghiệm $r_1, r_2$.  

- Với 3 trường hợp nghiệm:  
  1. Nếu $r_1, r_2$ là **số thực phân biệt**:  
     $$a_n = \alpha r_1^n + \beta r_2^n$$  
  2. Nếu $r_1 = r_2 = r$ là **nghiệm bội**:  
     $$a_n = \alpha r^n + \beta n r^n$$  
  3. Nếu $r_1, r_2 = u \pm iv$ là **số phức**:  
     $$a_n = \gamma^n\big[\alpha \cos(\theta n) + \beta \sin(\theta n)\big]$$  
     với $\gamma = \sqrt{u^2 + v^2}, \ \theta = \arctan{\frac{v}{u}}$.  

---

### Ví dụ: Phương trình Fibonacci  

- Đặt:  
  $$F(n) = F(n-1) + F(n-2), \quad F(0)=0, \ F(1)=1$$  
  $$\Rightarrow F(n) - F(n-1) - F(n-2) = 0$$  

- Phương trình đặc trưng:  
  $$r^2 - r - 1 = 0$$  
  với nghiệm:  
  $$r_{1,2} = \frac{1 \pm \sqrt{5}}{2}$$  

- Vì $r_1, r_2$ là nghiệm thực phân biệt ⇒ áp dụng công thức:  
  $$
  F(n) = \alpha \Big(\frac{1 + \sqrt{5}}{2}\Big)^n 
       + \beta \Big(\frac{1 - \sqrt{5}}{2}\Big)^n
  $$  

- Thay $n=0, n=1$ vào để tìm $\alpha, \beta$:  
  $$
  \begin{cases}
    F(0) = \alpha + \beta = 0 \\
    F(1) = \alpha \frac{1+\sqrt{5}}{2} + \beta \frac{1-\sqrt{5}}{2} = 1
  \end{cases}
  $$  

  Giải hệ:  
  $$
  \alpha = \tfrac{1}{\sqrt{5}}, \quad \beta = -\tfrac{1}{\sqrt{5}}
  $$  

- Vậy:  
  $$
  \begin{aligned}
  F(n) &= \frac{1}{\sqrt{5}} \Big(\frac{1+\sqrt{5}}{2}\Big)^n 
        - \frac{1}{\sqrt{5}} \Big(\frac{1-\sqrt{5}}{2}\Big)^n \\[6pt]
       &= \frac{1}{\sqrt{5}}\Big(\phi^n - \hat{\phi}^n\Big)
  \end{aligned}
  $$  

  với $\phi = \tfrac{1+\sqrt{5}}{2}$ (tỉ lệ vàng) và $\hat{\phi} = \tfrac{1-\sqrt{5}}{2}$.  

Đây chính là **công thức Binet** của dãy Fibonacci.  


**Các bài toán kinh điển**
> Nhờ 3 nhóm lên phân tích bằng 3 cách khác nhau
- Fibonacci O(n) - thế
- Hanoi Tower O($2^n$) - cây
- Segment Tree O(nlogn) - master theorem


**Bài tập về nhà**:

**BÀI 1**:
von Neumann’s neighborhood revisited:
Cho một ma trận ô vuông màu trắng N * N. Bắt đầu với một ô vuông bị tô đen, với mỗi một đơn vị thời gian nó sẽ tự loan màu sang các ô khác, hỏi sau n đơn vị thời gian thì có bao nhiêu ô bị loan màu.
Tìm ra công thức truy hồi và tìm độ phức tạp thời gian.

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

BÀI 3. Cho đoạn code
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

