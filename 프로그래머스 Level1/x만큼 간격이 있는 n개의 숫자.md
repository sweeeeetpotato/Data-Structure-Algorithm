<연습문제>

## 문제 설명
함수 solution은 정수 x와 자연수 n을 입력 받아, x부터 시작해 x씩 증가하는 숫자를 n개 지니는 리스트를 리턴해야 합니다. 다음 제한 조건을 보고, 조건을 만족하는 함수, solution을 완성해주세요.

<br>

### 제한사항
* x는 -10000000 이상, 10000000 이하인 정수입니다.
* n은 1000 이하인 자연수입니다.

<br>

### 입출력 예
|x|n|answer|
|:---:|:---:|:---:|
|2|5|[2,4,6,8,10]|
|4|3|[4,8,12]|
|-4|2|[-4, -8]|

<br>

---

<br>

## 내 답안
<내 풀이>
```JavaScript
function solution(x, n) {
    const arr = [];
    
    for (let i = 1; i <= n; i++) {
        arr.push(x * i);
    }
    
    return arr;
}
```
> * `arr.push(x * i)`대신에 `arr[i-1] = x * i`도 가능
> * 사실 push보다는 오른쪽방식이 더 실행속도가 빠름

<리팩토링 풀이>
```JavaScript
function solution(x, n) {
    return Array(n).fill(x).map((val, index) => val * (index+1));
}
```
> * `Array(n).fill(x)` : n개의 원소를 가진 배열을 생성하는데, n개의 원소는 x값으로 채워져있음
> * 전부 같은 값으로 이루어져있는 배열 원소들을 (인덱스 + 1)로 곱하면 원하는 답이 나옴