# 스코프
## 스코프란?

**변수는 자신이 선언된 위치에 의해 자신이 유효한 범위, 즉 다른 코드가 변수 자신을 참조할 수 있는 범위가 결정된다.** 이 범위를 스코프(Scope, 유효범위)라 한다.

- 전역 스코프
  - 전역에서 선언된 변수는 전역 스코프를 가진다.
- 지역 스코프
  - `var` 키워드로 선언한 변수는 함수 몸체 내부를 지역 스코프로 가지고, `let`이나 `const`로 선언한 변수는 블록 내부를 스코프로 가진다.

## 블록레벨 스코프

if, for 문을 포함한 모든 블록`{}` 의 내부에서 선언된 변수는 그 블록을 지역 스코프로 가지는 것

## 함수레벨 스코프

다른 블록이 아닌, 함수 블록 내부에서 선언된 변수만이 지역 스코프를 가지는 것

# 스코프 체인이란?

스코프의 계층적인 구조. 코드의 중첩에 의해서 만들어진다. 전역이 최상위 스코프이고, 지역 스코프는 하위 스코프이다. 스코프는 중첩될 수 있으며 중첩 관계가 스코프 체인의 계층을 만든다.

## 지역 스코프가 변수를 검색하는 과정

처음은 자기가 속한 스코프에서 변수를 찾고, 없을 경우 스코프 체인을 따라 상위 스코프로 이동하며 검색한다. 전역변수에도 해당 변수가 없을 경우 선언되지 않은 변수를 참조했으므로 ReferenceError가 발생한다.

# 동적 스코프와 정적 스코프

스코프를 언제 결정할지에 대한 방법

## 동적 스코프

식별자가 호출되는 위치로 스코프를 결정한다. 스코프가 어떻게 결정될지 예측할 수 없다.

## 정적 스코프 (Lexical Scope)

식별자가 선언된 위치로 스코프를 결정한다. 스코프가 변하지 않아 결과를 예상할 수 있다.

# 암묵적 전역변수

밑 코드의 결과는 둘 다 10

`var` 키워드 없이 변수를 선언해 x가 암묵적으로 전역변수로 선언되었기 때문에 전역 스코프를 가진다. 그래서 어디에서나 x를 참조할 수 있게 된다.

```javascript
function foo() {
  x = 10;
}
foo();
console.log(x);
```