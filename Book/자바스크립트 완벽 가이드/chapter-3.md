자바스크립트 완벽 가이드
---

**[Chapter 3] 데이터 타입과 값.**

- 자바스크립트에서는 세가지 기본 데이터 타입인 `숫자`, `텍스트의 나열(String)`, `불리언 진리 값(boolean)`이 있다.
- 또한 두개의 단순 데이터 타입인 `null`과 `undefined`를 정의하고 있다. 두 타입 모두 단일 값을 가진다.
- `객체(Object)`라고 불리는 복합 데이터 타입을 지원하는데, 값들의 모임이다. 객체는 이름 붙은 값들의 순서 없는 모임을 나타내거나, 번호가 붙은 순서 있는 값들의 모임을 나타내기도 한다`(배열)`.
- `함수(function)`이라고 불리는 특별한 형태의 객체를 정의하기도 한다. `함수`는 실행 가능한 코드를 담은 객체다.
- 이 밖에도 `Date 클래스`는 날짜를 표현하는 객체들을 정의하고, `RegExp 클래스`는 정규 표현식을 나타내는 객체를 정의 하며, `Error 클래스`는 문법 에러나 자바 스크립트에서 발생할 수 있는 런타임 에러를 나타내는 객체들을 정의 한다.

**3.1 숫자.**
- 자바 스크립트는 정수 값과 실수 값을 구별하지 않는다는 점에서 `C`나 `JAVA`와는 다르다. 자바 스크립트에서 모든 숫자는 실수로 표현된다.

**3.1.2 16진수와 8진수**
- 16진수 리터럴은 `Ox`나 `0X`로 시작하고 16진수 숫자들이 뒤따르는 형태이다.
- 8진수 리터럴은 숫자 `0`으로 시작되고 `0-7`까지의 숫자 시퀀스가 뒤따르는 형태이다.
- 자바 스크립트 구현에 따라서 8진수 리터럴을 지원할 수도 있고 하지 않을 수도 있기 때문에 `0`으로 시작하는 정수 리터럴은 절대로 사용하지 말라.

**3.1.3 부동소수점 리터럴.**
- 부동소수점 리터럴은 소수점을 가질 수 있다. 부동 소수점 리터럴은 전통적인 문법으로 표현 된다.
- `[digits][.digits](E|e)[(+|-)]digits]` 으로 표현된다.
- 실수는 무한 개 존재 하지만 자바 스크립트에서는 제한된 개수만을 표현 할 수 있다.

**3.1.6 특수한 숫자 값.**
- 부동 소수점 값으로 표현 가능한 가장 큰 유한 수보다 더 큰 값은 무한대를 나타내는 특수한 값이 되며 자바스크립트에서는 그 값을 `Infinity`로 출력한다. 음의 무한대일 경우 `-Infinity`로 출력 한다.
- 수리 연산(0을 0으로 나누는 것과 같은 경우)이 정의 되지 않은 결과를 산출 하거나 에러를 발생할 경우 `NaN`을 출력 한다. 이 값은 어떤 숫자와 비교해도 동일 하지 않으며 스스로와 비교해도 동일 하지 않다. 이 값을 테스트 하기 위해서는 `isNaN()`이라는 특별한 함수가 필요하다. 
- `isFinite()` 함수는 주어진 숫자가 `Nan`이 아닌 동시에 양의 무한대나 음의 무한대가 아닌지 여부를 검사한다.

**3.2 문자열.**
- `문자열(String)`은 unicode 문자난 숫자, 문장 부호들이 시퀀스로 텍스트를 표현 하는 데이터 타입이다. 
- `작은 따옴표(')`나 `큰 따옴표(")` 쌍으로 문자열을 둘러싸서 문자열 리터럴을 표현 할 수 있다.
- `C`나 `Java`와는 다르게 `char`같은 문자 데이터 타입은 가지고 있지 않다.

**3.2.1 문자열 리터럴.**
- 문자열은 0개 또는 하나 이상의 Unicode문자들이 `작은 따옴표(')` 혹은 `큰 따옴표(")`로 둘러싸인 시퀀스다.
- 문자열 리터럴은 한 줄을 넘지 말아야 한다. 문자열 내에 줄바꿈 문자를 포함시키고 싶다면 `\n`을 사용한다.

**3.2.2 문자열 리터럴 내 이스케이프 시퀀스.**
- `역슬래시 문자(\)`는 자바 스크립트 문자열에서 특별한 목적을 위해 사용한다. EX) \n, \'
- `역슬래시`는 작은 따옴표 문자를 일반적인 해석 방식에서 벗어나 특수한 방식으로 해석하게 만든다.

|시퀀스|표현하는 문자|
|-----|-----------|
|\0|널문자|
|\b|백스페이스|
|\t|수평 탭|
|\n|줄바꿈 문자|
|\v|수직 탭|
|\f|폼 피드|
|\r|캐리지 리턴|
|\"|큰 따옴표|
|\'|작은 따옴표|
|\\|역슬래시|

**3.2.3 문자열 조작.**
- 자바스크립트가 지원하는 기본 기능 중 하나는 여러 문자열을 이어 붙이는 것이다. 숫자에 `+ 연산자`를 문자열에 적용하면 두번째 문자열을 첫 번째 문자열에 이어 붙여 두 문자열을 합친다.
- 자바스크립트 문자열은 0부터 인덱스가 시작된다.

**3.2.4 숫자를 문자열로 변환하기.**
- 숫자는 필요할 떄 문자열로 자동으로 변환 된다. EX) 문자열을 이어 붙이는 표현식에서 숫자가 사용될 때.
- 숫자를 문자열로 변환 하려면 간단히 숫자에 빈 문자열을 더하면 된다. 또는 명시적으로 숫자를 문자열로 변환하려면 `String()` 함수를 사용한다. 또는 `toString()` 메서드를 사용한다.
- `toString()` 메서드에서 변환에 사용할 기수를 지정하면 기수에 맞게 변환된다. EX) toString(2) -> 2진수 변환.
- `toFixed()`는 숫자를 문자열로 변환하면서 소수점 이하 숫자를 지정된 개수만큼만 출력한다.
- `toExponential()`은 소수점 앞의 숫자 하나와 지정된 개수의 소수점 이후 숫자로 구성되는 지수 표기법을 사용하여 숫자를 문자열로 변환한다.
- `toPrecision()`은 지정된 수의 유효 숫자 개수만큼 숫자를 출력한다.

**3.2.5 문자열을 숫자로 변환하기.**
- 문자열이 숫자 문맥에 사용되면 자동으로 숫자로 변환된다.
- 문자열에서 0을 뺴면 문자열을 숫자로 변환 할 수 있다. 하지만 문자열에서 0을 더하면 타입 변환이 이루어 지는 것이 아니라 이어 붙이기가 수행된다는 것에 주의 하자.
- 명시적으로 문자열을 숫자로 변활 할 때에는 `Number()` 생성자를 함수처럼 호출 하는 것이다.
- `parseInt()`와 `parseFloat()`는 문자열 내에 존재하는 어떤 숫자라도 변화하여 반환하고 숫자 다음에 나오는 숫자가 아닌 문자들은 모두 무시한다. 만약 지정된 문자열을 숫자로 변환하지 못할 경우 `NaN`을 반환한다.
- `parseInt()`는 정수만 변환하며 `0x`나 `OX`로 시작하면 16진수 숫자로 인식한다. 
- `parseFloat()`는 정수와 부동소수점 숫자를 모두 변활 할 수 있다.

**3.3 불리언 값.**
- `불리언(boolean)` 데이터 타입은 오직 두개의 값만을 가질수 있다. 이 두개의 값은 `true`와 `false` 리터럴로 표현된다.

**3.3.1 불리언 타입 변환.**
- 불리언 값이 숫자 문맥에서 사용되면 `true`는 숫자 `1`로 `false`는 숫자 `0`으로 변환된다.
- 불리언 값이 문자열 문맥에서 사용되면 `true`는 문자열`"true"`로 `false`는 `"false"`로 변환된다.
- 불리언 값을 명시적으로 변환 할 경우에는 `Booleans()` 함수를 사용할수 있다.

**3.4 함수.**
- `함수(function)`는 자바스크립트 프로그램에 정의되어 있거나 자바스크립트 구현에 미리 정의되어 있는 실행 가능한 코드다. 
- `함수(function)`는 계산 대상인 값들을 지정하는 `전달인자(argument)`나 `매개변수(parameter)`를 넘겨 받을 수 있으며 계산 결과를 나타내는 값을 반환할 수도 있다.
- 자바스크립트에서 중요한 특징중 하나는 `함수도 자바스크립트 코드로 조작할 수 있는 형태의 값이라는 점이다.` 자바를 포함한 많은 언어에서 함수는 단지 언어의 문법적인 요소로서 존재한다. 함수는 단순히 정의하고 호출할 수 있는 것이지 데이터 타입은 아니다. 하지만 자바스크립트에서 함수가 실제로 값이라는 사실은 이 언어에 큰 유연성을 부여 한다. 이것은 `함수를 변수나 배열, 객체에 저장할 수 있으며 다른 함수의 전달인자로 넘겨 줄 수 있다는 것을 의미한다.`
- 함수도 숫자나 문자열처럼 값이므로 다른 값처럼 프로퍼티에 할당될 수 있다. 함수가 어떤 객체의 프로퍼티로 할당되면 흔히 그 `객체의 메서드(method)`라고 부른다.

**3.4.1 함수 리터럴.**
- 자바스크립트는 함수를 정의하는 함수 리터럴 문법도 제공한다. 
- `함수 리터럴`은 `function 키워드`, `함수이름(생략가능)`, `괄호로 둘러싸인 함수 전달인자 목록`, 마지막 `중괄호`로 구성된다.
- 따라서 `C`나 `Java`에서 사용되는 일반적인 방법 외에도 다음과 같이 함수 리터럴로 사용할 수 있다.

```JS
//일반적인 방법.
functio square(x) { return x*x;}

// 리터럴 사용방법.
var square = function(x) {return x*x;}
```

- 이름 없는 함수를 프로그램 내에 리터럴 형태로 포함시킬수 있게 한 최초의 언어인 `Lisp` 프로그램 언어를 기리는 의미에서 이런한 방식으로 정의된 함수를 람다함수(lambda funtion)라고 부른다.
- 함수를 정의하는 또다른 방법은 `전달인자 목록`과 함께 `함수 몸체`를 문자열 형태로 `Function()`생성자에 전달하는 것이다. 별로 유용한 방법은 아니다.

```JS
var square = new Function("x", "return x*x;");
```

**3.5 객체.**
- `객체(Object)`는 이름 붙은 값들의 모임이다. 보통 이 이름 붙은 값들을 `객체의 프로퍼티(property)`라고 부른다.
- `객체 프로퍼티`를 참조할려면 객체 이름을 쓰고 이어서 `마침표(.)`와 `프로퍼티 이름`을 적어주면 된다.
- 자바스크립트에서 객체는 `연관 배열(associative array)`역활도 수행한다. 즉, 객체는 임의 문자열에 임의의 값을 연결한다. 객체가 이러한 방식으로 사용될 경우 객체 프로퍼티에 접근할 때는 다른 문법을 사용한다. 이때는 접근 하려는 프로피터 이름을 나타내는 문자열을 `대괄호([])`로 둘러 싸면된다.

**3.5.1 객체 생성.**
- 원하는 객체를 생성하고 나면 마음대로 객체를 사용하고 프로퍼티 값을 설정 할 수 있다.

```JS
var point = new Object();
point.pi = 3.14;
point.r = 4;
```

**3.5.2 객체 리터럴.**
- 자바스크립트는 객체를 생성하고 프로퍼티를 지정하는 객체 리터럴 문법을 제공한다.
- `객체 리터럴`은 콜론으로 구별되는 프로퍼티 이름/값 쌍들이 다시 쉼표로 분리된 목록이다. 위 예제를 다음과 같이 생성하고 초기화 할 수 있다.

```JS
var point = { pi:3.14, r:4 };
```

**3.5.3. 객체 변환.**
- `null`이 아닌 객체가 불리언 문맥에서 사용되면 `true`로 변환된다.
- 객체가 문자열 문맥에서 사용되면 객체의 `toString()` 메서드가 호출되고 이 메서드가 반환하는 문자열이 대신 사용된다.
- 객체가 숫자 문맥에서 사용되면 `valueOf()`메서드를 호출한다. 이 메서드가 기본 데이터타입에 해당하는 값을 반환하면 그 값을 사용한다.

**3.6 배열.**
- `배열(array)`는 객체처럼 데이터 값들의 모음이다. 객체 내에 포함되는 각 데이터 값에는 이름이 있는 반면, 배열의 각 데이터 값에는 번호, 즉 인덱스(index)가 있다. 
- `배열`은 다른 배열이나 객체, 혹은 함수를 포함한, 어떠한 자바스크립트 데이터 타입의 데이터라도 담을 수 있다.
- 자바스크립트가 배열의 배열 형태 말고는 다차원 배열을 지원하지 않는다는것을 주의하자.
- 자바스크립트는 타입의 제약이 없는 언어이므로, 자바 언어처럼 배열의 원소들이 모두 동일한 타입을 가질 필요는 없다.

**3.6.1 배열 생성.**
- 배열은 `Array()` 생성자 함수로 생성할 수 있다.

```JS
var example = new Array();
example[0] = 1.2;
example[1] = "hello world";
example[2] = false;
example[3] = { pi:3.14, r:4 };
```

- 배열 원소드릉ㄹ `Array()`생성자에 넘겨주어 배열을 초기화 할 수도 있다.

```JS
var example = new Array(1.2, "hello world", false, { pi:3.14, r:4});
```

- `Array()` 생성자에 숫자 하나를 넘겨주면 숫자는 배열의 크기로 사용된다.

**3.7 null.**
- 자바스크립트 키워드 `null`은 아무런 값도 나타내지 않는 특수한 값이다.
- `null`은 불리언 문맥에서 사용되면 `false`로 변환 된다.
- `null`은 숫자 문맥에서 사용되면 `0`으로 변환된다.
- `null`은 문자열 문맥에서 사용되면 `"null"`로 변환된다.

** 3.8 undefined.**
- `undefined`는 선언은 되었지만 값이 할당된 적이 없는 변수에 접근하거나, 존재하지 않는 개체 프로퍼티에 접근 할 경우 반환되는 값이다.
- `null`과 `undefined` 값은 서로 구별되는 값이지만 `동등 연산자(==)`는 둘을 같은 것으로 간주한다. 만약 `null`값과 `undefined`값을 구별하는 것이 목표라면 `일치 연산자(===)`나 `typeof 연산자`를 사용해라.

** 3.9 Date 객체.**
- 날짜나 시간 값은 기본 데이터 타입에 속하는 것은 아니지만, 자바스크립트에서는 날짜와 시간을 표현하고 그 값을 조작하는데 사용할 수 있는 객체 집합을 제공한다.
- `Date객첵`는 문자열이나 숫자 형태로 작성된 날짜를 밀리 초 형태로 변환하는 함수들을 제공하여, 날짜와 관련된 몇가지 산술 연산을 수행하기 편하게 해준다.

** 3.10 정규 표현식.**
- `정규 표현식(regular expression)`은 텍스트 패턴을 기술하는 데 사용할 수 있는 강력한 문법을 제공한다.
- `정규 표현식`은 `RegExp`객체로 표현되며 `RegExp()`생성자로 생설할 수 있다.

** 3.11 Error 객체.**
- 자바스크립트 인터프리터는 런타임 에러가 발생하면 이러한 클래스들 중 하나에 해당하는 객체를 `던진다(throw)`. 각 에러 객체에는 자바스크립트 구현 나름의 에러메세지를 담고 있는 message 프로퍼티가 있다.

** 3.14 객체에서 기본 타입으로 변환.**
- `null`이 아닌 객체가 불리언 문맥에서 사용되면 `true`로 변환된다. 배열, 함수, 심지어 false로 변환되는 기본값을 나타내는 객체도 그렇다.

** 3.15 값에 의한 vs. 참조에 의한.**

||값에 의한|참조에 의한|
|----|--------|---------|
|복사|실제로 값이 복사된다. 두 개의 개별적이고 독립적인 복사본이 존재한다.|값에 대한 참조만 복사된다. 새로운 참조에 의해 값이 변경되면 원본 참조에서도 그 변경이 나타난다.|
|전달|별개의 값 복사본이 함수에 전달된다. 복사본을 변경해도 함수 외부에 아무런 영향을 주지 않는다.|값에 대한 참조가 함수에 전달된다. 함수내에서 전달 받은 참조를 통해 값을 변경하면 그 변경은 함수 외부에서도 일어난다.|
|비교|동일한 값인지를 알아보기 위해 별개의 두 값이 비교된다.|서로 동일한 값을 가리키는지 알아보기 위해 두 참조가 비교된다. 참조가 가리키는 값들이 비록 동일한 바이트들로 구성되었다 할지라도, 서로 다른 값을 가리키는 두 참조는 같지 않다.|