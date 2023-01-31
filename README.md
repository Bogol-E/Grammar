@@@자바스크립트 문법
 @@@
 @@@브라우저 인터페이스
 @@@alert
 @@@alert(message);
 @@@message가 담긴 얼럿 창을 보여줍니다.
 @@@
 @@@prompt
 @@@result = prompt(질문, 초기값[선택값]);
 @@@‘확인’ 버튼을 눌렀을 땐 사용자가 입력한 값을 반환해주고,
 @@@‘취소’ 버튼을 눌렀을 땐 null을 반환
 @@@
 @@@confirm
 @@@result = confirm(질문)
 @@@확인 true 그외 false
 @@@
 @@@<윈도우키>+<.> : 이모지
 @@@
 @@@외부 스크립트
 @@@<script src="/path/to/script.js"></script>
 @@@
 @@@주석
 @@@//한줄	/* 여러줄 */
 @@@
 @@@변수
 @@@var, let, const	카멜 표기법(camelCase)
 @@@
 @@@자료형
 @@@숫자형, Bigint(끝에 'n'), 불린형, 객체형, 심볼형
 @@@문자형(글자형_char X)
 @@@'[백틱] ... ${변수나 표현식} ... [백틱]'
 @@@
 @@@null
 @@@'존재하지 않는(nothing)’ 값, ‘비어 있는(empty)’ 값, ‘알 수 없는(unknown)’ 값
 @@@
 @@@undefined
 @@@'값이 할당되지 않은 상태’
 @@@
 @@@문자형 변환 String(value)
 @@@
 @@@숫자 형변환 Number(value) 수학과 관련된 함수와 표현식에서 자동
 @@@undefined	->	NaN
 @@@null		->	0
 @@@true / false	->	1 / 0
 @@@string	전달받은 문자열을 “그대로” 읽되, 처음과 끝의 공백을 무시합니다.
 @@@문자열이 비어있다면 0이 되고, 오류 발생 시 NaN이 됩니다.
 @@@
 @@@불린 형변환 Boolean(value)
 @@@0, null, undefined, NaN, ""	->	false
 @@@그 외의 값		->	true
 @@@
 @@@쉼표 연산자
 @@@for (a = 1, b = 3, c = a * b; a < 10; a++) {
 @@@ ...
 @@@}
 @@@표현식 각각이 모두 평가되지만, 마지막 표현식의 평가 결과만 반환
 @@@
 @@@조건식
 @@@let result = condition ? value1 : value2;
 @@@condition이 truthy라면 value1이, 그렇지 않으면 value2가 반환
 @@@
 @@@if (조건1) {
 @@@  조건1 true일때 실행' );
 @@@} else if (조건2) {
 @@@  조건2 true일때 실행;
 @@@} else {
 @@@  그외 실행;
 @@@}
 @@@
 @@@||(OR)
 @@@인수 중 하나라도 true이면 true를 반환하고, 그렇지 않으면 false를 반환
 @@@변환 후 그 값이 true이면 연산을 멈추고 해당 피연산자의 변환 전 원래 값을 반환
 @@@모든 피연산자가 false로 평가되는 경우엔 마지막 피연산자를 반환합니다.
 @@@
 @@@&&(AND)
 @@@두 피연산자가 모두가 참일 때 true를 반환합니다. 그 외의 경우는 false를 반환
 @@@변환 후 값이 false이면 평가를 멈추고 해당 피연산자의 변환 전 원래 값을 반환
 @@@모든 피연산자가 true로 평가되는 경우엔 마지막 피연산자가 반환
 @@@
 @@@!(NOT)
 @@@피연산자를 불린형(true / false)으로 변환후 그 값의 역을 반환
 @@@
 @@@nullish 병합 연산자 '??'
 @@@여러 피연산자 중 그 값이 ‘확정되어있는’ 변수를 찾음
 @@@x = a ?? b
 @@@x = (a !== null && a !== undefined) ? a : b;
 @@@a가 null도 아니고 undefined도 아니면 a 그 외의 경우는 b
 @@@||는 첫 번째 truthy 값을 반환.
 @@@??는 첫 번째 정의된(defined) 값을 반환
 @@@
 @@@반복문
 @@@while (condition) {
 @@@  // condition(조건)이 truthy 이면 코드가 실행
 @@@}
 @@@
 @@@do {
 @@@  // 본문이 먼저 실행되고, 조건을 확인한 후 조건이 truthy인 동안엔 본문이 계속 실행
 @@@} while (condition);
 @@@
 @@@for (begin; condition; step) {
 @@@  // ... 반복문 본문 ...
 @@@}
 @@@continue는 현재 반복을 종료시키고 다음 반복으로 넘어가고 싶을 때
 @@@레이블(label) 은 반복문 앞에 콜론과 함께 쓰이는 식별자
 @@@break <labelName>문을 사용하면 레이블에 해당하는 중첩 반복문을 빠져나옴
 @@@break와 continue는 반복문 안에서만 사용할 수 있고,
 @@@레이블은 반드시 break이나 continue 지시자 위에 있어야 함
 @@@
 @@@<ex>소수 출력하기
 @@@let n = 10;
 @@@nextPrime:
 @@@for (let i = 2; i <= n; i++) { // 각 i에 대하여 반복문을 돌림
 @@@  for (let j = 2; j < i; j++) { // 제수(나눗수)를 찾음
 @@@    if (i % j == 0) continue nextPrime; // 소수가 아니므로 다음 i로 넘어감
 @@@  }
 @@@  alert( i ); // 소수
 @@@}
 @@@
 @@@switch문
 @@@switch(x) {
 @@@  case 'value1':  // if (x === 'value1')
 @@@    ...
 @@@    [break] //break문이 없으면 switch문 끝까지 실행
 @@@
 @@@  case 'value2':  // if (x === 'value2')
 @@@    ...
 @@@    [break]
 @@@
 @@@  default:
 @@@    ... //생략가능
 @@@    [break]
 @@@}
 @@@
 @@@함수선언
 @@@function name(parameter1, 매개변수2, ... parameterN) {
 @@@  // 함수 본문
 @@@}
 @@@코드 블록이 실행되기도 전에 처리
 @@@
 @@@함수 표현
 @@@let name = function(parameter) {
 @@@  // 함수 본문
 @@@};
 @@@실제 실행 흐름이 해당 함수에 도달했을 때 함수를 생성
 @@@
 @@@함수호출
 @@@name() name(인수) name(인수X:undefined)
 @@@매개변수에 값을 전달하지 않아도 그 값이 undefined가 되지 않게 하려면
 @@@함수를 선언할 때 =를 사용해 '기본값(default value)'을 설정
 @@@if (매개변수 === undefined) 매개변수 = '기본값';
 @@@text = text || '빈 문자열';
 @@@
 @@@반환 값(return value) return (여러줄)
 @@@return문이 없거나 return 지시자만 있는 함수는 undefined를 반환
 @@@
 @@@<ex>소수 출력함수1
 @@@function showPrimes(n) {
 @@@  nextPrime: for (let i = 2; i < n; i++) {
 @@@    for (let j = 2; j < i; j++) {
 @@@      if (i % j == 0) continue nextPrime;
 @@@    }
 @@@    alert( i ); // 소수
 @@@  }
 @@@}
 @@@
 @@@<ex>소수 출력함수2
 @@@function showPrimes(n) {
 @@@  for (let i = 2; i < n; i++) {
 @@@    if (!isPrime(i)) continue;
 @@@    alert(i);  // a prime
 @@@  }
 @@@}
 @@@function isPrime(n) {
 @@@  for (let i = 2; i < n; i++) {
 @@@    if ( n % i == 0) return false;
 @@@  }
 @@@  return true;
 @@@}
 @@@
 @@@<ex>콜백함수
 @@@function ask(question, yes, no) {
 @@@  if (confirm(question)) yes()
 @@@  else no();
 @@@}
 @@@ask(
 @@@  "동의하십니까?",
 @@@  function() { alert("동의하셨습니다."); },
 @@@  function() { alert("취소 버튼을 누르셨습니다."); }
 @@@);
 @@@
 @@@화살표 함수
 @@@let func = (arg1, 인자2, ...argN) => expression
 @@@<or>
 @@@let func = function(arg1, arg2, ...argN) {
 @@@  return 표현식;
 @@@};
 @@@
 @@@객체	키를 사용해 식별할 수 있는 값을 담은 컬렉션
 @@@let user = new Object( ); // '객체 생성자' 문법
 @@@let user = { };  // '객체 리터럴' 문법
 @@@중괄호 {...} 안에는 ‘키: 값’ 쌍으로 구성된 프로퍼티
 @@@키는 문자형과 심볼형만 가능
 @@@
 @@@프로퍼터 접근
 @@@점 표기법: obj.property
 @@@대괄호 표기법: obj["property"]
 @@@obj[varWithKey] 변수에서 키를 가져옴
 @@@
 @@@delete obj.prop	프로퍼티를 삭제
 @@@"key" in obj	해당 key를 가진 프로퍼티가 객체 내에 있는지 확인
 @@@for (let key in obj)	프로퍼티를 나열
 @@@
 @@@계산된 프로퍼티
 @@@객체 리터럴 안의 프로퍼티 키가 대괄호로 둘러싸인 표현식
 @@@
 @@@단축 프로퍼티
 @@@property. // property: property 과 같음
 @@@
 @@@‘for…in’ 반복문
 @@@for (key in object) {
 @@@  // 각 프로퍼티 키(key)를 이용하여 본문(body)을 실행합니다.
 @@@}
 @@@
 @@@‘for…of’ 반복문
 @@@for (key of object) {
 @@@  // [Symbol.iterator] 속성을 가지는 컬렉션 전용
 @@@}
 @@@
 @@@객체 복사
 @@@let clone = {}; // 새로운 빈 객체
 @@@// 빈 객체에 user 프로퍼티 전부를 복사해 넣습니다.
 @@@for (let key in user) {
 @@@  clone[key] = user[key];
 @@@}
 @@@<or>
 @@@Object.assign(dest, [src1, src2, src3...])
 @@@객체 src1, ..., srcN의 프로퍼티를 dest에 복사
 @@@
 @@@중첩 객체 복사(dep cloning)
 @@@lodash의  _.cloneDeep(obj) 메서드 사용
 @@@
 @@@메서드(method) 
 @@@객체 프로퍼티에 할당된 함수
 @@@객체명.함수명();
 @@@this 로 객체에 접근, 없으면 undefined
 @@@화살표 함수는 외부함수에서 가져옴
 @@@
 @@@메서드 단축 구문
 @@@객체명 = {
 @@@  메서드명() { // "메서드명: function()"과 동일
 @@@  }
 @@@};
 @@@
 @@@객체명.함수명1();
 @@@객체명.함수명2();
 @@@<or> 체이닝
 @@@객체명.함수명1()함수명2();
 @@@
 @@@생성자 함수(constructor function)
 @@@유사한 객체를 여러게 만들떄 사용
 @@@첫 글자는 대문자로 시작
 @@@'new' 연산자를 붙여 실행
 @@@this에 저장되고 반환
 @@@객체를 return 한다면 this대신 객체 반환
 @@@원시형 return은 무시
 @@@
 @@@<ex>
 @@@function User(name) {
 @@@  this.name = 이름;
 @@@  this.isAdmin = false;
 @@@}
 @@@let user = new User("보라");
 @@@
 @@@익명 생성자 함수(재사용X)
 @@@let user = new function() {
 @@@  this.name = "John"
 @@@};
 @@@
 @@@옵셔널 체이닝 '?.'
 @@@프로퍼티가 없는 중첩 객체를 에러 없이 안전하게 접근
 @@@?.'앞’의 평가 대상이 undefined나 null이면 평가를 멈추고 undefined를 반환
 @@@
 @@@심볼(symbol)
 @@@유일한 식별자(unique identifier)를 만들고 싶을 때 사용
 @@@let 심볼명 = Symbol("심볼이름(설명)");
 @@@Symbol.for(key)	 key라는 이름을 가진 전역 심볼을 반환
 @@@Symbol.*		 시스템 심볼 접근
 @@@
 @@@객체-원시형 형변환
 @@@obj[Symbol.toPrimitive] = function(hint) {
 @@@  // 반드시 원시값을 반환해야 함
 @@@  // hint는 "string", "number", "default" 중 하나가 될 수 있음
 @@@};
 @@@"string" (alert 같이 문자열을 필요로 하는 연산)
 @@@"number" (수학 연산)
 @@@"default" (드물게 발생함)
 @@@obj[Symbol.toPrimitive](hint)메서드
 @@@else> obj.toString( )이나 obj.valueOf( )를 호출
 @@@else> obj.valueOf( )나 obj.toString( )을 호출
 @@@
 @@@배열 	순서가 있는 컬렉션을 저장할 때 쓰는 자료구조
 @@@배열선언 
 @@@let arr = new Array( );
 @@@let arr = [ ];
 @@@.length		배열의 길이(숫자형 인덱스 중 가장 큰 값에 1을 더한 값)
 @@@push(...items)	items를 배열 끝에 더해줌다.
 @@@pop( ) 		배열 끝 요소를 제거하고, 제거한 요소를 반환합니다.
 @@@shift( )		배열 처음 요소를 제거하고, 제거한 요소를 반환합니다.
 @@@unshift(...items)	items를 배열 처음에 더해줍니다.
 @@@splice(pos, delCount, ...items)	pos부터 delCount개의 요소를 지우고, items 추가하기
 @@@slice(start, end)	start부터 end 바로 앞까지의 요소를 복사해 새로운 배열을 만듦
 @@@concat(...items) 	배열의 모든 요소를 복사하고 items를 추가해 새로운 배열을
 @@@	만든 후 이를 반환함. items가 배열이면 이 배열의 인수를 기존 배열에 더해줌
 @@@indexOf / lastIndexOf(item, pos)	pos부터 원하는 item을 찾음. 
 @@@			찾게 되면 해당 요소의 인덱스를, 아니면 -1을 반환함
 @@@includes(value) 	배열에 value가 있으면 true를, 그렇지 않으면 false를 반환함
 @@@find/filter(func) 	func의 반환 값을 true로 만드는 첫 번째/전체 요소를 반환함
 @@@findIndex 		find와 유사함. 다만 요소 대신 인덱스를 반환함
 @@@forEach(func)	모든 요소에 func을 호출함. 결과는 반환되지 않음
 @@@map(func)		 모든 요소에 func을 호출하고, 반환된 결과로 새로운 배열을 만듦
 @@@sort(func) 	배열을 정렬하고 정렬된 배열을 반환함
 @@@reverse( ) 		배열을 뒤집어 반환함
 @@@split/join 		문자열을 배열로, 배열을 문자열로 변환함
 @@@reduce(func, initial) 	요소를 차례로 돌면서 func을 호출함. 반환값은 다음 함수 
 @@@		호출에 전달함. 최종적으로 하나의 값이 도출됨
 @@@Array.isArray(arr) 	arr이 배열인지 여부를 판단함
 @@@arr.some(fn)	함수의 반환 값을 true로 만드는 요소가 하나라도 있는지 여부를 확인
 @@@arr.every(fn)	모든 요소가 함수의 반환 값을 true로 만드는지 여부를 확인
 @@@arr.fill(value, start, end)	start부터 end까지 value를 채워 넣음
 @@@arr.copyWithin(target, start, end)     start부터 end까지 요소를 복사하고 target에 덮어씀
 @@@for (let i=0; i<arr.length; i++)	가장 빠른 방법이고 오래된 브라우저와도 호환
 @@@for (let item of arr) 		배열 요소에만 사용되는 모던한 문법 (인덱스X 값만)
 @@@for (let i in arr)		키가 숫자가 아니라도 가고 느림 객체에 사용
 @@@
 @@@이터러블
 @@@for..of을 사용할 수 있는 객체
 @@@이터레이터 obj[Symbol.iterator] 	 반드시 구현
 @@@메서드 next( ) 	객체 {done: Boolean, value: any} 반드시 반환
 @@@done : true은 반복이 끝났음을 의미, 그렇지 않은 경우엔 value
 @@@유사 배열		인덱스와 length 프로퍼티가 있는 객체
 @@@Array.from(obj[, mapFn, thisArg]) 이터러블이나 유사 배열인 obj를 진짜 Array로 만듬
 @@@
 @@@맵(Map) 	키가 있는 값이 저장된 컬렉션. 객체와 달리 맵은 키에 다양한 자료형을 허용
 @@@new Map([iterable])	 맵을 만듬. [key,value]쌍이 있는 iterable(예: 배열)을 선택적으로
 @@@		넘길 수 있는데, 이때 넘긴 이터러블 객체는 맵 초기화에 사용.
 @@@map.set(key, value)	키를 이용해 값을 저장
 @@@map.get(key)	키에 해당하는 값을 반환. key가 존재하지 않으면 undefined를 반환
 @@@map.has(key)	키가 있으면 true, 없으면 false를 반환 
 @@@map.delete(key)	키에 해당하는 값을 삭제 
 @@@map.clear( )	맵 안의 모든 요소를 제거 
 @@@map.size		요소의 개수를 반환
 @@@
 @@@셋	 중복이 없는 값을 저장할 때 쓰이는 컬렉션
 @@@new Set([iterable])	셋을 만듬. iterable 객체를 선택적으로 전달받을 수 있는데
 @@@	(대개 배열을 전달받음), 이터러블 객체 안의 요소는 셋을 초기화하는데 쓰임
 @@@set.add(value)	값을 추가하고 셋 자신을 반환. 셋 내에 이미 value가 있는 경우 동작X
 @@@set.delete(value) 	값을 제거합니다. 제거에 성공하면 true, 아니면 false를 반환
 @@@set.has(value) 	셋 내에 값이 존재하면 true, 아니면 false를 반환 
 @@@set.clear()		셋을 비움
 @@@set.size 		셋에 몇 개의 값이 있는지 카운트
 @@@
 @@@위크맵 (WeakMap)
 @@@키가 반드시 객체, 반복 작업과 keys(), values(), entries() 메서드를 지원하지 않는다
 @@@weakMap.get(key)
 @@@weakMap.set(key, value)
 @@@weakMap.delete(key)
 @@@weakMap.has(key)
 @@@
 @@@위크셋 (WeakSet)
 @@@객체만 저장할 수 있다
 @@@add, has, delete를 사용할 수 있고, size, keys()나 반복 작업 관련 메서드는 사용할 수 없다
 @@@
 @@@순회(iteration)	
 @@@일반객체
 @@@Object.keys(obj)	객체의 키만 담은 배열을 반환 
 @@@Object.values(obj)	객체의 값만 담은 배열을 반환 
 @@@Object.entries(obj)	[키, 값] 쌍을 담은 배열을 반환
 @@@Map, Set, Array 
 @@@map.keys( )	iterable 객체 반환	
 @@@객체에 배열 전용 메서드 사용하기
 @@@Object.entries(obj)를 사용해 객체의 키-값 쌍이 요소인 배열을 얻음
 @@@만든 배열에 map 등의 배열 전용 메서드를 적용.
 @@@반환된 배열에 Object.fromEntries(array)를 적용해 배열을 다시 객체로 되돌림
 @@@
 @@@
 @@@
 @@@
 @@@
 @@@
 @@@숫자형
 @@@0의 개수를 'e'뒤에 추가 소수는 음수
 @@@16진수(0x), 8진수(0o), 2진수(0b)
 @@@parseInt(str, base)	str을 base진수로 바꿈
 @@@num.toString(base)	base진법으로 num을 표현한 후, 이를 문자형으로 변환
 @@@parseInt/parseFloat	문자열에서 숫자만 읽고, 읽은 숫자를 에러가 발생하기 전에 반환
 @@@parseInt(str, radix)	정수 반환, 두번째 인수는 진수
 @@@parseFloat		부동 소수점 숫자
 @@@Math.floor	소수점 첫째 자리에서 내림(버림)
 @@@Math.ceil		소수점 첫째 자리에서 올림
 @@@Math.trunc	소수부를 무시
 @@@Math.round	소수점 첫째 자리에서 반올림
 @@@Math.random( )	0과 1 사이의 난수를 반환합니다(1은 제외)
 @@@num.toFixed(n)	소수점 n번째 까지 어림수를 문자형 반환
 @@@isNaN(value) 	인수를 숫자로 변환한 다음 NaN인지 테스트
 @@@isFinite(value) 	인수를 숫자로 변환하고 변환한 숫자가 NaN/Infinity/-Infinity가 아닌
 @@@		일반 숫자인 경우 true를 반환 // 숫자인지 검증하는데 사용
 @@@
 @@@문자열
 @@@[pos] <or> str.charAt(pos)	문자열 내 pos위치 접근
 @@@백틱 문자열 중간에 ${…}을 사용해 표현식 가능
 @@@func`string` 템플릿 함수(백틱 안을 인수로 받아 자동으로 func 호출)
 @@@str.trim() – 문자열 앞과 끝의 공백 문자를 다듬어 줍니다(제거함).
 @@@str.repeat(n) – 문자열을 n번 반복
 @@@length 프로퍼티엔 문자열의 길이
 @@@toLowerCase()		대문자를 소문자로 변경
 @@@toUpperCase()		소문자를 대문자로 변경
 @@@str.indexOf(substr, pos)		문자열 str의 pos에서부터 시작해,          (앞부터)
 @@@str.lastIndexOf(substr, position)	부분 문자열 substr이 어디에 위치하는지 (뒤부터)
 @@@str.includes(substr, pos)	str에 부분 문자열 substr이 있는지에 따라 true나 false를 반환
 @@@str.slice(start [, end])		문자열의 start부터 end까지(end는 미포함)를 반환
 @@@str.substring(start [, end])	start와 end 사이에 있는 문자열을 반환
 @@@str.substr(start [, length])	start에서부터 시작해 length 개의 글자를 반환
 @@@str.codePointAt(pos)		pos에 위치한 글자의 코드를 반환
 @@@String.fromCodePoint(code)	숫자 형식의 code에 대응하는 글자를 만듬
 @@@str.localeCompare(str2)	 ECMA-402에 따라 str - str2 나타내는 정수 반환 
