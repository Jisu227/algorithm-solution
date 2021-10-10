# 2021.10.10 (일요일)
### **1. x만큼 간격이 있는 n개의 숫자**

Q. 함수 solution은 정수 x와 자연수 n을 입력 받아, x부터 시작해 x씩 증가하는 숫자를 n개 지니는 리스트를 리턴해야한다. 
   다음 제한 조건을 보고, 조건을 만족하는 함수, solution을 완성해주세요.


#### -  접근방법

1. for문을 이용하여 쉽게 구현해 주었다.

**<나의풀이>**
```javascript
<html>
    <head>
        <meta charset="UTF-8">
        <title>출력결과</title>
    </head>
    <body>
        <script>
          function solution(x, n) {
            let answer = [],tmp = 0;
            for(let i = 0; i < n; i++) {
              tmp += x;
              answer.push(tmp);
            }
            return answer;
          }
          console.log(2,5)
        </script>
    </body>
</html>
```

**<다른 풀이 1번>**
```javascript
<html>
    <head>
        <meta charset="UTF-8">
        <title>출력결과</title>
    </head>
    <body>
        <script>
           funtion solution(x,n) {
             return Array(n).fill(x).map((v,i)=>(i+1)*v);
           }
           console.log(2,5)
        </script>
    </body>
</html>
```


---
##  **🔥 새로 배운 내용 & 느낀 점**

    1. 다른 풀이 1번은 내가 구현한 for문 보다 성능은 떨어지지만, 
       훨씬 짧게 코드를 구현할 수 있다는 장점이 있었다.
