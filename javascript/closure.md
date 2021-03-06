# 클로저 \(closure\)

클로저\(closure\)는 내부함수가 외부함수의 맥락\(context\)에 접근할 수 있는 것을 말한다.

```javascript
function outter(){
  var title = 'Hello in outter';
  return function(){
    // 외부 함수 `outter`의 내부 변수 `title`을
    // 리턴되는 내부 함수에서 접근할 수 있다.
    // 즉 외부함수의 스코프에 있는 변수에 접근할 수 있다.
    return title;
  }
}

var inner = outter();
inner(); // 'Hello'
```

```javascript
function movie(name){
  return {
    setName: function(_name){
      name = _name;    
    },
    getName: function(){
      return name;
    },
  }
}
var m1 = movie('Matrix');
m1.getName(); // 'Matrix'
m1.setName('매트릭스'); // 매트릭스
```

`movie`의 인자로 받는 name 변수는 외부에서 접근 불가하지만, 내부에서는 사용할 수 있는 private 변수가 된다.

```javascript
var arr = [];
for(var i=0; i<5; i++) {
  arr[i] = function(){
    return i;
  }
}

for (var index in arr) {
	arr[index](); // 모두 5
}
```

위와 같이 바꾸면 리턴되는 내부 함수가 외부 함수의 콘텍스트에 접근할 수 있기 때문에 정상 작동한다.

```javascript
var arr = [];
for(var i=0; i<5; i++) {
  arr[i] = (function(id){
    return function(){
      return id;
    };
  })(i)
}

for (var index in arr) {
	console.log( arr[index]() ); // 0 ~ 4 출력
}
```

`arr`에 할당되는 함수가 외부 함수의 변수에 접근할 수 없기 때문에 위와 같은 결과가 나온다.

---

#### 함수를 호출하면?

함수를 호출하면 **실행 컨텍스트**와 **스코프 체인**이 생성된다. 함수를 실행하면 값을 읽거나 쓸 변수를 스코프 체인에서 검색한다. **스코프 체인**은 **변수 객체를 가리키는 포인터의 목록**이며,  객체를 직접 포함하는 것은 아니다.

#### 함수 실행이 끝나면?

함수 실행이 끝나면 활성화 객체는 파괴되고, 메모리에는 전역 스코프만 남는다. 외부함수가 실행을 마치고 익명함수를 반환하면, **익명함수의 스코프체인**은 **외부함수의 활성화 객체**와  **전역변수 객체를 포함**하도록 초기화된다.

#### 

