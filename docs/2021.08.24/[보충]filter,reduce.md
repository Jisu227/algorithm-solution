# [보충] filter ,reduce 메서드란?
-> forEach와 map과 같이 고차함수이다.
## *📌  filter 란?*
filter 또한 map과 마찬가지로 새로운 배열을 생성하여 return 받게 되는데 **map과는 다르게 새로 생성된 배열의 길이가 원본배열의 길이와 동일할 필요가 없다.** 정확하게 원하는 원소만 콜백함수가 return하여 생성해준다. 

filter의 원리를 살펴보자면 
콜백함수가 return 했을 때의 그 요소만 딱 새로운 배열의 원소로 저장되게 하는 것이다. 
```javascript
a = [10,11,12,13,14,15];
let answer = a.filter(function(v,i){
    return v % 2 === 0;
},[1,2]);
console.log(answer);
```
예를 들자면 , 여기에서 참인 요소는 **[10,12,14]** 가 되면서 새로운 배열의 요소로 들어가게 되는 것이다. 

### 정리해보자면 
    filter는 
    map 처럼 아에 새로운 요소들로 생성된 배열을 만드는 것이 아니라 
    원본 배열 중에서 참인 요소들로 이루어진 배열을 만들어 내는 것이다. 


---


## *📌  reduce란?*
```javascript
a = [10,11,12,13,14,15];
let answer = a.reduce(function (acc,v){
    return acc+v;
}, 0);
console.log(answer);
```
**출력 =>  75**

reduce 콜백함수의 구조는 앞서 배운 메소드 들과는 좀 다른데 , 
첫번째 인자는 누적하는 값이고 , 두번째 인자의 값이 value이다. 
value 는 원본배열의 인수들이 대응되는 값을 말한다. 

reduce()는 배열의 각 요소에 대하여 reducer 함수를 실행하고, map과 filter 와 달리 배열이 아닌 하나의 결과 값을 반환한다는 차이점이 있다. 

위의 코드는 **값을 계속 누적하여 갖고 있는 누산기인 acc와** 현재 요소인 v 를 매개변수로 하여 모든 요소의 합을 반환하는 로직이다. 

누산기라는 개념은 reducer 함수를 수행하면서 생기는 값을 임시적으로 보관하는 형태를 말한다. 

그리고 예시에서 사용한 매개변수를 포함하여 총 4개의 매개변수를 가지고 있다.

    1.accumulator : 리턴한 값을 저장하는 변수. 초기값을 지정한 경우에는 초기값 부터 시작.
    2. currentValue : 현재 요소.
    3. currentIndex : 요소의 인덱스.
    4. array : map()을 호출한 원본 배열

reduce() 함수는 위의 예시말고도 활용도가 높은 함수이기 때문에 다양한 목적으로 사용할 수 있다. 
활용방법은 [공식문서](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)에 자세하게 나와 있으니 참고하도록 하자.