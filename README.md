알고리즘 스터디

#### 최솟값 구하기

* Number.MAX_SAFE_INTEGER : 아주 큰 정수 값(안정적인)으로 초기화 시키기 
* 큰 정수 값을 넣어 놓고서 for(i=0; i<arr.length; i++) 반복문 돌리기

* ... 전개 연산자(spread operator) : 배열 또는 객체를 하나하나 넘기는 용도
* answer에 배열로 값을 넣기 위해서는 push를 사용한다.
* 카운팅을 하려면 answer=0으로 만들어준다

#### for ... of

* 반복가능한 객체에 대해서 반복하고 각 개별 속성값에 대해 실행되는 문이 있는 사용자 정의 반복 후크를 호출하는 루프를 생성
  * ex) for(const x of arr)

#### forEach, map, filter, reduce (고차원 함수)

* arr.forEach(함수를 받음, ) 호출하는 것 / for 문 대신에 사용

```javascript
arr = [10, 11, 12, 13, 14];
arr.forEach((v, i) => {console.log(v, i, this)}, [1, 2]);
// 콜백 함수 안의 this는 뒤에 적용한 [1,2]
// v는 인덱스의 값 i index 번호
// 출력 10 0 / 11 1 / 12 2 ...
```

* map 요소들을 하나씩 확인하면서 새로운 배열을 생성한다. 만약 조건을 주고 그 조건에 맞지 않으면 값이 undefined로 넘어간다.

```javascript
arr = [10, 11, 12, 13, 14];
let answer = arr.map((v, i) => {
  return v*v
}, [1, 2]);
console.log(answer);
// v는 넘어가는 원본 배열
// 출력 [100, 121, 144 ...]

let answer = arr.map((v, i) => {
  if(v%2 === 0) return v;
}, [1, 2]);
console.log(answer);
// return 한 부분을 넘기는데 원본 배열과는 길이가 동일하여 조건에 맞지 않으면 undefined를 출력에 나온다
// 출력 [100, undefined, 144 ...]
```

* filter는 새로운 배열을 생성하여 return한다.
* 조건에 맞는 배열만 뽑아낸다. 새로운 값을 만들지 않음

```javascript
arr = [10, 11, 12, 13, 14];
let answer = arr.filter((v, i) => {
 return v%2 === 0;
}, [1, 2]);
console.log(answer);
// 조건이 참인 부분만 return 배열에 나온다
// 원본 배열의 값이 변하지 않고 조건에 맞는 배열만 출력이 된다.
// 출력 [10, 12, 14]
```

* reduce 배열을 생성하는 것이 아닌 하나의 값을 생성한다,
  * let sum = arr.reduce((a, b) => a+b , 0) 0은 a의 초기 값

```javascript
arr = [1, 2, 3, 4, 5];
let answer = arr.reduce((acc, v) => {
 return acc+v;
}, 0);
console.log(answer);
// 0은 초기화 하는 값을 넣어준다.
// acc는 누적 되는 값, v는 원본 배열의 값
// return은 배열이 아닌 값이 출력
// 출력 15
```

#### splice 배열안에 값을 제거

* arr.splice(i , 1) i에 값 1개 제거
* 이중 for문으로 제거를 할 때 뒷 배열 부터 제거 하자

#### 문자열 탐색

* replace(/A/g, '#') 스트링은 주소 복사가 아닌 값이 복사되어 사용하면 그 값이 들어가 변경이 되지 않는다 .
* split 구분자로 빠져서 앞뒤로 나온다. 길이를 구하러면 길이 -1을 사용
* toUpperCase() : 대문자로 바꾸기
* charCodeAt : 아스키코드로 변경한다.

#### indexOf

* 중복된 값을 제거
* 문자열을 찾는데 index번호로 찾아준다.
* indexOf('k', 1)을 예시로 하면 1번 인덱스 이후 부터 찾아라

---

문제를 풀때는 기준을 잡아서 진행을 해야한다

#### Array.from({length: n} , () => 1)

* 앞에는 인덱스 수를 정해준다, 뒤에는 콜백 함수를 사용하여 모든 인덱스에 1을 넣어준다.

#### Set 함수를 사용 후에 배열로 변환하는 것을 Array.from말고 [...new Set(arr)]!!!

#### 4방향을 탐색

* 2중 for문을 사용하며 x, y축으로 확인을 한다.
* dx=[-1, 0, 1, 0], dy=[0, 1, 0, -1]로 지정하여 2중 for문 안에서 한번더 돌려서 4방향 확인을 한다

---

#### 회문 문자열 탐색

* 앞에서 읽을 때, 뒤에서 읽을 때 같은 문자열을 회문 문자열이라 한다,
* 빈 문자열로 split을 하면은 모든 문자열이 다 따로 나온다
* reverse() 모든 문자열을 뒤집어 준다.
* join(' ') 은 배열로 모든 문자열이 나눠진 것을 다시 스트링으로 묶어준다.

#### 정규식

* /^a-z/g, 모든 문자가 소문자가 아닐 때를 표현

#### isNaN

* 숫자가 아닌지를 확인 가능
* 숫자 확인을 하고 싶으면 !isNaN() 을 사용

#### parseInt

* 숫자에 000208 이런 부분을 208로 변경

#### 문자거리 문제

양쪽에서 기준을 잡고서 증가할 수 있도록

---

#### toString

* 숫자를 스트링으로 변환하려 split
* 스트링을 그냥 합치면 안되서 Number로 변환을 해줘야 한다.

#### isPrime

* 소수 인지 확인하는 함수를 만든다

```javascript
function isPrime(num){
  if(num === 1){
    return false;
  }
  for(let i=2; i<= Math.sqrt(num); i++){
    if(num%i === 0) return false;
  }
  return true;
}

function primecheck(n){
    for(var i=2;i<=Math.sqrt(n);i++){
        if(n%i == 0){
            return false;
        }
    }
    return true;    
}
```

#### getDivisor

```javascript
function getDivisot (n) {
  let arr = [];
  for(var i=1;i<=Math.sqrt(n);i++){
    if(n%i === 0){
      arr.push(i);
      if(n/i!=i) arr.push(n/i)
    }
  }
  return arr
}
```



#### Set

* 중복된 자료를 제거하는 함수 
* new Set()을 한 부분에서는 바로 sort함수 사용이 불가능 하다. 그렇기 때문에 Array.from을 사용하여 배열로 변환하고 sort함수를 사용하여야 한다.

#### 두 배열 합치기

* two pointers algorism을 사용한다.

#### 행렬의 덧셈

* 각 자리의 수를 각자 더해서 다시 넣어준다.

```javascript
function solution(arr1, arr2) {
    var answer = [];
    
   for(let i=0; i<arr1.length; i++){ 
       let temp = []; 
       for(let j=0; j<arr1[i].length; j++){
           temp.push(arr1[i][j] + arr2[i][j]);
       } 
       answer.push(temp) 
   }
    return answer;
}
```

#### 배열 안에 수를 더하기 위해서는 reduce함수를 사용!!!!

---

#### 배열 안의 값을 정렬하여 가장 큰 값을 뽑아낸디

```javascript
function solution(numbers) {
    var answer = numbers.map(v=>v+'')
                        .sort((a,b) => (b+a)*1 - (a+b)*1)
                        .join('');

    return answer[0]==='0'?'0':answer;
}
```

