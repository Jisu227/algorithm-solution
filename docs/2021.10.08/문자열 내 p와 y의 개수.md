# 2021.10.08 (금요일)
### **2. 문자열 내 p와 y의 개수**

Q. 대문자와 소문자가 섞여있는 문자열 s가 주어졌을때 s에 'p'의 개수와 'y'의 개수를 비교해 같으면 True,
   다르면 False를 return 하여라. 'p', 'y' 모두 하나도 없는 경우는 항상 True를 리턴한다.
   단, 개수를 비교할 때 대문자와 소문자는 구별하지 않는다.



#### -  접근방법

1. 대문자와 소문자를 구별하지 않기 때문에 toUpperCase() 메서드로 다 대문자로 변경시켜 준다. 
2. for문을 통해 문자열에 'P'와 'Y'가 있다면 count해주고 그 count 값을 비교한다.


**<나의풀이>**
```javascript
<html>
    <head>
        <meta charset="UTF-8">
        <title>출력결과</title>
    </head>
    <body>
        <script>
            function solution(str) {
              let pCount = 0, yCount = 0;
              str = str.toUpperCase();
              for(let i = 0; i < str.length; i++) {
                if(str[i] === "P") {
                  pCount ++;
                }
                if(str[i] === "Y") {
                  yCount ++;
                }
              }
              if(pCount === yCount) {
                return true;
              } else {
                return false;
              }
            }
            let str = 'pPoooyY'
            console.log(solution(str))
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
           function solution (s) {
               return s.toUpperCase().split("p").length === s.toUpperCase().split("Y").length;
           }
           let s = "pPoooyY"
           console.log(solution(s))
        </script>
    </body>
</html>
```



---
##  **🔥 새로 배운 내용 & 느낀 점**

    1. 다른 풀이 1번의 핵심에는 split()에 separator 를 줘서 나누면 리턴되는 배열의 길이를 비교해주는 것이다.
    