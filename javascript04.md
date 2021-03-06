**함수** : 함수 이름으로 호출하는 것이 아니라 함수 객체를 가리키는 식별자로 호출한다. 자바스크립트의 함수는 객체 타입의 값이다.

 **함수선언문** : 함수 이름을 생략할 수 없다. 표현식이 아닌 문이다.

```
function add(x, y) {  
return x + y; 
}
```

**함수 표현식** : 함수 리터럴로 생성한 함수 객체를 변수에 할당할 수 있다. 함수 이름을 생략할 수 있다.

```
var sub = function (x ,y) {
	return x - y;
};
```

모든 선언문이 그렇듯 함수 선언문도 런타임 이전에 먼저 실행된다. 함수 표현식은 변수에 할당되는 값이 함수 리터럴인 문이다. 따라서 함수 표현식은 변수 선언문과 변수 할당문을 한번에 기술한 축약 표현이다. 변수 선언은 런타임 이전에 실행되어 undefined로 초기화되지만 변수 할당문의 값은 할당문이 실행되는 시점, 즉 런타임에 평가되므로 함수 표현식의 함수 리터럴도 할당문이 실행되는 시점에 평가되어 함수 객체가 된다.

따라서 함수 표현식으로 함수를 정의하면 함수 호이스팅이 발생하는 것이 아닌 변수 호이스팅이 발생하게 된다.

**화살표 함수** : ES6에서 새롭게 도입된 화살표 함수는 function 키워드 대신 화살표를 사용해 좀 더 간략한 방법으로 함수를 선언할 수 있다.

```
//일반적인 함수 표현식

var sub = function (x ,y) {
	return x + y;
};

//화살표 함수

const add = (x,y) => x + y;
```

**매개변수와 인수** : 함수를 실행하기 위해서는 필요한 값을 함수 외부에서 함수 내부로 전달해야한다. 매개변수(parameter,인자)를 통해 인수(argument)를 전달한다. 인수는 값으로 평가될 수 있는 표현식이어야 한다.

```
// 함수 선언문
function add(x, y) {
	return x + y;
}

// 함수 호출
// 이 때 1과2는 인수 , x와y는 매개변수이다. 인수는 매개변수에 순서대로 할당되고 함수 몸체의 문들이 실행된다.
var result = add(1, 2);
```

매개변수는 함수를 정의할 때 선언하며 함수 몸체 내부에서 변수와 동일하게 취급된다. 즉, 함수가 호출되면 함수 몸체 내에서 암묵적으로 매개변수가 생성되고 일반 변수와 마찬가지로 undefined로 초기화된 이후 인수가 순서대로 할당된다. 



**반환문** : 함수는 return 키워드와 표현식(반환값)으로 이루어진 반환문을 사용해 실행 결과를 함수 외부로 반환할 수 있다.

```
function multiply(x, y) {
	return x * y;  //반환문
}

// 함수 호출은 반환값으로 평가된다.
var result = multiply(3, 5);
console.log(result); //15
```

반환문은 두 가지 역할을 한다.

1. 반환문은 함수의 실행을 중단하고 함수 몸체를 빠져나간다. 따라서 반환문 이후에 다른 문이 존재하면 그 문은 실행되지 않고 무시된다.
2. 반환문은 return 키워드 뒤에 오는 표현식을 평가해 반환한다. return 키워드 뒤에 반환값으로 사용할 표현식을 명시적으로 지정하지 않으면 undefined가 반환된다.

**즉시실행함수** : 함수 정의와 동시에 즉시 호출되는 함수를 즉시 실행 함수라고한다. 즉시 실행 함수는 단 한 번만 호출되며 다시 호출할 수 없다.

```
// 익명 즉시 실행 함수
(function () {
	var a = 3;
	var b = 5;
	return a * b;
}());
```

즉시 실행 함수는 함수 이름이 없는 익명 함수를 사용하는 것이 일반적이다.

**재귀 함수** : 함수가 자기 자신을 호출하는 것을 재귀 호출이라 한다. 재귀 함수는 자기 자신을 호출하는 행위, 즉 재귀 호출을 수행하는 함수를 말한다.

```
function countdown(n) {
	if (n < 0) return;
	cosole.log(n);
	countdown(n - 1);  //재귀 호출
}

countdown(10);  //10부터 0까지 출력하는 함수
```



재귀 함수를 사용하면 팩토리얼을 간단하게 구현할 수 있다.

```
// 팩토리얼(계승)은 1부터 자신까지의 모든 양의 정수의 곱이다.
// n! = 1 * 2 * ... * (n - 1) * n
function factorial(n) {
	//탈출 조건: n이 1 이하일 때 재귀 호출을 멈춘다.
	if (n <= 1) return 1;
	// 재귀 호출
	return n * factorial(n - 1);
}


console.log(factorial(3)); // 3! = 3 * 2 * 1 = 6
console.log(factorial(4)); // 4! = 4 * 3 * 1 * 1 = 24
console.log(factorial(5)); // 5! = 5 * 4 * 3 * 2 * 1 = 120
```

재귀 함수는 자신을 무한 재귀 호출한다. 따라서 재귀 함수 내에는 재귀 호출을 멈출 수 있는 탈출 조건을 반드시 만들어야 한다.



**중첩 함수** : 함수 내부에 정의된 함수를 중첩 함수 또는 내부함수라고 한다. 일반적으로 중첨 함수는 자신을 포함하는 외부 함수를 돕는 헬퍼 함수의 역할을 한다.

```
function outer() {
	var x = 1;
	
	//중첩 함수
	function inner() {
		var y = 2;
		//외부 함수의 변수를 참조할 수 있다.
		console.log(x + y); //3
	}
	
	inner();
}

outer();
```

 

**콜백함수** : 

```
// n만큼 어떤 일을 반복한다
function repeat1(n) {
  // i를 출력한다.
  for (var i = 0; i < n; i++) console.log(i);
}

repeat1(5); // 0 1 2 3 4

// n만큼 어떤 일을 반복한다
function repeat2(n) {
  for (var i = 0; i < n; i++) {
    // i가 홀수일 때만 출력한다.
    if (i % 2) console.log(i);
  }
}

repeat2(5); // 1 3
```

위 예제의 함수들은 반복하는 일은 변하지 않고 공통적으로 수행하지만 반복하면서 하는 일의 내용은 다르다. 즉, 함수의 일부분만이 다르기 때문에 매번 함수를 새롭게 정의해야 한다. 이 문제는 함수를 합성하는 것으로 해결할 수 있다. 함수의 변하지 않는 공통 로직은 미리 정의해 두고, 경우에 따라 변경되는 로직은 추상화해서 함수 외부에서 함수 내부로 전달하는 것이다.






**스코프** : 모든 식별자(변수 이름, 함수 이름, 클래스 이름)는 자신이 선언된 위치에 의해 자신이 유효한 범위, 즉 다른 코드가 변수 자신을 참조할 수 있는 범위가 결정된다. 즉, 식별자가 유효한 범위를 말한다.

```
var x = 'global';

function foo() {
  var x = 'local';
  console.log(x); // ①
}

foo();

console.log(x); // ②
```

만약 스코프라는 개념이 없다면 같은 이름을 갖는 변수는 충돌을 일으키므로 프로그램 전체에서 하나밖에 사용할 수 없다. 식별자는 어떤 값을 구별할 수 있어야 하므로 유일해야한다. 즉, 하나의 값은 유일한 식별자에 연결되어야 한다.

스코프는 전역(global)과 지역(local)으로 구분할 수 있다. 

전역 : 코드의 가장 바깥 영역

지역 : 함수 몸체 내부

전역에서 선언된 변수는 전역 스코프를 갖는 전역 변수이고, 지역에서 선언된 변수는 지역 스코프를 갖는 지역 변수이다. 모든 스코프는 하나의 계층적 구조로 연결되며, 모든 지역 스코프의 최상위 스코프는 전역 스코프이다. 이렇게 스코프가 계층적으로 연결된 것을 스코프 체인이라 한다. 



함수코드가 만들어지면 함수의 스코프가 만들어진다.

만약 함수내부의 스코프에 없는 값을 찾으라고 하면 상위 스코프로 이동해서 찾는다.

전역에도 없으면 에러.

하위스코프로 가는건 없다. 무조건 상위 스코프로 간다. (단방향 연결 리스트)/스코프체인

호출이 되면 그때서야 스코프가 만들어진다.



함수가 호출 되자마자 태어난다.(스코프에 들어오면 태어난다.)  없어지면 소멸한다.

함수호출이 종료되면 스코프는 없어진다.

굉장히 짧은 시간안에 생성되고 소멸 2가지를 한다.



전역변수는 어플리케이션을 키는 순간부터 종료하는 순간까지 지속된다.

이상적인 함수는 하나의 일만 하는 함수. 짧을수록 좋다.



