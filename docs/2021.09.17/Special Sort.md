# 2021.09.17 (금요일)
### **2. Special Sort(구글 인터뷰)**

Q. N개의 정수가 입력될 때, 입력된 정수를 정렬하여라. 
   단 , 음의정수는 앞쪽에 위치해야 하고 양의정수는 뒷쪽에 위치해야 한다.
   또한 양의정수와 음의정수의 순서에는 변함이 없도록 해 주어야 한다.

#### -  접근방법
1. 음의정수와 양의정수일 경우를 나누어서 구분해준다.

**<나의풀이>**
```javascript
<html>
    <head>
        <meta charset="UTF-8">
        <title>출력결과</title>
    </head>
    <body>
        <script>
          function solution (arr){
            let answer = arr;
            for(let i = 0; i < arr.length-1; i++) {
              if(arr[i] < 0) {
                for(let j = 0; j < arr.length-i-1; j++) {
                  arr[i] = arr[j];
                }
              } else {
                  for(let j = 0; j < arr.length-i-1; j++) {
                    [arr[j],arr[j+1]] = [arr[j+1],arr[j]];
                  }
                }
            }
            return answer;
           }
           let arr = [1, 2, 3, -3, -2, 5, 6, -6];
           console.log(solution(arr)); 
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
          function solution (arr) {
            let answer = arr;
            for(let i = 0; i < arr.length -1; i++) {
              for(let j = 0; j <arr.length-i-1; j++) {
                if(arr[j] > 0 && arr[j+1] < 0) {
                  [arr[j],arr[j+1]] = [arr[j+1],arr[j]];
                }
              }
            }
            return answer;
          }
          let arr = [ 1, 2, 3, -3, -2, 5, 6, -6];
          console.log(solution(arr));
        </script>
    </body>
</html>
```

---
##  **🔥 새로 배운 내용 & 느낀 점**
    1. 나의 풀이에서 음수와 양수를 비교하는 과정에서 음수 양수를 나누고 , 또 다시 음수와 양수로 나눈 
      수의 앞뒤를 한번 더 바꾸어 줄려고 해서 틀렸다. // 근데 나의 의도대로 구현한 코드도 틀린 풀이방법인것 같다.
       순서를 바꾸지 말라는 문제의 조건을 간과한 풀이였다.