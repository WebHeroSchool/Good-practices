# JavaScript Good practices

*Некоторые установленные best practice*

## Правила

1. Никогда не объявляйте `Number`, `String`, `Boolean` объекты.
2. Всегда пользуйтесь `;` в конце строк кода.
3. Используйте `===` и `!==` (строгое сравнение ), вместо `==` и `!=` (нестрогое сравнение).
4. Размещайте ваш скрипт в конце страницы
5. Не используйте `eval()`;
6. Не переносите строку после оператора присваивания.
7. Используйте `'use strict'` в js.
8. Используйте camelCase для названий переменных, объектов и функций.
9. Всегда используйте `let` или `const` для объявления переменных, не используйте `var`.
10. Объявляйте переменные вначале функций или сценариев.
___
## Подробнее

### 1. Никогда не объявляйте `Number`, `String`, `Boolean` объекты.
##### Всегда обрабатывайте числа, строки или логические значения в качестве примитивных значений. Не как объекты.

##### Объявление этих типов как объектов, замедляет скорость выполнения и создает неприятные побочные эффекты:

✔ **Хорошо**
```js
let x1 = {};
let x2 = "";
let x3 = 0;
let x4 = false;
let x5 = [];
let x6 = /()/;
let x7 = function(){};
```
❌ **Плохо**
```js
let x1 = new Object();
let x2 = new String();
let x3 = new Number();
let x4 = new Boolean();
let x5 = new Array();
let x5 = new RegExp();
let x7 = new Function();
```

### 2. Всегда пользуйтесь `;` в конце строк кода.
✔ **Хорошо**
```js
let someItem = 'some string';
function doSomething() {
  return 'something';
}
```
❌ **Плохо**
```js
let someItem = 'some string'
function doSomething() {
  return 'something'
}
```

### 3. Используйте `===` и `!==` (строгое сравнение ), вместо `==` и `!=` (нестрогое сравнение).
✔ **Хорошо**
```js
typeof foo === 'undefined'
'hello' !== 'world'
0 === 0
true === true
foo === null
```
❌ **Плохо**
```js
a == b 
foo == true
bananas != 1
value == undefined
```

### 4. Размещайте ваш скрипт в конце страницы.
##### Если вам приходится копировать и вставлять блок кода, это признак того, что данный блок можно выделить в отдельную функцию.
✔ **Хорошо**
```js
  <body>
    <p>And now you know my favorite kinds of corn. </p>
    <script type="text/javascript" src="path/to/file.js"></script>
    <script type="text/javascript" src="path/to/anotherFile.js"></script>
  </body>
</html>
```
❌ **Плохо**
```js
    <script type="text/javascript" src="path/to/file.js"></script>
    <script type="text/javascript" src="path/to/anotherFile.js"></script>
  </head>
  <body>
    <p>And now you know my favorite kinds of corn. </p>
  </body>
</html>
```
### 5. Не используйте `eval()`;
##### Использование eval () в ненадежном коде может открыть программу для нескольких различных инъекционных атак. Использование eval () в большинстве случаев может заменить лучший альтернативный подход к проблеме.
✔ **Хорошо**
```js
let value = eval('object.' + aProperty); //not compliant
```
❌ **Плохо**
```js
let value = object[aProperty]; //compliant
```
### 6.  Не переносите строку после оператора присваивания.
✔ **Хорошо**
```js
const foo =
  superLongLongLongLongLongLongLongLongFunctionName();
```
❌ **Плохо**
```js
const foo = (
  superLongLongLongLongLongLongLongLongFunctionName()
);
```
### 7. Используйте `'use strict'` в js.
##### Строгий режим не разрешает необъявленные переменные.
✔ **Хорошо**
```js
"use strict"; // could have unforeseen effects

b = 'John';
console.log(b); //выведет ошибку, что переменная не объявлена
```
❌ **Плохо**
```js
name = 34;
```

### 8. Используйте camelCase для названий переменных, объектов и функций.
✔ **Хорошо**
```js
const thisIsMyObject = {};
function thisIsMyFunction() {}
```
❌ **Плохо**
```js
const OBJEcttsssss = {};
const this_is_my_object = {};
function 1234c() {}
```

### 9. Всегда используйте `let` или `const` для объявления переменных, не используйте `var`.
✔ **Хорошо**
```js
const superPower = new SuperPower();
```
❌ **Плохо**
```js
uperPower = new SuperPower();
var number = 4;
```

### 10. Объявляйте переменные вначале функций или сценариев.
##### Это хорошая практика кодирования, помещая все объявления в верхней части каждого сценария или функции.

✔ **Хорошо**
```js
let container = document.getElementById('container');
 for(let i = 0, len = someArray.length; i < len;  i++) {
    container.innerHtml += 'my number: ' + i;
    console.log(i);
 }
```
❌ **Плохо**
```js
for(let i = 0; i < someArray.length; i++) {
    let container = document.getElementById('container');
    container.innerHtml += 'my number: ' + i;
    console.log(i);
 }
```