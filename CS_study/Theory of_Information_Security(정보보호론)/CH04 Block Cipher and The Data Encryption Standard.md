# CH04. Block Cipher and The Data Encryption Standard(DES)

- [4.1 Traditional Block Cipher Structure](#41-traditional-block-cipher-structure)
  * [1) Stream Ciphers and Block Ciphers](#1-stream-ciphers-and-block-ciphers)
    + [(1) Stream Cipher](#1-stream-cipher)
    + [(2) Block Cipher](#2-block-cipher)
  * [2) Motivation for the Feistel Cipher Structure](#2-motivation-for-the-feistel-cipher-structure)
  * [3) The Feistel Cipher](#3-the-feistel-cipher)
- [4.2 The Data Encryption Standard](#42-the-data-encryption-standard)
  * [0) Simplified DES 알고리즘](#0-simplified-des-알고리즘)
    + [(1) 설명](#1-설명)
    + [(2) Key 생성](#2-key-생성)
    + [(3) Encryption (암호화) & 복호화](#3-encryption-암호화--복호화)
    + [(4) 예제](#4-예제)
  * [1) DES Encryption](#1-des-encryption)
---

# 4.1 Traditional Block Cipher Structure

## 1) Stream Ciphers and Block Ciphers

- 암호화는 Stream Cipher와 Block Cipher로 나뉜다

### (1) Stream Cipher

![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled.png)

- 데이터를 순서대로 쭉 집어넣느다
- 단점
    - 중간에 데이터가 손실되면, 뒷 데이터가 모두 엉망이 되어버린다.

### (2) Block Cipher

![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%201.png)

- 예를 들어 block size가 128bit이면, 데이터를 128bit씩 끊어서 보낸다
- 장점
    - 하나의 block이 손상되어도, 다른 block들은 영향을 받지 않는다.

## 2) Motivation for the Feistel Cipher Structure

- block cipher는 n bits의 plaintext block에서 작동하여 n bits의 ciphertext를 생성한다
- 2$^n$개의 다른 plaintext block들이 있고, 암호화를 되돌리기 위해선(즉, 복호화 하기 위해선), 각각의 block이 unique한 cipher text block을 생성해야 한다.
- 이러한 변환을 reversible 또는 nonsingular라고 부른다
- ex) 2-bit 암호화
    
    ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%202.png)
    

## 3) The Feistel Cipher

- Substitution: 각 평문 요소 또는 요소 그룹은 해당하는 암호문 요소 또는 요소 그룹으로 고유하게 대체된다.
- Permutation: 평문 요소의 시퀀스는 해당 시퀀스의 순열로 대체된다. 즉, 시퀀스에서 요소가 추가되거나 삭제되거나 대체되지 않고 시퀀스에서 요소가 나타나는 순서가 변경된다.
    
    ⇒ 이 2가지를 잘 섞는 것이 암호화의 목표이다.
    
- Feistel Encryption and Decryption (16 rounds)
    
    ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%203.png)
    

# 4.2 The Data Encryption Standard

---

## 0) Simplified DES 알고리즘

### (1) 설명

- key는 10bits
- 2 round 과정 거침 → key 2개 필요
    - 하나의 key로부터 subkey를 생성하게 된다.
    - 유저는 하나의 key만 기억한다
- 전체 그림
    
    ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%204.png)
    

### (2) Key 생성

- sender와 receiver가 공유하는 10-bit key로부터 subkey를 생성한다.
    - 즉, Key로부터 2개의 8-bit subkey가 생성된다.
- Permutation P10
    
    ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%205.png)
    
    ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%206.png)
    
- Permutation P8
    
    ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%207.png)
    
- 알고리즘 이미지
    
    ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%208.png)
    

### (3) Encryption (암호화) & 복호화

- Initial and Final Permutations
    - IP
        
        ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%209.png)
        
    - IP$^{-1}$
        
        ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2010.png)
        
- The Function $f_K$
    - $f_K(L,R)=(L\oplus F(R,SK),R)$
- Permutation E/P
    
    ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2011.png)
    
- Sbox
    
    ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2012.png)
    
- Permutation P4
    
    ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2013.png)
    
- 상세 이미지
    
    ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2014.png)
    

### (4) 예제

- Plain text = 0111 0010
- key = 10100 00010 (10-bit)
1. sub key 생성
    - key = 10100 00010 (10-bit)
        
        ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2015.png)
        
2. Encryption
    - key = 10100 00010 (10-bit)
    - Plain text = 0111 0010
    1. Round1
        1. IP & F function
            
            ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2016.png)
            
        2. F $\oplus$ LE$_0$
            
            ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2017.png)
            
        3. SW
            
            ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2018.png)
            
    2. Round 2
        1. F function
            
            ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2019.png)
            
        2. F $\oplus$ LE$_1$
            
            ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2020.png)
            
        3. $IP^{-1}$
            
            ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2021.png)
            
        4. 
3. Decryption
    - Cipher text = 0111 0111
    - Key = 10100 00010 (10-bit)
    1. IP
        
        ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2022.png)
        
    2. Round1
        1. F function
            
            ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2023.png)
            
        2. F $\oplus$ LE$_0$
            
            ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2024.png)
            
        3. SW
            
            ![Untitled](CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard%20d4c046a2d7ff4c3f812b3c6a3092ce70/Untitled%2025.png)
            
    3. Round 2
        1. F function
            
            ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2026.png)
            
        2. F $\oplus$ LE$_1$
            
            ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2027.png)
            
        3. $IP^{-1}$
            
            ![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2028.png)
            

## 1) DES Encryption

![Untitled](./CH04%20Block%20Cipher%20and%20The%20Data%20Encryption%20Standard/Untitled%2029.png)