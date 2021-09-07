# 2021.09.07 (화요일)
### **2. k번째 큰수**

Q. 1부터 100까지 자연수가 적힌 N장의 카드가 있다. 같은 숫자의 카드가 여러장 있을 수 있다.
    이중 3장을 뽑아 각 카드에 적힌 수를 합한 값을 기록하려고 할 때 , 3장을 뽑을 수 있는
    모든 경우를 기록한다. 기록한 값 중 K번째로 큰 수를 출력하라.


#### -  접근방법
1. 카드와 , k(k번째 큰 값을 위한)를 입력받는다. 
2. 3장을 뽑을 수 있는 모든 경우의 수를 구하고, 그 3장의 합을 구해 임시 배열에 넣어준다.
3. 그 3장의 합을 구한 배열을 합이 큰 것부터 나열한다. 
4. 그 중 k 번째로 큰 수를 출력한다.


**<나의풀이>**
```javascript
<html>
    <head>
        <meta charset="UTF-8">
        <title>출력결과</title>
    </head>
    <body>
        <script>
            function solution(card,s) {
              let answer ,tmp=[];
              let n = card.length;
              card.sort((a,b)=>a-b)
              for(let i = 0; i < n; i++) {
                for(let j = i+1; j < n; j++){
                  tmp.push(card[i]+card[j]+card[j+1]);
                }
              }
              tmp.sort((a,b)=>b-a)
              answer = tmp[s-1];
              return answer;
            }
            let arr = [13 ,15 ,34 ,23 ,45 ,65 ,33 ,11 ,26 ,42];
            console.log(solution(arr,3));
        </script>
    </body>
</html>
```


**<다른 풀이>**
```javascript
<html>
    <head>
        <meta charset="UTF-8">
        <title>출력결과</title>
    </head>
    <body>
        <script>
            function solution (n,k,card) {
              let answer ;
              let tmp= new Set();
              for(let i = 0; i<n; i++) {
                for(let j= i+1; j<n; j++){
                  for(let k = j+1; k<n; k++){
                    tmp.add(card[i]+card[j]+card[k]);
                  }
                }
              }
              let a= Array.from(tmp).sort((a,b)=>b-a);
              answer=a[k-1];
              return answer;
            }
            let arr = [13, 15, 34, 23, 45, 65, 33, 11, 26, 42];
            console.log(solution(10,3,arr));
        </script>
    </body>
</html>
```

---
##  **🔥 새로 배운 내용 & 느낀 점**
    1. new Set() 이란?
    => Set 객체는 중복되지 않는 유일한 값들의 집합이다.

    - Set 객체의 특징
     a. 동일한 값을 중복하여 포함할 수 없다.
     b. 요소 순서에 의미가 없다.
     c. 인덱스로 요소에 접근할 수 없다.
    
    - Set 객체는 수학적 집합을 구현하기위한 자료구조이다.
    => 따라서, set을 통해 교집합,차집합,합집합,여집합 등을 구할 수 있다.
 