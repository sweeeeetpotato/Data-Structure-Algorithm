<연습 문제>

## 문제 설명
대문자와 소문자가 섞여있는 문자열 s가 주어집니다. s에 'p'의 개수와 'y'의 개수를 비교해 같으면 True, 다르면 False를 return 하는 solution를 완성하세요. 'p', 'y' 모두 하나도 없는 경우는 항상 True를 리턴합니다. 단, 개수를 비교할 때 대문자와 소문자는 구별하지 않습니다.

예를 들어 s가 "pPoooyY"면 true를 return하고 "Pyy"라면 false를 return합니다.

<br>

### 제한사항
* 문자열 s의 길이 : 50 이하의 자연수
* 문자열 s는 알파벳으로만 이루어져 있습니다.

<br>

### 입출력 예
|s|answer|
|:---:|:---:|
|"pPoooyY"|true|
|"Pyy"|false|

<br>

### 입출력 예 설명
입출력 예 #1   
'p'의 개수 2개, 'y'의 개수 2개로 같으므로 true를 return 합니다.

입출력 예 #2   
'p'의 개수 1개, 'y'의 개수 2개로 다르므로 false를 return 합니다.
<br>

---

<br>

## 내 답안
<첫 풀이>
```JavaScript
function solution(s){
    const p_count = s.match(/p/gi) ? s.match(/p/gi).length : 0;
    const y_count = s.match(/y/gi) ? s.match(/y/gi).length : 0;
    
    return p_count === y_count;
}
```
> * 정규표현식을 이용하여 풀이
> * match 함수는 인자에 포함된 문자를 찾으면 배열로 반환하는 함수인데, 문자를 찾지 못하면 null을 반환함
> * null은 false이므로 위와 같이 삼항연사자를 작성하였음
> * 생각보다 실행 속도가 느린 것을 보아 match 함수는 효율적이지는 않은 것 같음

<색다른 풀이>
```JavaScript
function solution(s){
    return s.toUpperCase().split("P").length === s.toUpperCase().split("Y").length;
}
```
> * 다른 분이 작성한 기발하고, 실행 속도가 빠른 풀이
> * 대소문자 구분없이 개수를 세야하므로 toUpperCase() 사용
> * split("P")/split("Y")를 할 때 문자를 기준으로 나누기 때문에 P/Y의 개수보다 1개 더 많이 분할됨. 
> * 예를들어 `"PPOOOYY".split("P")`를 하면 `['', '', 'OOOYY']`를 반환. P의 개수인 2개보다 1개 많은 3개의 요소가 생성됨
> * 하지만 이 문제는 개수를 반환하는 문제가 아니라 `'p'와 'y'의 개수의 일치 여부에 따른 boolean값을 반환하는 문제`이므로 효율적인 코드라 생각함