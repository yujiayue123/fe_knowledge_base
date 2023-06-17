## var、let 和 const 的范围、使用和提升

### Var

在 ES6 出现之前，var 声明占主导地位。但是，使用 var 声明的变量存在一些问题。这就是为什么有必要出现新的声明变量的方法。首先，在讨论这些问题之前，让我们更多地了解 var。

#### var 的作用域

作用域（scope）意味着这些变量可以在哪里使用。var 声明的作用域是全局的或函数/局部的。

当 var 变量在函数外部声明时，作用域是全局的。这意味着在函数体外用 var 声明的任何变量都可以在整个窗口中使用。

var 在函数中声明时，它的作用域是在函数体内。这意味着它只能在该函数中被访问。

要进一步了解，请查看下面的示例。

```javascript
var greeter = 'hey hi';

function newFunction() {
  var hello = 'hello';
}
```

在这里，greeter 是全局作用域的，因为它存在于函数之外，而 hello 是函数作用域，所以我们不能在函数之外访问变量 hello。所以如果我们这样做：

```javascript
var tester = 'hey hi';

function newFunction() {
  var hello = 'hello';
}
console.log(hello); // error: hello is not defined
```

我们会得到一个错误，这是由于 hello 在函数之外不可用。

#### var 变量可以重新声明和更新

这意味着我们可以在相同的作用域内执行此操作，并且不会出错。

```javascript
var greeter = 'hey hi';
var greeter = 'say Hello instead';
```

同时

```javascript
var greeter = 'hey hi';
greeter = 'say Hello instead';
```

#### var 的提升

提升（hoisting）是一种 JavaScript 机制，其中变量和函数声明在代码执行之前被移动到其作用域的顶部。这意味着，如果我们这样做：

```javascript
console.log(greeter);
var greeter = 'say hello';
```

它被解释为：

```javascript
var greeter;
console.log(greeter); // greeter is undefined
greeter = 'say hello';
```

因此 var 变量被提升到其作用域的顶部，并使用 undefined 值进行初始化。

#### var 的问题

var 有一个弱点，我将使用下面的例子来解释：

```javascript
var greeter = 'hey hi';
var times = 4;

if (times > 3) {
  var greeter = 'say Hello instead';
}

console.log(greeter); // "say Hello instead"
```

因此，由于 times > 3 返回 true，greeter 被重新定义为 "say Hello instead"。如果你有意要重新定义 greeter，这不是问题，但当你没有意识到之前已经定义了一个变量 greeter 时，它就会成为问题。

如果你在代码的其他部分使用了 greeter，你可能会对得到的输出感到惊讶。这可能会导致你的代码中出现很多错误。这就是为什么 let 和 const 是必要的。

### Let

let 现在是变量声明的首选。这并不奇怪，因为它是对 var 声明的改进。它还解决了我们刚刚介绍的 var 的问题。让我们考虑一下为什么会这样。

#### let 是块作用域

块是由 {} 界定的代码块。一个块存在于花括号中。花括号内的任何内容都是一个块。

因此，在带有 let 的块中声明的变量只能在该块中使用。让我用一个例子来解释一下：

```javascript
let greeting = 'say Hi';
let times = 4;

if (times > 3) {
  let hello = 'say Hello instead';
  console.log(hello); // "say Hello instead"
}
console.log(hello); // hello is not defined
```

我们看到在它的块（定义它的花括号）之外使用 hello 会返回一个错误。这是因为 let 变量是块作用域的。

#### let 可以更新但不能重新声明

就像 var 一样，使用 let 声明的变量可以在其作用域内更新。与 var 不同，let 变量不能在其作用域内重新声明。所以虽然这会运行：

```javascript
let greeting = 'say Hi';
greeting = 'say Hello instead';
```

这将返回一个错误：

```javascript
let greeting = 'say Hi';
let greeting = 'say Hello instead'; // error: Identifier 'greeting' has already been declared
```

但是，如果同一个变量定义在不同的作用域，就不会报错：

```javascript
let greeting = 'say Hi';
if (true) {
  let greeting = 'say Hello instead';
  console.log(greeting); // "say Hello instead"
}
console.log(greeting); // "say Hi"
```

为什么没有错误？这是因为两个实例都被视为不同的变量，因为它们具有不同的作用域。

这一事实使 let 成为比 var 更好的选择。使用 let 时，如果你以前使用过变量名称，则不必担心，因为变量仅存在于其作用域内。

此外，由于一个变量不能在一个作用域内多次声明，那么前面讨论的 var 出现的问题就不会发生。

#### let 的提升

就像 var 一样，let 声明被提升到顶部。与初始化为 undefined 的 var 不同，let 关键字未初始化。所以如果你在声明之前尝试使用 let 变量，你会得到一个 Reference Error。

### Const

用 const 声明的变量保持恒定值。 const 声明与 let 声明有一些相似之处。

#### const 声明是块作用域

与 let 声明一样，const 声明只能在它们声明的块内访问。

#### const 不能更新或重新声明

这意味着用 const 声明的变量的值在其作用域内保持不变。它不能被更新或重新声明。所以如果我们用 const 声明一个变量，我们不能这样做：

```javascript
const greeting = 'say Hi';
greeting = 'say Hello instead'; // error: Assignment to constant variable.
```

也不能这样：

```javascript
const greeting = 'say Hi';
const greeting = 'say Hello instead'; // error: Identifier 'greeting' has already been declared
```

因此，每个 const 声明都必须在声明时进行初始化。

当涉及到用 const 声明的对象时，这种行为在某种程度上有所不同。虽然无法更新 const 对象，但可以更新此对象的属性。因此，如果我们这样声明一个 const 对象：

```javascript
const greeting = {
  message: 'say Hi',
  times: 4,
};
```

虽然我们不能这样做：

```javascript
greeting = {
  words: 'Hello',
  number: 'five',
}; // error:  Assignment to constant variable.
```

但可以这样操作：

```javascript
greeting.message = 'say Hello instead';
```

这将更新 greeting.message 的值而不返回错误。

#### const 的提升

就像 let 一样，const 声明被提升到顶部但没有被初始化。

### 总结

这三个声明方法有以下区别：

- var 声明是全局作用域或函数作用域，而 let 和 const 是块作用域。
- var 变量可以在其作用域内更新和重新声明；let 变量可以更新但不能重新声明；const 变量既不能更新也不能重新声明。
- 它们都被提升到了作用域的顶部。但是，var 变量是用 undefined 初始化的，而 let 和 const 变量不会被初始化。
- var 和 let 可以在不初始化的情况下声明，而 const 必须在声明时初始化。
