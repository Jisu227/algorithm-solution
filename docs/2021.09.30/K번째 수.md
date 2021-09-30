# 2021.09.29 (수요일)
### **1. K번째 수**

Q. 배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 한다.
   예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면
   1. array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3] 된다.
   2. 1에서 나온 배열을 정렬하면 [2, 3, 5, 6] 가 된다.
   3. 2에서 나온 배열의 3번째 숫자는 5다.
   배열 array, [i, j, k]를 원소로 가진 2차원 배열 commands가 매개변수로 주어질 때,
   commands의 모든 원소에 대해 앞서 설명한 연산을 적용했을 때 나온 결과를 배열에 담아 출력하여라.

#### -  접근방법

1. 일단 2차원 배열의 index 번호를 살펴 보았다. 
   문제에서 말하는 i 에 해당하는 index 번호는 commands[0][0],commands[1][0],commands[2][0]이고,
   j 에 해당하는 index는 commands[0][1],commands[1][1],commands[2][1]
   k 에 해당하는 index는 commands[0][2],commands[1][2],commands[2][2] 라는 것을 알게 되었다.
   i 에서는 행의 길이에서 0 이고정되고, j에서는 1, k에서는 2가 고정된다는 사실을 알게되었다.
   따라서 열의 길이는 0,1,2로 반복되기 때문에 for문을 이용하여 풀이해 주었다.
   
2. 이후 배열의 요소를 자를 수 있는 메서드인 slice를 이용하였다. 
 
**<나의풀이>**
```javascript
<html>
    <head>
        <meta charset="UTF-8">
        <title>출력결과</title>
    </head>
    <body>
        <script>
            function solution (array,commands) {
              let answer = [];
              for(let i = 0; i < commands.length; i++) {
                let arr = array.slice(commands[i][0]-1,commands[i][1]);
                arr.sort();
                answer.push(arr[commands[i][2]-1]);
              }
              return answer;
            }
            let arr = [1, 5, 2, 6, 3, 7, 4];
            let commands = [[2, 5, 3], [4, 4, 1], [1, 7, 3]];
            console.log(solution(arr,commands));
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
           function solution (array,commands) {
             let answer = [];
             commands.forEach((command)=> {
               let arr = array.slice(command[0] - 1, command[1]).sort(function(a,b) {
                 return a-b;
               });
               answer.push(arr[command[2]-1]);
             })
             return answer;
            }
            let arr = [1, 5, 2, 6, 3, 7, 4];
            let commands = [[2, 5, 3], [4, 4, 1], [1, 7, 3]];
            console.log(solution(arr,commands));
        </script>
    </body>
</html>
```

**<다른 풀이 2번>**
```javascript
<html>
    <head>
        <meta charset="UTF-8">
        <title>출력결과</title>
    </head>
    <body>
        <script>
           function solution (array,commands) {
             let answer = [];
             for(let i = 0; i < commands.length; i++) {
               const [a,b,c] = commands[i]; // 구조 분해 할당
               const arr = array.slice(a-1,b);
               arr.sort((a,b)=> a-b);
               answer.push(arr[c-1]);
             }
             return answer;
            }
            let arr = [1, 5, 2, 6, 3, 7, 4];
            let commands = [[2, 5, 3], [4, 4, 1], [1, 7, 3]];
            console.log(solution(arr,commands));
        </script>
    </body>
</html>
```

---
##  **🔥 새로 배운 내용 & 느낀 점**

    1. 나의 풀이를 보면 Array.slice를 해주고 그것을 새로운 변수인 arr에 담아 주었는데 , 
      그 이유는 slice 메서드 자체가 원본을 수정해주는 메서드가 아니기 때문이다.
      그 특징을 간과한 채 변수에 담지않고 slice를 해주었더니 수정되지 않은 메서드가 출력되었다.
      이번기회로 인해서 slice 메서드 사용방법을 제대로 익힌 것 같아서 뿌듯했다.
      그리고 ,정답을 제출했을 때 계속 하나의 테스트에서만 실패했는데 그 이유는 정렬 때문이었다.
      js는 compareFunction 이 제공되지 않으면 유니코드 포인터 순서로 문자열을 비교하여 정렬한다.
      이 문제에서는 문자열 비교가 아닌 숫자를 비교해야되므로 정렬 순서를 꼭 정의해 주어야 한다. 

    2. 다른 풀이 1번에서는 forEach를 사용하여 풀이해 주었다.
       forEach문은 입력받은 배열의 길이만큼 반복한다.

    3. 다른 풀이 2번에서 참신 했던 점은 구조 분해 할당을 사용했다는 점이다.
      
