# JS事件

## 三种事件模型

事件是用户操作网页时发生的交互动作或者网页本身的一些操作，现代浏览器一共有三种事件模型。

### 1、DOM0级模型

这种模型不会传播，所以没有事件流的概念，但是现在有的浏览器支持以冒泡的方式实现，它可以在网页中直接定义监听函数，也可以通过js属性来指定监听函数。这种方式是所有浏览器都兼容的。

### 2、IE事件模型

在该事件模型中，一次事件共有两个过程，事件处理阶段和事件冒泡阶段。

事件处理阶段会首先执行目标元素绑定的监听事件。然后是事件冒泡阶段，冒泡指的是事件从目标元素冒泡到document，依次检查经过的节点是否绑定了事件监听函数，如果有则执行。这种模型通过attachEvent来添加监听函数，可以添加多个监听函数，会按顺序依次执行。

### 3、DOM2级事件模型

在该事件模型中，一次事件共有三个过程，第一个过程是事件捕获阶段。捕获指的是事件从document一直向下传播到目标元素，一次检查经过的节点是否绑定了事件监听函数，如果有则执行，后面两个阶段和IE事件模型的两个阶段相同。这种事件模型，事件绑定的函数是addEventListener，其中第三个参数可以指定事件是否在捕获阶段执行。

## 1、事件委托

### 基本概念

事件委托，通俗来讲，就是把一个元素响应事件（click，keydown...）的函数委托到另一个元素。

一般来讲，会把一个或者一组元素的事件委托到它的父层或者更外层元素上，真正绑定事件的是外层元素，当事件响应到需要绑定的元素上时，会通过**事件冒泡**机制从而触发它的外层元素的绑定事件上，然后在外层元素上去执行函数。

### 委托的优点

#### 1、减少内存消耗

列表之中有大量的列表项，如果给每个列表项一一都绑定一个函数，那对于内存消耗是非常大的，效率上需要消耗很多性能；

#### 2、动态绑定事件

动态改变的元素改变时需要重新给新增的元素绑定事件，给即将删去的元素解绑事件；如果用了事件委托就没有这种麻烦了，因为事件时绑定在父层的，和目标元素的增减是没有关系的，执行到目标元素是在真正响应执行事件函数的过程中去匹配的；所以使用事件在动态绑定事件的情况下是可以减少很多重复工作的。

### 局限性

事件委托也是有一定局限性的；

比如focus、blur之类的事件本身没有事件冒泡机制，所以无法委托；

mousemove、mouseout这样的事件，虽然有事件冒泡，但是只能不断通过位置去计算定位，对性能消耗高，因此也是不适合于事件委托的；

## 2、事件传播

当事件发生在DOM元素上时，该事件并不完全发生在那个元素上，在当事件发生在DOM元素上时，该事件并不完全发生在那个元素上。

事件传播有三个阶段：

1. 捕获阶段
    事件从window开始，然后向下到每个元素，直到到达目标元素事件或event.target。
2. 目标阶段
    事件已到达目标元素。
3. 冒泡阶段
    事件从目标元素冒泡，然后上升到每个元素，直到到达window。

## 3、事件捕获

当事件发生在DOM元素上时，该事件并不完全发生在那个元素上。在捕获阶段，事件从window开始，一直到触发事件的元素。window--->document--->html--->body--->目标元素

## 4、事件冒泡

事件冒泡刚好和事件捕获相反，当事件发生在DOM元素上时，该事件并不完全发生在那个元素上。

addEventListener方法具有第三个可选参数useCapture，其默认值为false，事件将在冒泡阶段中发生，如果为true，则事件将在捕获阶段中发生。

  

  

  

  

  