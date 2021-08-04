# Javascript-this
## Description
   >javascript this binding
## ES2016
```javascript
class MyClass {
    constructor(name : string) {
        this.iv_name = name;
    }

    iv_name : string

    // Class Method
    fn01() {
        console.log(`Class Method, this=${this}`);
        if (this && this.iv_name) console.log('fn01', this.iv_name);
    }

    // Class Member Variable Function
    fn02 = function(this:MyClass) {
        console.log(`Class Member Variable Function, this=${this}`);
        if (this && this.iv_name) console.log('fn02', this.iv_name);
    }

    // Arrow Function
    fn03 = () => {
        console.log(`Arrow Function this=${this}`);
        if (this && this.iv_name) console.log('fn03', this.iv_name);
    }

    static iv_old : number = 10

    static fn04 = function() : void {
        console.log('Static Method, ', MyClass.iv_old);
    }
}


let x01 : MyClass = new MyClass('유미');
let x02 : MyClass = new MyClass('바둑이');

MyClass.fn04();

x01.fn01();
x01.fn02();
x01.fn03();

let m_f = x01.fn01;  m_f();
m_f = x01.fn02; m_f();
m_f = x01.fn03; m_f();
```

## ES5

```javascript
"use strict";
var MyClass = /** @class */ (function () {
    function MyClass(name) {
        var _this = this;
        // Class Member Variable Function
        this.fn02 = function () {
            console.log("Class Member Variable Function, this=" + this);
            if (this && this.iv_name)
                console.log('fn02', this.iv_name);
        };
        // Arrow Function
        this.fn03 = function () {
            console.log("Arrow Function this=" + _this);
            if (_this && _this.iv_name)
                console.log('fn03', _this.iv_name);
        };
        this.iv_name = name;
    }
    // Class Method
    MyClass.prototype.fn01 = function () {
        console.log("Class Method, this=" + this);
        if (this && this.iv_name)
            console.log('fn01', this.iv_name);
    };
    MyClass.iv_old = 10;
    MyClass.fn04 = function () {
        console.log('Static Method, ', MyClass.iv_old);
    };
    return MyClass;
}());
var x01 = new MyClass('유미');
var x02 = new MyClass('바둑이');
MyClass.fn04();
x01.fn01();
x01.fn02();
x01.fn03();
var m_f = x01.fn01;
m_f();
m_f = x01.fn02;
m_f();
m_f = x01.fn03;
m_f();

Customize
```
## f01 Function
   f01 함수는 모든 instance 에서 공유하기 위해서 Prototype 에 생성됨 ,여기서 this는 나중에 만들어질 instance객체를 가르킴
## f02 Function   
   f02 함수는 Class의 Member Variable로써 만들어질 instance객체안에 생성되는 함수(메모리 낭비)
## f03 Function   
   f03 함수는 화살표함수로써 함수 자체의 this바인딩을 갖지 않는다.따라서 '_ this' 변수안에 this를 참조  
