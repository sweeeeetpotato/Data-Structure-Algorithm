<연습문제>

## 문제 설명
JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다. 단, 첫 문자가 알파벳이 아닐 때에는 이어지는 알파벳은 소문자로 쓰면 됩니다. (첫 번째 입출력 예 참고)   
문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.

<br>

### 제한 조건
* s는 길이 1 이상 200 이하인 문자열입니다.
* s는 알파벳과 숫자, 공백문자(" ")로 이루어져 있습니다.
  * 숫자는 단어의 첫 문자로만 나옵니다.
  * 숫자로만 이루어진 단어는 없습니다.
  * 공백문자가 연속해서 나올 수 있습니다.

<br>

### 입출력 예
|s|return|
|:---:|:---:|
|"3people unFollowed me"|"3people Unfollowed Me"|
|"for the last week"|"For The Last Week"|

<br>

---

<br>

## 내 답안
<첫 풀이>
```JavaScript
function solution(s) {
    const wordArr = s.toLowerCase().split(" ");
    
    for (let i = 0; i < wordArr.length; i++) {
        wordArr[i] = wordArr[i].replace(/^[a-z]/, char => char.toUpperCase());
    }
    
    return wordArr.join(" ");
}
```
> * 중간에 대문자가 섞여있는 경우를 고려하여 우선 전부 소문자로 변경(toLowerCase())후 공백으로 split하여 단어를 분리하여 배열로 만듬
> * 정규표현식에서 `문자열의 시작을 판단`하는 조건인 캐럿(^)을 이용
> * 반복문과 정규표현식을 이용하여 각 단어의 첫번째 글자를 대문자로 변경후, 다시 공백으로 join하여 리턴

<리팩토링 풀이>
```JavaScript
function solution(s) {
    const newS = s.toLowerCase().replace(/\b[a-z]/g, char => char.toUpperCase());

    return newS;
}
```
> * 정규표현식에서 `\b`은 문자열에서 `단어가 경계에 있는지` 확인하는 역할
> * 각 단어의 첫글자를 대문자로 변경한 뒤 리턴