# CH02. Introduction to Number Theory

- [2.1 Divisibility and The Division Algorithm](#21-divisibility-and-the-division-algorithm)
  * [1) Divisibility](#1-divisibility)
  * [2) The Division Algorithm](#2-the-division-algorithm)
- [2.2 The Euclidean Algorithm(유클리드 호제법)](#22-the-euclidean-algorithm유클리드-호제법)
  * [1) Greatest Common Divisor(최대 공약수)](#1-greatest-common-divisor최대-공약수)
  * [2) Finding the Greatest Common divisor](#2-finding-the-greatest-common-divisor)
    + [(1) 방법](#1-방법)
    + [(2) 예제](#2-예제)
- [2.3 Modular Arithmetic](#23-modular-arithmetic)
  * [1) The Modulus](#1-the-modulus)
  * [2) Properties of Congruences](#2-properties-of-congruences)
    + [(1) 성질](#1-성질)
    + [(2) 예제](#2-ec9888eca09c-1)
  * [3) Modular Arithmetic Operations](#3-modular-arithmetic-operations)
    + [(1) 성질](#1-ec84b1eca788-1)
  * [4) Properties of Modular Arithmetic](#4-properties-of-modular-arithmetic)
    + [(2) 성질](#2-성질)
    + [(3) 예제](#3-예제)
  * [5) The Extended Euclidean Algorithm](#5-the-extended-euclidean-algorithm)
    + [(1) 공식](#1-공식)
    + [(2) 예제](#2-ec9888eca09c-2)

---

# 2.1 Divisibility and The Division Algorithm



## 1) Divisibility

- if a= mb, b divides a (정수 ㅇ간)
    - b | a
    - ex) 5 | 20, -5 | 30
- if a | 1, then a = += 1
- if a | b, b | a, then a = += b
- Any b ≠ 0 divides 0.
- if a | b and b | c, then a | c.
    - ex) 3 | 12, 12 | 24, then 3 | 24
- if b | g and b | h, then b | (mg + nh).
    - g = g$_1$ x b
    - h = $h_1$ x b
    - mg + nh = mg$_1$b +  nh$_1$b = (mg$_1$ + nh$_1$)b
    - ex) b = 7, g = 14, h = 63
        - m = 3, n = 2 ⇒ 7 | (3 x 14 + 2 x 63)

## 2) The Division Algorithm

- a = q · n + r
    - 0 ≤ r < n (나머지)
    - q = ⌊a/n⌋ (몫)

# 2.2 The Euclidean Algorithm(유클리드 호제법)

---

> 정수론의 기본 기술 중 하나는 두 양의 정수의 최대 공약수를 결정하는 간단한 절차인 유클리드 알고리즘입니다. 
먼저 간단한 정의가 필요합니다: 두 정수는 공통 양의 정수 인수가 1인 경우에만 서로소 관계이 있습니다.
> 

## 1) Greatest Common Divisor(최대 공약수)

- c = gcd(a, b)
    1. c | a, c | b
    2. any divisor of a and b is divisor of c
        
        (a와 b의 약수는 c의 약수이다)
        
- gcd(a, b) = max{k **|** k|a, k|b}
    - gcd(a, b) = gcd(|a|, |b|)

## 2) Finding the Greatest Common divisor

> 이제 두 정수의 최대공약수를 쉽게 찾는 Euclid의 알고리즘을 설명합니다(그림 2.2). 이 알고리즘은 암호화에서 광범위한 의미를 갖습니다. 알고리즘에 대한 설명은 다음과 같이 설명해 나갈 수 있습니다.
> 

### (1) 방법

1. 정수 $a$와 $b$ 의 최대공약수 $d$를 구한다고 가정하자:
그것은 $d = gcd(a, b)$ 를 결정하게 된다.
$gcd(|a|, |b|) = gcd(a, b)$이기 때문에, $a ≥ b ≥ 0$ 이라고 가정해도 아무런 문제가 없다
2. $a$를 $b$로 나누고, dividing 알고리즘을 적용하면 다음과 같이 나타낼 수 있다.
    - $a = q_1b + r_1$   (0 ≤ $r_1$ < b) (2.2)
3. $r_1 = 0$ 인 경우,
    
    따라서 b는 a를 나누고, b와 a를 모두 나누는 더 큰 수는 분명히 없다. 왜냐하면 그 수는 b보다 클 것이기 때문이다. 
    따라서 $d = gcd(a, b) = b$이다.
    
4. $r_1 \neq 0$ 인 경우,
    
    나눗셈의 기본 속성에 의해 $d | r_1$ 을 정의할 수 있다. 
    $d |a$와 $d | b$는 함께 $d|r_1$와 같은 $d|r_1$$d | (a - q_1|b)$을 암시한다
    
5. 유클리드 알고리즘을 적용하기 전에 아래의 질문에 답해보자
    - $gcd(b, r_1)$ = ?
    - $d | b$ 와 $d | r_1$ 을 알고 있다
    - 이제 $b$와 $r_1$을 모두 나누는 임의의 정수 c를 취하자
    - 따라서, $c | (q_1b+r_1) = a$ 이다.
    - c가 a와 b를 모두 나누기 때문에, $c \leq d$ 가 있어야 하며, 이는 a와 b의 최대 공약수이다.
    - 따라서, $d = gcd(b, r1)$이다.
6. 이제 다시 (2.2) 식으로 돌아가서 $r_1 \neq 0$ 인 경우를 가정해보자.
    - $b \gt r_1$ 이기 때문에, $r_1$으로 $b$를 나눌 수 있고 아래처럼 division 알고리즘을 적용할 수 있다.
        - $b = q_2r_1 + r_2 \ \ \ \ \ \ \  (0 \leq r_2 < r_1)$이이
7. 이제 이전과 같이, $r_2 = 0$인 경우, $d=r_1$이 되고, $r_2 \neq 0$인 경우, $d = gcd(r_1, r_2)$가 된다. 나머지 값은 음수가 아닌 값의 내림차순을 형성하므로 나머지가 0일 때 종료해야 한다. 이것은 예를 들어, $r_{n-1}$을 $r_n$으로 나눈 $(n + 1)$번째 단계에서 발생한다. 그 결과는 다음과 같은 방정식 체계이다.
    
    ![Untitled](./CH02%20Introduction%20to%20Number%20Theory/Untitled.png)
    
- 각 반복에서 최종적으로 $d = gcd(r_n, 0) = r_n$이 될 때까지 $d = gcd(r_i, r_{i+1})$을 수행한다.
따라서, 이렇게 나누기 알고리즘을 반복적으로 적용하여 두 정수의 최대공약수를 구할 수 있다.
- 이 체계는 유클리드 알고리즘(Euclidean algorithm)으로 알려져 있다.

### (2) 예제

1. gcd(a, b) = b in b | a
    - gcd(b, r), a = qb + r
    - ex) gcd(1000, 520)
        
        = gcd(520, 480) →재귀적으로 구현
        
        = gcd(480, 40) = 40
        
    
    <div style="background-color: #393939; border-radius:15px">
    <br>

    &nbsp;&nbsp;&nbsp;💡 $d = gcd(a, b) = gcd(1000, 520) \newline \ \ \ \ \ \ \ \ 1000 = 1 \times 520 + 480 \newline \ \ \ \ \ \ \ \ 520 = 1 \times 480 + 40 \newline \ \ \ \ \ \ \ \ 480 = 12 \times 40 + 0 \newline \ \ \ \ \ \ \ \ \therefore d = gcd(1000, 520) = 40$
    <br></br>
    </div>
    
2. d = gcd(a, b) = gcd(1160718174, 316258250)
    
    ![Untitled](./CH02%20Introduction%20to%20Number%20Theory/Untitled%201.png)
    
    ![Untitled](./CH02%20Introduction%20to%20Number%20Theory/Untitled%202.png)
    

# 2.3 Modular Arithmetic

---

## 1) The Modulus

- %, mod ⇒ 정수를 다룰 때, 매우 유용하다
    - ex)
        - 11 mod 7 = 4
        - -11 mod 7 = (-2) x 7 + 3 mod 7 = 3
- if $a\ mod\ n=b \ mod\ n$, then $a \equiv b\ (mod\ n)$
    - 즉, n으로 나누었을 때, 나머지가 같다는 의미이다
    - ex) $73 \equiv 4\ (mod\ 23);\ \ \ \ 21\equiv -9\ (mod\ 10)$
- if $a \equiv 0\ (mod\ n)$, then n | a.

## 2) Properties of Congruences

### (1) 성질

1. $a \equiv b\ (mod\ n)\$  if $n|(a - b)$.
2. $a \equiv b\ (mod\ n)$ implies .
3. $a \equiv b\ (mod\ n)$ and $b \equiv c\ (mod\ n)$ imply a $a \equiv c\ (mod\ n)\$ 

### (2) 예제

- $23 \equiv 8\ (mod\ 5)$  because $23 - 8 = 15 = 5 \times 3$
- $-11 \equiv 5\ (mod\ 8)$ because $-11 - 5 = -16 = 8 \times (-2)$
- $81 \equiv 0\ (mod\ 27)$   because $81 - 0 = 81 = 27 \times 3$

## 3) Modular Arithmetic Operations

### (1) 성질

1. [(a mod n) + (b mod n)] mod n = (a + b) mod n
2. [(a mod n) - (b mod n)] mod n = (a - b) mod n
3. [(a mod n) * (b mod n)] mod n = (a * b) mod n

## 4) Properties of Modular Arithmetic

- Zn = {0, 1, c , (n - 1)} 이라고 정의하자
- $+\ (mod\ n)$
    - ex) $+\ (mod\ 8)$
        
        ![Untitled](./CH02%20Introduction%20to%20Number%20Theory/Untitled%203.png)
        
- $\times\ (mod\ n)$
    - ex) $\times\ (mod\ 8)$
        
        ![Untitled](./CH02%20Introduction%20to%20Number%20Theory/Untitled%204.png)
        
    - 곱셈의 역원은 존재하지 않는 경우가 있다.

### (2) 성질

![Untitled](./CH02%20Introduction%20to%20Number%20Theory/Untitled%205.png)

<aside style="background-color: #393939; border-radius:15px">
<br>

&nbsp;&nbsp;&nbsp;💡 if $a \times b\equiv(a\times c)\ (mod\ n)$,

- then $b \equiv c\ (mod\ n)$.

- (단, a와 n이 서로소(relative prime)일 때만 성립)
<br></br>
</aside>

- 반례)
    - $6\times3=18\equiv2\ (mod\ 8)$
    - $6\times7=42\equiv2\ (mod\ 8)$
    - but, $3\not\equiv7\ (mod\ 8)$ → 6과 8이 서로소가 아니기 때문이다.
- mod 13 처럼
    - n 이 소수라면, 모든 수에 대해 역원($a^{-1}$, $-a)$가 존재한다.

### (3) 예제

- $a^{-1}\ (mod\ 26)$
    - ex) $9^{-1}\ (mod\ 26) = 3$
    - 방법1) 손으로 1 ~ 26까지 다 해보는 것
        - → n이 큰 수가 되면 힘들다.
    - 방법2) Extended Euclidean Algorithm 사용

## 5) The Extended Euclidean Algorithm

### (1) 공식

$i = -1)\ \ a(r_{-1}) = q_1b+r_1\newline 
i = \ \ \ 0)\ \ b(r_{0}) = q_2r_1+r_2\newline 
i = \ \ \ 1)\ \ r_{1} = q_3r_2+r_3\newline 
i = \ \ \ 2)\ \ r_{2} = q_4r_3+r_4\newline
... \newline
i = n - 2)\ \ q_{n}r_{n-1}+r_n\newline
i = n - 1)\ \ q_{n+1}r_{n}+0$

$a(=r_{-1}) = ax_{-1}+by_{-1}\newline
b(=r_{0}) = ax_{0}+by_{0}\newline
r_{1} = ax_{1}+by_{1}\newline
r_{2} = ax_{2}+by_{2}\newline
... \newline
r_{n - 2} = ax_{n-2}+by_{n-2}\newline
r_{n - 1} = ax_{n-1}+by_{n-1}\newline
r_{n} = ax_{n}+by_{n}$

- $r_n$ → gcd(a, b)
- $x_n$ → $x$
- $y_n$ → $y$

<aside style="background-color: #393939; border-radius:15px">
<br>

&nbsp;&nbsp;&nbsp;💡 $x_i =x_{i-2}-q_ix_{i-1}\newline\ \ \ \ \ \ \ \ 
y_i =y_{i-2}-q_iy_{i-1}$
<br></br>
</aside>

- c책
    
    ![Untitled](./CH02%20Introduction%20to%20Number%20Theory/Untitled%206.png)
    
    ![Untitled](./CH02%20Introduction%20to%20Number%20Theory/Untitled%207.png)
    

### (2) 예제

1. 책 예제
    - 문제
        - $a = 1759, b = 550$
        - $1759x + 550y = gcd(1759, 550)$ 만족하는 x, y, d 구하기
    - 풀이
        
        ![Untitled](./CH02%20Introduction%20to%20Number%20Theory/Untitled%208.png)
        
    - 답
        - $1759 \times (-111) + 550 \times 355 = -195249 + 195250 = 1$
2. 응용 예제
    - 문제
        - $9^{-1}\ mod\ 26 =\ ?$
    - 풀이
        - $9y\ mod \ 26 = 1$
        - $26x+9y=1$ 인 $x$와 $y$구하기
            - $gcd(26,9) = 1$
        - 계산
            1. $i = -1)\ \ 26(r_{-1}) = 2\times 9+8\newline 
            i = \ \ \ 0)\ \ 9(r_{0}) = 1 \times 8+1\newline 
            i = \ \ \ 1)\ \ 8(r_{1}) = 8 \times 1+0$
            2. $26(=r_{-1}) = 26x_{-1}+9y_{-1}=26\times1+9\times0\newline
            9(=r_{0}) = 26x_{0}+9y_{0}=26\times0+9\times1\newline
            8(=r_{1}) = 26x_{1}+9y_{1}=26\times1+9\times(-q_2)=26\times1+9\times-2)\newline
            1(=r_{2}) = 26x_{2}+9y_{2}$
            3. $x_2=x_{i-2}-q_ix_{i-1}=0-1\times1=-1$
                
                $y_2=y_{i-2}-q_iy_{i-1}=1-1\times-2=3$
                
                d = 1
                
            4. $26x+9y=1, x=-1, y=2\newline
            \therefore 9^{-1}\ mod\ 26 = 3$

# 2.4 Prime numbers(소수)

---

- $a = p_1^{a1}\times p_2^{a2}\times ...\times p_t^{at}$
    - a는 정수
    - 소수들의 지수승 형태로 소인수 분해 가능하다
    - ex)
        
        $91 = 7^1\times13^1\newline
        3600 = 2^4\times3^2\times5^2$
        
- 조금 더 일반화 하면,
    
    $a=\prod\limits_{p\in P} p^{a_p}$, $(a_p \geq0, \ P \ is\ the\ set\ of\ all\ prime\ numbers)$
    
    - $P = \{2, 3, 5, 6, 11, 13, ...\}$
    - ex)
        
        $12: \{a_2=2, a_3=1\}\newline
        18: \{a_2=1, a_3=2\}$
        

<aside style="background-color: #393939; border-radius:15px">
<br>

&nbsp;&nbsp;&nbsp;💡 
$a=\prod\limits_{p\in P} p^{a_p}$
$b=\prod\limits_{p\in P} p^{b_p}$

- ⇒ $k = ab = \prod\limits_{p\in P} p^{k_p},\ \ k_p=a_p+b_p$
- ex)
    
    $12\times18=\{a_2=2, a_3=1\} \times \{a_2=1, a_3=2\}=\{a_2=3, a_3=3\}=2^3\times3^3$
    <br></br>
</aside>

<aside style="background-color: #393939; border-radius:15px">
<br>

&nbsp;&nbsp;&nbsp;💡 $a=\prod\limits_{p\in P} p^{a_p}$, $b=\prod\limits_{p\in P} p^{b_p}$

- If $a | b$, then $a_p \leq b_p\ for\ all\ p.$
- 즉, 각 지수가 크거나 같아야 한다.
- ex)
    
    $a=12;\ b=36;\ 12|36\newline
    12=2^2\times3;\ 36=2^2\times3^2\newline
    a_2=2=b_2\newline
    a_3=1\leq2=b_3$
    
    따라서, 부등식 $a_p\leq b_p$는 모두 소수에 대해 만족한다.
    <br></br>
</aside>

<aside style="background-color: #393939; border-radius:15px">
<br>

&nbsp;&nbsp;&nbsp;💡 $\gcd{(a,b)}$: $k_p=min(a_p,b_p)\ for\ all\ p$

- 각 지수의 minimum을 취한다.
- 이렇게 하면 훨씬 쉽게 gcd를 구할 수 있다.
    - 하지만, 더 좋은 알고리즘 X ⇒ 소인수 분해하는 작업에 많은 시간이 걸리기 때문이다.
- ex)
    
    $\gcd(12, 18)=\gcd(2^3\times 3^1, 2^1\times3^2)=2^1\times3^1$
    <br></br>
</aside>

# 2.5 Fermat’s And Euler’s Theorem

---

## 1) Fermat’s Theorem

### (1) 설명

- If a is NOT divisible by p(p로 나누어 떨어지지 않으면, 즉 서로소이면), then
    - $a^{p-1}\equiv1\ (\mod p\ )$
    - $a^p\equiv a(\mod p\ \ )$은 Fermat’s Theorem의 대체 식이다.

⇒ 나중에 RSA 알고리즘 할 때 쓰이게 된다.

### (2) 증명

-생략-

### (3) 예제

- ex) $a= 7, p = 19$
    - $7^{18}\equiv1(\mod 19\ )$