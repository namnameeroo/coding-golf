# coding-golf
- Archive JS-shortest-code-hack _(especially, [Clash-Of-Code](https://www.codingame.com/multiplayer/clashofcode))_

# Goal
- JavaScript로 shortest code 대회나 게임할 때 유리한 문법들을 수집해요. (for FUN)

# Clash-Of-Code
- Clash-Of-Code 는 온라인 알고리즘 대결 웹사이트입니다. 대결 모드는 크게 Fastest, Reverse, Shortest가 있습니다.
- 그 중에서도 가장 짧은 코드를 제출해야하는 Shortest 모드에 유리한 문법들을 수집해요.
- ~~그렇지 않으면, Ruby나 Python을 당해내지 못하거든요.~~


___
# 본문
## 입력
: Clash-Of-Code (이하 CoC)는 JS 입출력을 readline, print로 가능하도록 지원합니다. shortest에서는 적극 사용합니다만, 입력이 반복될 경우 이마저도 길게 느껴지므로 변수로 할당해 줄여봅니다.
  또한, 실무에서나, strict모드에서 필수적인 변수 선언 예약어도 shortest에서는 제거합니다.

* before
```JavaScript
const N = readline();
const M = readline();
```

* after
```JavaScript
r=readline;
N=r();
M=r();
```

## 문자에서 숫자로 형변환 (parseInt, Number)
: 주로, "123"을 숫자 123으로 변환하기 위해 parseInt나 Number를 사용합니다. 그러나 JS의 허점을 이용한다면 단 하나의 바이트(`+`)로 형변환이 가능합니다.

* 각 자리 수의 합을 구하는 예제
  * before
  ```JavaScript
    const StringNum = '123';
    const result = StringNum.reduce((acc,v)=>acc+parseInt(v),0);
    console.log(result);
  ```
  * after
  ```JavaScript
    const StringNum = '123';
    const result = StringNum.reduce((acc,v)=>+v+a),0);
    console.log(result);
  ```

## 영문 대문자 판별하기 (toUpperCase)
: 영문 대문자를 판별하는 방법은 toUpperCase값과 현재 값을 비교하거나 ASCII 코드 값의 범위를 확인하는 방법이 있습니다. 
  이를 짧게 표현하기 위해서는 **정규식**만한 것이 없네요!
  * before
  ```JavaScript
    const word = 'ASCii';
    const upperCase = [...word].map(v=> {
                        if (v.toUpperCase() == v) {
                          return v;
                        }
                      }).join('');
  ```
   * after
  ```JavaScript
    const word = 'ASCii';
    const upperCase = [...word].map(v=> v.match(/[A-Z]/g) && v ).join('');
  ```

## split과 join의 괄호 없애보기 : ()=> ``
* before
  ```JavaScript
    const sentence = 'I go to school';
    const words = sentence.split(' ');
  ```
* after
  ```JavaScript
    const sentence = 'I go to school';
    const words = sentence.split` `; // 인용부호 따옴표가 아닌 템플릿 리터럴 쓸 때 사용하는 "백틱"입니다.
  ```
