# Javascript-this

```
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
