#### call\(\)

Function.propotype.call\(\)

`fun.call(thisArg, arg1, arg2, ...)`

thisArg:

    fun函数运行时指定的this值

    需要注意的是，指定的`this`值并不一定是该函数执行时真正的`this`值，
    如果这个函数处于[非严格模式下](https://developer.mozilla.org/zh-CN/docs/JavaScript/Reference/Functions_and_function_scope/Strict_mode)，
    则指定为`null`和`undefined`的`this值会自动指向`全局对象\(浏览器中就是window对象\)，
    同时值为原始值\(数字，字符串，布尔值\)的`this`会指向该原始值的自动包装对象。

可以让call\(\)中的对象调用当前对象所拥有的function。你可以使用call\(\)来实现继承：写一个方法，然后让另外一个新的对象来继承它（而不是在新对象中再写一次这个方法）。

document.color = 'red';

window.color = 'yellow';

var s = {color: 'black'};

function color\(\){

	return this.color;

}

color.call\(s\);  //black

color.call\(\);  //yellow;   默认传参window

color.call\(document\);    //red



#### **top变量**

指分割窗口最高层次的浏览器窗口





