# 2021.09.18 (토요일)
### **2. Least Recently Used(카카오 캐시 문제 변형)**
Q. 캐시 메모리는 CPU 와 주기억장치(DRAM) 사이의 고속의 임시 메모리로서 CPU가 처리할 작업을 저장해 놓았다가 필요할 때 , 바로 사용해서 처리속도를 높이는 장치이다.
사용해야 할 컴퓨터는 캐시메모리 사용 규칙이 LRU 알고리즘을 따르는데, LRU 알고리즘은 Least Recently Used 약자로 직역하면 가장 최근에 사용되지 않은 것 정도의 의미를 가지고 있다. 캐시에서 작업을 제거할 때 가장 오랫동안 사용하지 않은 것을 제거하겠다는 알고리즘이다. 

예를 들어 캐시의 사이즈는 5이고 작업이 2-3-1-6-7 순으로 저장되어 있다. 

1. Cache Miss : 해야할 작업이 캐시에 없는 상태로 위 상태에서 만약 새로운 작업인 5번 작업을 CPU 사용한다면 Cache Miss가 되고 모든 작업이 뒤로 밀리고 5번작업은 캐시의 맨앞에 위치한다.

2. Cache Hit : 해야할 작업이 캐시에 있는 상태로 위 상태에서 만약 3번 작업을 CPU가 사용한다면 Cache Hit 가 되고, 앞에 있는 5,2 번 작업은 한칸 뒤로 밀리고 , 3번이 맨앞에 위치 하게 된다.

캐시의 크기가 주어지고, 캐시가 비어있는 상태에서 N개의 작업을 CPU가 차례로 처리한다고 하면 N개의 작업을 처리한 후 캐시 메모리의 상태를 가장 최근 사용된 작업부터 차례대로 출력하는 프로그램을 작성하라.


#### -  접근방법
1. for문으로 탐색하여 같은 숫자가 push 되면 이미 안에 들어있는 숫자는 제거하여 준다.
2. 자리 5개가 다 차면 제일 먼저 들어온 값은 제거해준다.

**<나의풀이>**
```javascript
<html>
    <head>
        <meta charset="UTF-8">
        <title>출력결과</title>
    </head>
    <body>
        <script>
          function solution (n,arr) {
            let answer ;
            let queue = Array(n);
            for(let x of arr) {
              queue.push(x)
              if(queue.includes(x)) {
                queue.push(x)
                queue.shift(queue.includes(x));
              } else if(queue.length === n) {
                queue.shift();
              }
            }
            return answer;
          }
          let arr = [1,2,3,2,6,2,3,5,7];
          console.log(solution(5,arr));
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
          function solution(size,arr) {
            let answer = Array.from({length:size}, () => 0);
            arr.forEach(x => {
              let pos = -1;
              for(let i = 0; i < size; i++) if(x===answer[i]) pos = i;
                if(pos === -1) {
                for(let i  = size -1; i>=1; i--){
                  answer[i]=answer[i-1];
                }
                } else {
                for(let i = pos; i>=1; i--) {
                  answer[i]=answer[i-1];
                }
               }  
                answer[0]=x;
            });
            return answer;
          }
          let arr = [1,2,3,2,6,2,3,5,7];
          console.log(solution(5,arr));
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
          function solution(size,arr) {
            let answer = [];
            arr.forEach(x => {
              let pos = -1;
              for(let i = 0; i < size; i++) if(x===answer[i]) pos=i;
              if(pos=== -1) {
                answer.unshift(x);
                if(answer.length>size) answer.pop();
              }
              else {
                answer.splice(pos,1);
                answer.unshift(x);
              }
            });
            return answer;
          }
          let arr = [1,2,3,2,6,2,3,5,7];
          console.log(solution(5,arr));
        </script>
    </body>
</html>
```


---
##  **🔥 새로 배운 내용 & 느낀 점**
    1. 첫번째 풀이 방법은 삽입 정렬을 이용하여 풀이한 방법이다.
       코드 구현력을 위하여 이 방법으로도 코드를 구현할 수 있어야 한다.

    2. 두번째 풀이 방법은 내장함수 를 이용하여 풀이해 주었다.
       내장함수 unshift(), slice() 를 이용한다.
    
    - unshift() 란 ?
    => unshift 메서드는 새로운 요소를 배열의 맨 앞쪽에 추가하고, 새로운 길이를 반환한다.

    