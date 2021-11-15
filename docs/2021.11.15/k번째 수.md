# 2021.11.15 (월요일)
### **2. k번째 수**

Q. N개의 숫자로 이루어진 숫자열이 주어지면 해당 숫자열중에서 s번째부터 e번째 까지의 수를 
   오름차순 정렬했을 때 k번째로 나타나는 숫자를 출력하는 프로그램을 작성하세요


#### -  접근방법

1. list를 만들어 slice를 사용해 결과를 출력해준다.

**<풀이 코드>**
```python
import sys
sys.stdin = open("input.txt", "rt")
T = int(input())
for t in range(t):
    n, s, e, k = map(int, input().split())
    a = list(map(int, input().split()))
    a = a[s-1:e]
    a.sort()
    print("#%d %d" %(t+1, a[k-1]))

          
   
```


---
##  **🔥 새로 배운 내용 & 느낀 점**
    
    1. slice란? 
    - 기본형태
    => a 라는 연속적인 객체들의 자료구조 (예: 리스트, 튜플, 문자열)가 있다고 가정할 때,
       기본형태는 아래와 같다.
       
       => a[start:end:step]
    
    - start, end, step 모두 양수와 음수를 가질 수 있다.
    - start: 슬라이싱을 시작할 시작 위치이다.
    - end : 슬라이싱을 끝낼 위치로 end는 포함하지 않는다.
    - step : stride(보폭)라고도 하며 몇개씩 끊어서 가져올지와 방향을 정합니다. 
             옵션이며 아래의 예제를 확인하면 쉽게 이해가 가능하다.

    
    
  