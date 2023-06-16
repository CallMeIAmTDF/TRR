# Toan Roi Rac
## 1. Lý thuyết
1. **Chương 5**: Trình bày và đánh giá độ phức tạp của thuật toán chia đôi để tính $a^n$ với $a\in R, n \in N$.
    <pre>
    x = 1
    i = n
    while i > 0:
        if i % 2 == 1:
            x = x * a
        a = a * a
        i = i // 2
    </pre>
    **Độ phức tạp:**
    Cần chứng minh: $f(n) \leq 1 + log_2n$
    1. $f(1) = 1  \leq 1 + log_21$ : Đúng
    2. Giả sử $f(k) \leq 1 + log_2k$ đúng $\forall k=\overline{1,n}$. Xét thuật toán với n + 1. 
    Sau lần đầu tiên, $i = \left\lfloor \frac{n+1}{2} \right\rfloor$ nên $f(n+1) = 1 + f(\left\lfloor \frac{n+1}{2} \right\rfloor)$. 
    Mặt khác $1 \leq \frac{n+1}{2} \leq n$ nên $1 \leq \left\lfloor \frac{n+1}{2} \right\rfloor \leq n$
    Suy ra, $f(\left\lfloor \frac{n+1}{2} \right\rfloor) \leq 1 + log_2\left\lfloor \frac{n+1}{2} \right\rfloor \leq 1 + log_2\frac{n+1}{2} =log_2(n+1)$
    Do đó, $f(n+1) \leq 1 + log_2(n+1) \in log_2(n)$. **Thuật toán có độ phức tạp Loga**

2. **Chương 7**: Phát biểu, chứng minh công thức hàm **Euler phi** tìm các số nguyên dương nhỏ hơn $n$ và nguyên tố cùng nhau với $n$. Tìm $\Phi(1984)$
    1. Phát biểu
        Cho số nguyên dương $n \geq 2$. Theo **định lý cơ bản của số học**, $n$ có phân tích $n = p_1^{e_1}p_2^{e_2}...p_k^{e_k}$ trong đó $p_i$ là số nguyên tố, $e_i \in \mathbb{Z^+}, 1 \leq i \leq k$. Khi đó
        $\Phi(n) = n \displaystyle \prod_{i=1}^k(1-\frac{1}{p_i})$
    2. Chứng minh
        Với phân tích nguyên tố này của $n$, một số nguyên dương $m$ nguyên tố cùng nhau với $n$ nếu $p_i$ không là ước của m, $1 \leq i \leq k$. Trong các số m từ $1$ tới $n$ xét điều kiện 
        **$c_i:  p_i$ là ước của m** và cần tính
        $N(\overline{c_1} \overline{c_2} ... \overline{c_k})= N_0 - N_1+N_2-N_3+....+(-1)^k N_k$ trong 
        *  $N_0=n$
        *  $N_1=\displaystyle \sum_{1 \leq i\leq k} N(c_i) = \displaystyle \sum_{1 \leq i\leq k}\left\lfloor \frac{n}{p_i} \right\rfloor = \displaystyle \sum_{1 \leq i\leq k}\frac{n}{p_i}$
        *  $N(c_ic_j), 1 \leq i < j \leq k$, là số các số từ 1 tới n là bội của $p_i$ và $p_j$, tức là bội của $lcm(p_i,p_j)$. Mặt khác, $p_i, p_j$ là hai số nguyên tố cùng nhau, nên $lcm(p_i, p_j) = p_ip_j$. Suy ra $N(c_ic_j)=\left\lfloor \frac{n}{p_ip_j}\right\rfloor=\frac{n}{p_ip_j}$
        $N_2 = \displaystyle \sum_{1 \leq i < j\leq k} N(c_ic_j)=\displaystyle \sum_{1 \leq i < j\leq k}\frac{n}{p_ip_j}$
        * Tương tự
            $N_3 = \displaystyle \sum_{1 \leq i < j < l\leq k} N(c_ic_jc_l) = \displaystyle \sum_{1 \leq i < j < l\leq k}\frac{n}{p_ip_jp_l},...$
            $N_r = \displaystyle \sum_{1 \leq i_1 < i_2 < .... < i_r\leq k}N(c_{i_1}c_{i_2}...c_{i_r}) = \displaystyle \sum_{1 \leq i_1 < i_2 < .... < i_r\leq k}\frac{n}{p_{i_1}p_{i_2}...p_{i_r}},...$
            $N_k = N(c_1,c_2,...c_k)=\frac{n}{p_1p_2...p_k}$
        * Các số này có thừa số chung là n, nên
        $N(\overline{c1}\overline{c2}...\overline{ck}) = n(1 - \displaystyle \sum_{1 \leq i\leq k}\frac{1}{p_i} + \displaystyle \sum_{1 \leq i < j\leq k}\frac{1}{p_ip_j} - \displaystyle \sum_{1 \leq i < j < l\leq k}\frac{1}{p_ip_jp_l} +...+ (-1)^{r-1}\displaystyle \sum_{1 \leq i_1 < i_2 < .... < i_r\leq k}\frac{1}{p_{i_1}p_{i_2}...p_{i_r}} +(-1)^k\frac{1}{p_1p_2...p_k})$
        $=n\displaystyle\prod_{i=1}^{k}(1-\frac{1}{p_i})$
    3. $\Phi(1984)$
        $1984 = 2^6 \times 31$
        $p_1 = 2, p_2 = 31$
        $\Phi(1984) = 1984 \times \displaystyle \prod_{i=1}^{2}(1 - \frac{1}{p_i}) = 960$
        
3. **Chương 8**: Số Catalan là gì? Trình bày hệ thức đệ quy của số Catalan, và phương pháp hàm sinh để tìm công thức tường minh của nó
    1. Số catalan: Số Catalan là số cách tính tích các ma trận $A = A_0 A_1 A_2 A_3...A_n$. 
    2. Hệ thức đệ quy
        $c_n = \displaystyle \sum_{k=0}^{n-1}c_kc_{n-k-1}$
        với $c_1 = 1, c_0 = 1$
    3. Dùng hàm sinh
        Xét $f(x) = \displaystyle \sum_{n=0}^{\infty}c_nx^n$, ta có$[f(x)]^2 = \displaystyle \sum_{n=0}^{\infty}a_nx^n$ với $a_n=\displaystyle \sum_{k=0}^{n}c_kc_{n-k}=c_{n+1}$. Suy ra
        $[f(x)]^2 = \displaystyle \sum_{n=0}^{\infty}c_{n+1}x^n=\frac{1}{x}\displaystyle \sum_{n=0}^{\infty}c_{n+1}x^{n+1}=\frac{1}{x}\displaystyle \sum_{n=1}^{\infty}c_{n}x^{n}=\frac{1}{x}[f(x)-1]$
        $\Rightarrow x[f(x)]^2 - f(x) + 1 = 0 \Rightarrow f(x)=\frac{1\pm \sqrt{1-4x}}{2x}$
        Hệ số của $x^n$ trong $f(x)$ tương ứng với mỗi nghiệm, là:
        $c_n = \pm \frac{1}{2} \bigg(  \frac{1}{2} , {n+1} \bigg)(-4)^{n+1} = \pm \frac{1}{2} \frac{\frac{1}{2}(\frac{1}{2}-1)(\frac{1}{2}-2)...(\frac{1}{2}-n)}{(n+1)!}(-4)^{n+1}$
        Ta chọn nghiệm $f(x)$ ứng với dấu - để hệ số này dương. Cuối cùng,
        $c_n=\frac{1.2.3...(2n-1)(2n)}{2.4...(2n)}\frac{2^n}{n!(n+1)}=\frac{1}{n+1}\frac{(2n)!}{n!n!}=\frac{1}{n+1}\bigg( 2n , n  \bigg)$
4. **Chương 9:** Phát biểu, chứng minh định lý **Léma** về đánh giá thuật toán **Euclid** tìm ước chung lớn nhất của hai số nguyên dương. Trình bày thuật toán **Euclid** tìm gcd(2023, 1984)
    1. Phát biểu
        (Định lý). Cho $a,b \in \mathbb{Z^+}, a,b \geq 2$. Số phép chia dùng trong thuật toán Euclid để tìm ước chung lớn nhất của a và b không quá 5 lần số chữ số của b
    3. Chứng minh
        Đặt $r_0=a$ và $r_1=b$, ta có:
        $r_0 = r_1q_1 + r_2,(0 < r_2<r_1)$,
        $r_1 = r_2q_2 + r_3$ $,(0 < r_3<r_2)$,
        $r_2 = r_3q_3 + r_4$ $,(0 < r_4<r_3)$,
        $...................$,
        $r_{n-2} = r_{n-1}q_{n-1}+r_n$ $,(0 < r_n < n_{n-1})$,
        $r_{n-1}=r_nq_n$.
        Khi đó, $gcd(a,b)=r_n$, là phần dư khác 0 cuối cùng, và thuật toán thực hiện n phép chia.
        Ta thấy, $q_i\geq1, \forall i=\overline{1,n}$. Riêng $q_n \geq 2$, vì $r_{n-1}=r_nq_n$ mà $0<r_n<r_{n-1}$. Như vậy
        $r_n>0\Rightarrow r_n \geq 1 = F_2$,
        $r_{n-1}=r_nq_n\geq 1\cdot2=2=F_3$,
        $r_{n-2}=r_{n-1}q_{n-1}+r_n\geq F_3\cdot1+F_2 = F_4$,
        $r_{n-3}=r_{n-2}q_{n-2}+r_{n-1}\geq F_4\cdot1+F_3 = F_5$,
        $..........................$,
        $r_2=r_3q_3+r_4\geq F_{n-1}\cdot1+F_{n-2}=F_n$,
        $b=r_1=r_2q_2+r_3\geq F_n\cdot1+F_{n-1}=F_{n+1}$.
        Dẫn đến
        $b \geq F_{n+1}>\alpha^{(n+1)-2}=\alpha^{n-1}$
        $\Rightarrow n-1 < log_\alpha b = log_\alpha10\cdot log_{10}b=4.784971log_{10}b<5log_{10}b$
        Nếu $b$ có $k$ chữ số, thì $10^{k-1}\leq b < 10^k$, nên $log_{10}b<k$. Do đó $n-1<5k$, hay $n\leq 5k$, tức là số phép chia trong thuật toán Euclid không quá 5 lần số chữ số của b.
    7. gcd(2023, 1984)
        *    $2023 = 1984 \cdot1 + 39$
        *    $1984 = 39 \cdot50 + 34$
        *    $39 = 34 \cdot1 + 5$
        *    $34 = 5 \cdot6 + 4$
        *    $5 = 4 \cdot1 + 1$
        *    $4 = 1\cdot4 + 0$
        *    $\Rightarrow gcd(2023, 1984) = 1$
6. **Chương 9:** Trình bày và đánh giá độ phức tạp của thuật toán **sắp xếp trộn**
    1. Trình bày
        *  Nếu dãy chỉ có 1 số, ta không cần làm gì cả. Ngược lại, chuyển xuống thực hiện bước (2)
        *  Chia đôi dãy được hai dãy con $a_1, a_2, ..., a_k$ và $a_{k+1}, ..., a_n$ cỡ $\frac{n}{2}$. Sắp xếp hai dãy này, được hai dãy tăng
        *  Trộn hai dãy tăng cho thành một dãy tăng.
    2. Đánh giá độ phức tạp
        Gọi $f(n)$ là số chu trình tối giản của thuật toán với dãy cỡ n. Ta có 
        $f(n)=2f(\frac{n}{2})+n$
        Xét n = $2^k \Leftrightarrow k = log_2n$, và $a_k=f(n)=f(2^k)$ thì
        $a_k=2f(x^{k-1})+2^k=2a_{k-1}+2^k$
        trong đó $a_0=f(1)=0$
        Giaỉ hệ thức đệ quy này ta được $a_k=2^kk$, tức là $f(n)=nlog_2n$. Thuật toán có độ phức tạp $nlog_2n$.
## 2. Bài tập trình bày lời giải
1.
<pre>
    for i = 1 to 10 do
        for j = 1 to i do
            for k = 1 to j - 1 do:
                print i, j, k
</pre>
* C1:
    i = 1:
    * j = 1, không in

    i = 2:
    * j = 1, không in
    * j = 2, k = 1: in 1 lần

    i = 3:
    * j = 1, không in
    * j = 2, k = 1: in 1 lần    
    * j = 3, k = 1, 2: in 2 lần
    
    ...
    i = 10:
    * j = 1, không in
    * j = 2, k = 1: in 1 lần    
    * j = 3, k = 1, 2: in 2 lần
    * ...
    * j = 10, k = 1, 2, 3, ..., 9: in 9 lần

    **Tổng số lần in:** $0 + (0 + 1) + (0 + 1 + 2) + ... + (0 + 1 + 2 + ... + 9)$
    $= \displaystyle \sum_{i=0}^{9} (\displaystyle \sum_{j = 0}^{i}j)$
* C2
$\begin{cases}
    1 \leq i \leq 10 \\
    1 \leq j \leq i \\
    1 \leq k \leq j-1
\end{cases}$
2. Bằng quy nạp, chứng minh $\displaystyle \sum_{i=1}^n\frac{1}{i(i+1)} = \frac{n}{n+1}$
Xét khẳng định mở $S(n) = \displaystyle \sum_{i=1}^n\frac{1}{i(i+1)} = \frac{n}{n+1}$
$S(1): \frac{1}{2}=\frac{1}{2}$ Đúng
Giả sử với n cho trước, S(n) đúng. Ta chứng minh S(n+1) đúng. Thật vậy
$\displaystyle \sum_{i=1}^{n+1}\frac{1}{i(i+1)} = \displaystyle \sum_{i=1}^n\frac{1}{i(i+1)} + \frac{1}{(n+1)(n+2)}$
$=\frac{n}{n+1} + \frac{1}{(n+1)(n+2)}$ vì $S(n)$ đúng
$= \frac{n^2+2n+1}{(n+1)(n+2)}=\frac{(n+1)^2}{(n+1)(n+2)}=\frac{n+1}{n+2}$
Theo nguyên lý quy nạp, $S(n)$ đúng $\forall n \in \mathbb{Z^+}$
3. **Chương 6:** Cho quan hệ $\mathbb{R}$ trên tập $A$ cỡ $n=4,5,6$. Tìm bao đóng bắc cầu $\mathbb{R^*}$ và $\mathbb{R}$ bằng thuật toán:
    * nhân ma trận: ghi ra các ma trận $M, M^2,...,M^n$ và $M^*$
    <pre>
    import numpy as np 
    M = np.array([[0, 1, 0, 1], 
              [0, 1, 0, 0],
              [1, 0, 0, 0],
              [0, 0, 1, 0]], dtype=bool)
    n = len(M)
    A = M.copy()
    L = M.copy()
    for k in range(2, n+1):
        L = M.dot(L)
        A += L
        print(k, np.array(L, dtype=int))
    print("R* ", np.array(A, dtype=int))
    </pre>
    * Warshall: ghi ra các ma trận $W_0,W_1,W_2,...,W_{n-1}$và$W^*$
    <pre>
    import numpy as np 
    W = np.array([[0, 1, 0, 1], 
              [0, 1, 0, 0],
              [1, 0, 0, 0],
              [0, 0, 1, 0]], dtype=bool)
    n = len(W)
    for k in range(n):
        for i in range(n):
            for j in range(n):
                W[i, j] += W[i, k] * W[k, j]
        print(k+1, np.array(W, dtype=int))
    </pre>
4. **Chương 9** Cho hàm $a(n)$ định nghĩa bằng đệ quy 
    <pre>
    def a(n):
        if n == 0:
            return 1
        return 2*a(n-1) + 1
    </pre>
    * $a(3)$
        $a(3) =15$
    * Đặt $f(n)$ là số phép toán số học và phép so sánh dùng để tính $a(n)$. Lập hệ thức đệ quy cho dãy $f(n)$ và giải $f(n)$    
        * $f(0)$: số phép toán số học và so sánh để tính $a(0)$
        $f(0)=1$
        * Để tính $a_n$ cần 1 phép so sánh với 0, cần tính $a_{n-1}$, kiểm tra  sau đó nhân 2 và cộng 1 (2 phép toán số học) để tính $a{n-1}$ cần $f{n-1}$ phép tính.
        * Như vậy $f(n)=f(n-1)+3$ với $f(0) = 1$
    * Giải $f(n)$
        * $f(n) = f(n-1)+3$ với $f(0) =1$ là cấp số cộng ứng với $d = 3 , c = 1$, có nghiệm $f(n)=3\cdot n+1$ 
## Các thuật toán, công thức
1. Giải hệ thức đệ quy
    <pre>
    rsolve([Phương trình], [biểu thức cần giải], [Số liệu cho trước])
    
    from sympy import *
    n = symbols('n')
    a = symbols('a', cls=Function)
    print(rsolve(a(n) - a(n-1) - 3, a(n), {a(0) : 3}))
    </pre>
2. Chuyển số hệ b sang hệ 10
    <pre>
        int(<Số cần chuyển dạng string>, <hệ>)
        int('10101', 2)
    </pre>
3. Phân tích thừa số nguyên tố
    <pre>
        from sympy import *
        factorint(1900)
    </pre>
4. Số $a_1^{e_1}\cdot a_2^{e_2}\cdot a_n^{e_n}$ có $(e_1+1)\cdot(e_2+1)\cdot(e_3+1)$ ước
5. Số **hàm** từ tập cỡ **m** vào tập cỡ **n** (hay số cách xếp **m vật** vào **n hộp**): $n^m$
6. Số **đơn ánh** từ tập cỡ **m** vào tập cỡ **n** (hay số cách xếp **m vật** vào **n hộp** sao cho **mỗi hộp không quá một vật**): $P(n,m)$
7. Có bao nhiêu **toàn ánh** từ tập cỡ **n** vào tập cỡ **m** (hay số cách xếp **m vật** vào **n hộp** sao cho **không hộp nào trống**)
$\displaystyle \sum_{k=0}^n(-1)^k\cdot C(n, n-k)\cdot (n-k)^m$
8. Số Stirling S(m, n)  (hay số cách chia **m vật** thành **n phần** khác rỗng, **không quan tâm thứ tự các phần**): $S(m, n) = S(m-1, n-1) + n \cdot S(m-1, n)$ với khi $m=n$, $S(m,n)=1$ và khi $n=1$ , $S(m,n)=1$
9. Số **quan hệ** từ tập cỡ **m** vào tập cỡ **n**: $2^{m\cdot n}$
10. Xếp không hộp nào cùng số
$n!\cdot [1-\frac{1}{1!} + \frac{1}{2!}-\frac{1}{3!}+...+\frac{(-1)^n}{n!}]$
11. Số cách $x_1+x_2+...+x_n = r$: $C(n+r-1, r)$
