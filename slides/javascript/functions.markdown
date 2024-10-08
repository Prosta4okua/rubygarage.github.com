---
layout: slide
title:  Основи функції
---

![](/assets/images/javascript/javascript_logo.png)

---

# ФУНКЦІЇ

--

Загальний вигляд функції:

```javascript
function назваФункції(назваПараметру1, ..., назваПараметруN) {
    // інший код
}
```

<br>

Приклад:
```javascript
function sumTo(n) {
    let sum = 0;
    for (let i = 1; i <= n; i++) {
        sum += i;
    }
    return sum;
}
```

--

### Повернення значень

```javascript
function isEven(n) {
    if (n % 2 == 0) {
        return "парне число";
    }
    // в іншому випадку повертається undefined
}
```

--

## Важливо

<br>

- Не оголошуються типи параметрів та типи повернення
- Функція може повертати що завгодно
- Якщо функція не повертає нічого, то вона повертає значення undefined
- Функція може іноді повертати значення, а іноді ні

--

## Виклик функції

Загальний вигляд:

```javascript
назваФункції(параметрПерший, параметрДругий)
```

```javascript
function sumTo(n) {
    let sum = 0;
    for (let i = 1; i <= n; i++) {
        sum += i;
    }
    return sum;
}
```

Приклад:

```javascript
sumTo(6)                     // повертається 21
```

Передані додаткові параметри ігноруються

```javascript
sumTo(3, "hello", null, 42)  // повертається 6
```

Очікувані параметри не передано undefined :

```javascript
sumTo()                      // повертається 0
```

--
## Анонімна функція
Анонімна функція (лямбда-вираз, стрілочна функція) - це стислий спосіб визначення короткої функції в програмуванні.

```js

// звичайна функція
function multiply (a, b) {
    return a * b;
}
// лямбда-вираз
let multiply = (a, b) => a * b;
console.log(multiply(5, 9));
```
--

## Опціональні параметри

```javascript
function greet(name, msg) {
    if (typeof(msg) === "undefined") {
        msg = "радощів";
    }
    print('Бажаю' + 'msg + " тобі, " + name);
}
```

> ```javascript
greet("Лізо", "щастя"); // повертає "Бажаю щастя тобі, Лізо"
```

> ```javascript
greet("Софіє"); // повертає "Бажаю радощів тобі, Софіє"
```

--

## Об'єкт в якості аргументу

```javascript
function coffeeCost(argObj) {
    let finalSum = argObj["цінаКави"];

    if (argObj["податок"]) {
        finalSum += argObj["податок"];
    }
    if (argObj["чайові"]) {
        finalSum += argObj["чайові"];
    }
    if (argObj["пожертва"]) {
        finalSum += argObj["пожертва"];
    }

    return finalSum;
}
```

> ```javascript
const order1 = {
    "цінаКави": 50,
    "податок": 5,
    "чайові": 10
};
coffeeCost(order1) // повертає 65
```

> ```javascript
const order2 = {
    "цінаКави": 40,
    "податок": 4,
    "чайові": 8,
    "пожертва": 5
};
coffeeCost(order2); // повертає 57
```

--

## Оголошення функції: два способи

```js
function squared(x) {
    return x * x
}

const squared = function(x) {
    return x * x;
};
```


--
## Функція зворотного порядку та функція вищого порядку

Функція зворотного виклику (колбек, callback) — це функція, яка передається як аргумент іншій функції. Ця техніка дозволяє функції викликати іншу функцію.

Функція вищого порядку — це функція, яка приймає одну чи декілька функцій як аргументи або повертає функцію як результат.

```js
// Функція зворотного виклику, передана як параметр у функцію вищого порядку
function callbackFunction(){
    console.log('Я функція зворотного виклику');
}

// Функція вищого порядку
function higherOrderFunction(func){
    console.log('Я функція вищого порядку');
    func();
}

higherOrderFunction(callbackFunction);

function higherOrderFunctionSecond(){
    console.log('Я функція вищого порядку');
    return callbackFunction;
}

higherOrderFunctionSecond()()

```

--

## Вбудовані функції вищого порядку в масиві

- map: створює новий масив, викликаючи передану функцію для кожного елемента.
- filter: створює новий масив з елементами, які відповідають умові, заданій у функції.
- reduce: обчислює єдине значення, застосовуючи функцію до кожного елемента, зберігаючи проміжний результат.
- forEach: виконує функцію для кожного елемента масиву, не повертаючи нового масиву.

--

```js
// map: створює новий масив, викликаючи передану функцію для кожного елемента
const doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]

// filter: створює новий масив з елементами, які відповідають умові, заданій у функції
const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers); // [2, 4]

// reduce: обчислює єдине значення, застосовуючи функцію до кожного елемента, зберігаючи проміжний результат
const sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum); // 15

// forEach: виконує функцію для кожного елемента масиву, не повертаючи нового масиву
numbers.forEach(num => console.log(num * 2));
// Виведе: 2, 4, 6, 8, 10
```