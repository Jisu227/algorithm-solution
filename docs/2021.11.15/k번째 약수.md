# 2021.11.15 (월요일)
### **1. k번째 약수**

Q. 어떤 자연수 p와 q가 있을 때, 만일 p를 q로 나누었을 때 나머지가 0이면 q는 p의 약수이다.
   두 개의 자연수 N과 K가 주어졌을 때, N의 약수들 중 K번째로 작은 수를 출력하는 프로그램을 작성하시오.


#### -  접근방법

1. for - else 문을 사용한다.

**<풀이 코드>**
```python
import sys
sys.stdin = open("input.txt", "rt")
n, k = map(int, input().split())
cnt = 0
for i in range(1, n+1):
    if n%i == 0 :
        cnt += 1
    if cnt == k :
        print(i)
        break
else print(-1)

          
   
```


---
##  **🔥 새로 배운 내용 & 느낀 점**

    1. import sys
       sys.stdin = open("input", "rt") 는 입력을 받기 위한 코드이다.

    2. 옆으로 띄어쓰기를 하고 들어온 코드는 map이라는 함수로 읽어 주어야 한다.  

    3. for - else 
    => for와 함께 쓰이는 else는 , for문이 중간에 break등으로 끊기지 않고 ,
       끝까지 수행되었을 때 수행하는 코드를 담고 있다.

    
  