---
title: 4.JavaScript- object oriented 
excerpt: JavaScript


#최상위 사진
header:
  #image: /assets/images/moon3.png
  teaser: /assets/images/moon3-th.png

gallery:
  - url: /assets/images/unsplash-gallery-image-1.jpg
    image_path: assets/images/unsplash-gallery-image-1-th.jpg
    alt: "placeholder image 1"
  - url: /assets/images/unsplash-gallery-image-2.jpg
    image_path: assets/images/unsplash-gallery-image-2-th.jpg
    alt: "placeholder image 2"
  - url: /assets/images/unsplash-gallery-image-3.jpg
    image_path: assets/images/unsplash-gallery-image-3-th.jpg
    alt: "placeholder image 3"
    


 #사이드바 설정 
sidebar:
  - title: "Role"
    nav: sidebar-sample

# 해당 글 목차
toc: true
toc_sticky: true

toc_label: "Yimsu's Blog"
toc_icon: "cog"


## 테그설정

categories:
  - JavaScript

tags:
  - JavaScript
  - "2021"
  - "2021.07"



---


4.Javascript - 객체지향 프로그래밍 

자바스크립트의 객체 지향은 자바와 c++ 이 추구하는 객체지향의 개념과 다르다.
Prototype - based programming 에 속한 자바스크립트에 대해 알아본다

<br/>
<br/>

보통의 사이트는 글 목록 , 본문 , 댓글 등으로 이루어져있다.
각각의 항목들은 각각의 로직으로 구성이된다. 
댓글에 대한 변수,메소드 들이 모여 객체로 관리하게 된다.
재활용성은 높아지지만 여러가지 문제들이 발생하게된다.
이런 문제들을 컨트롤하기위해 여러가지 방법들이 추가된다, 


<br/>

좋은 객체를 만들기 위해서는 문법적인 부분과 설계적인 부분 모두를 고려해야 한다. 
복잡하게 구성되어 있는 현실문제를 단순화 시키는것이 abstract(추상화) 이다.
메소드와 그 메소드가 사용하는 변수들을 그룹핑한것이 object(객체) 이다. 
내부의 동작은 숨기고 사용자에게 사용방법만 노출시키는것이 은닉화,캡슐화이다.
표준에 맞게 각 부품을 연결할때 연결점, 부품간의 interface(인터페이스) 라고한다. 

<br/>

First citizen : 전달저장리턴
클로저 : 내부함수가 외부함수의 context(지역변수,파라미터 등)에 접근하는것

<br/>



### 1. 객체 생성

<br/>
<br/>


``` javascript


var person = {} // 객체 생성 
person.name = 'ego'; // 변수 (프로퍼티 - 속성)을 생성
person.introduce = function() {
	return 'My name is ' + this.name + '</br>';
} // 객체 내에 프로퍼티 생성
document.write(person.introduce());
// 객체를 만드는 과정이 분산 



var person = {
	'name' : 'egg',
	'introduce2' : function() {
		return 'My name is ' + this.name + '</br>'; 
	}
}
var person2 = {
	'name' : 'egg2',
	'introduce2' : function() {
		return 'My name is ' + this.name + '</br>'; 
	}
}
document.write(person.introduce2());
// 분산을 해결 했지만 함수를 만드는것에서 중복 발생


```

<br/>
<br/>

### 2. 생성자 
 
constructor(생성자) 는 객체를 만든다

<br/>

``` javascript


function person(){}
var p0 = person(); // 객체 생성 x 
var p = new person(); // new 키워드가 붙어 함수를 생성자로 사용하여 객체 생성함  

p.name = 'egoing';
p.introduce = function(){
	return 'My name is ' + this.name;
}

————————————————————————


function Person(){}
var p1 = new Person();
p1.name = 'egoing';
p1.introduce = function(){
    return 'My name is '+this.name; 
}
var p2 = new Person();
p2.name = 'leezche';
p2.introduce = function(){
    return 'My name is '+this.name; 
} // p1, p2 생성 함수 중복 


function Person(name){
	this.name = name;
	this.introduce = function(){
		return 'My name is ' + this.name; 
	}
}
var p1 = new Person('ddd');
document.write(p1.introduce() + "<br/>")
var p2 = new Person('ccc');
document.write(p2.introduce() + "<br/>")
// 중복 해결
// 생성자는 객체를 초기화하는 역할을 한다. -> 코드의 재사용성 향상




```

<br/>
<br/>

### 3. 전역 객체 
 
<br/>


``` javascript




function func(){
	alert('gi');

}
window.func(); // 객체.속성 방식으로 속성(메소드) 호출. 
//func(); - 암시적으로 window의 속성으로 간주. 
// window 를 전역객체( global object)이라한다

var o = {'func':function(){
    alert('Hello?');
}}
o.func();
window.o.func(); // o 역시 window의 프로퍼티로 간주. 



```
<br/>
<br/>



### 4. this 

self 와 유사 
 
<br/>


``` javascript



function func(){
	if(window === this){
		document.write("window === this");
	}
}
func(); // 함수에서의 this는 window라는 전역객체를 가리킨다 

————————————

var o = {
	func : function() {
		if(o === this){
			document.write("o === this")
		}
	}
}
o.func(); // 메소드에서 this는 그 객체를 가리킨다 

————————————



var funcThis = null; 
function Func(){
    funcThis = this;
}

var o1 = Func();
if(funcThis === window){
    document.write('window <br />');
} // 기본적으로 함수안의 this는 window를 가리킨다 , window === window 
 
var o2 = new Func();
if(funcThis === o2){
    document.write('o2 <br />');
} // 생성자 안의 this가 o2객체를 가르키기 때문에 o2 === o2가 된다 




————————————




// var oo = { };  -  객체 리터럴 
// var oo = [1,2,3]; - 배열 리터럴
function sum(x,y){return x+y;}; // 함수 리터럴 생성 - sum 이 객체 
alert(sum(3,2));
var sum2 = new Function('x','y', 'return x+y'); // 함수 객체를 생성 
alert(sum2(1,2));



var o = {}
var p = {}
function func(){
	switch(this){
		case o:
			document.write('o<br/>');
			break;
		case p:
			document.write('p<br/>');
			break;
		case window:
			document.write('window<br/>');
			break;
	}
}
func();
func.apply(o); // o객체를 가져와서 this 값을 제어.
func.call(p); // this 값을 제어








```
<br/>
<br/>





### 5. 상속 
 
<br/>


``` javascript


function Person2(name){
    this.name = name;
}
Person2.prototype.name=null;
Person2.prototype.introduce = function(){
    return 'My name is '+this.name;  // 이부분을 수정하면 p2가 바꿔고 그것을 상속한 p3도 바뀐다.
}
var p2 = new Person2('egoing');
document.write(p2.introduce()+"<br />");


function Programmer(name){
    this.name = name;
}
Programmer.prototype = new Person2(); // prototype을 사용하여 Programmer에  Person2 객체가 가지고있는 name과 introduce를 상속
Programmer.prototype.coding = function(){
    return "hello world";
}; //  상속을 받은다음 .coding을 추가하여 발전시키는 상속의 중요 가치
var p3 = new Programmer('egooo');
document.write(p3.introduce()+"<br />");
document.write(p3.coding()+"<br />");







```
<br/>
<br/>




### 6. prototype 

상속의 구체적인 수단인 prototype.
prototype에 저장된 속성들은 생성자를 통해서 객체가 만들어질 때 그 객체에 연결된다. 

 
<br/>


``` javascript

function Ultra(){}
Ultra.prototype.ultraProp = true;
 
function Super(){}
Super.prototype = new Ultra();
 
function Sub(){}
Sub.prototype = new Super();
 
var o = new Sub();
console.log(o.ultraProp);


```
<br/>
<br/>



### 7. 표준 내장 객체(Standard Built-in Object) 

Array,Function etc…
 
<br/>


``` javascript


var arr = new Array('seoul','new york','ladarkh','pusan', 'Tsukuba');
function getRandomValueFromArray(haystack){
    var index = Math.floor(haystack.length*Math.random());
    return haystack[index]; 
}

document.write(getRandomValueFromArray(arr) + "<br/>")



————————————



// prototype을 통해 내장객체의 확장
var arr2 = new Array('seoul','new york','ladarkh','pusan', 'Tsukuba');
Array.prototype.rand = function(){
    var index = Math.floor(this.length*Math.random());
    return this[index];
}
document.write(arr2.rand());





```
<br/>
<br/>



### 8. Object 
 
<br/>


``` javascript


// Object.keys()
var arr = ["a","b","c"];
document.write('Object.keys(arr) -> ',Object.keys(arr)+" <br/>");

var o = {name:"a", age:"20"};
document.write(Object.keys(o)+" <br/>"); // .keys 는 key 값을 배열로만들어서 리턴 


// Object.prototype.toString() 
var a = [1,2,3];
document.write(a.toString()+" <br/>"); // toString은 배열이 가진 값을 출력 

var b = new Array(1,2,3);
document.write(b.toString());

// https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys

//toString 은 공식문서를 보면 매우 낮은 버전의 브라우저에서도 지원을 한다.


————————————



Object.prototype.contain = function(nee) {
	for(var key in this){
		if(this[key] === nee){
			return true; 
		}
	}
	return false;
}

var o = {'name':'egoing', 'city':'seoul'}
document.write(o.contain('egoing'));// contain 메소드도 o 객체에 포함된다. - Object 확장시 조심해야될 부분 
var a = ['egoing','leezche','grapittie'];
document.write(a.contain('leezche'));


for(var name in o){
    if(o.hasOwnProperty(name))
        console.log(name);  
} // hasOwnProperty 를 통해 prototpye으로 상속받은 객체(contain 메소드)를 제거한다.





```
<br/>
<br/>



### 9. 데이터 타입 
 
<br/>

객체가아닌 것 - 숫자, 문자열, boolean, null, undefined

<br/>
래퍼 객체 - String, number, Boolean ( 자동으로 생성 후 제거) 

<br/>

객체가 아닌 데이터 타입을 원시 데이터 타입( primitive type)이며 그외의 모든 데이터 타입들은 객체이다 

<br/>

``` javascript


var str = 'coding';
console.log(str.length);   // 6 , 문자열은 원시데이터 타입이지만 자바스크립트는 임시로 문자열 객체를 만들고 사용하고 제거하게된다 
console.log(str.charAt(0));   // "C"

```
<br/>
<br/>



### 10. 참조 
 
<br/>


``` javascript

var a = {'id':1};
var b = a; // 참조  
b.id = 2; 
console.log(a.id); 


var c = {'id':1};
var d = c;   
b = {'id':2}; // 새로운 객체를 할당해서 별개의 데이터로 분리  
console.log(c.id); 



// 원시 데이터 타입을 인자로 넘겼을 때
var aa = 1;
function func(bb){
	bb=2; // bb = aa  
}
func(aa);
console.log(aa); // 1 

// 참조 데이터 타입을 인자로 넘겼을 때 
var aaa = {'id':1};
function func (bbb) {
	bbb = {'id':2} // bbb = aaa  -> 새로운 객체 {'id':2} 를 생성한것
}
func(aaa);
console.log(aaa.id); // 1 


var aaaa = {'id':1};
function func(bbbb){
    bbbb.id = 2; // bbbb = aaaa -> id 값을 2로 변경한것 
}
func(aaaa);
console.log(aaaa.id);




// 변수에 담겨있는 데이터가 원시형이면 - 실제 데이터가 담겨있다. - 복제  
// 변수에 담겨있는 데이터가 객체라면 - 데이터에 대한 참조가 담겨있다 - 참조 - call by reference 와 유사 
// 객체가 아니라면 참조로 변경하기 어려운데 ,,,? 




```
<br/>
<br/>


자바스크립트 완벽가이드 // 자바스크립트 핵심가이드 // 자바스크립트 닌자 비급ㄴ

