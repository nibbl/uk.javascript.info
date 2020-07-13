# Стрілкові функції, основи

Існує ще один простий та короткий синтаксис для створення функцій, який часто доцільніше використовувати замість Функціонального Виразу.

Це так звані "стрілкові функції", а виглядають вони ось так:

```js
let func = (arg1, arg2, ...argN) => expression
```

...Цей код створить функцію `func` з аргументами `arg1..argN`, що обчислює `expression` з правого боку (використовуючи ці аргументи) та повертає його результат.

Іншими словами, це приблизно те ж саме, що і:

```js
let func = function(arg1, arg2, ...argN) {
  return expression;
};
```

Розглянемо інший приклад:

```js run
let sum = (a, b) => a + b;

/* Ця стрілкова функція — це коротша форма для:

let sum = function(a, b) {
  return a + b;
};
*/

alert( sum(1, 2) ); // 3
```

Як ви бачите, `(a, b) => a + b` означає функцію, яка приймає два аргументи `a` і `b`. Після запуску, вона виконає вираз `a + b` і поверне результат.

- Якщо функція має лише один аргумент, тоді дужки навколо параметрів можна опускати, що дозволить записати її ще коротше.

    Наприклад:

    ```js run
    *!*
    let double = n => n * 2;
    // те ж саме, що і: let double = function(n) { return n * 2 }
    */!*

    alert( double(3) ); // 6
    ```

- Якщо аргументів немає, то дужки повинні бути порожніми (але вони повинні бути):

    ```js run
    let sayHi = () => alert("Привіт!");

    sayHi();
    ```

Стрілкові функції можна використовувати тим самим способом, що й Функціональні Вирази.

Наприклад, щоб динамічно створити функцію:

```js run
let age = prompt("Скільки вам років?", 18);

let welcome = (age < 18) ?
  () => alert('Привіт') :
  () => alert("Вітання!");

welcome();
```

Стрілкові функції можуть спершу здатись незвичними та незручними для читання, але це швидко мине, щойно очі звикнуть до таких конструкцій.

Вони дуже зручні для простих однорядкових дій, коли нам лінь писати багато слів.

## Багаторядкові стрілкові функції

У попередніх прикладах зліва від `=>` були аргументи, а справа — окремий вираз, що певним чином їх використовував.

Проте іноді, нам потрібно дещо складніше, наприклад, декілька виразів чи інструкцій. Це також можливо, але ми повинні записати їх в фігурних дужках і використати `return`, як у звичайних функціях.

Ось так:

```js run
let sum = (a, b) => {  // фігурна дужка починає блок багаторядкової функції
  let result = a + b;
*!*
  return result; // якщо ми використовуємо фігурні дужки, то "return" дозволить повернути результат
*/!*
};

alert( sum(1, 2) ); // 3
```

```smart header="І ще дещо..."
Тут ми розглянули лише основи стрілкових функцій. Це ще не все! Стрілкові функції мають й інші цікаві особливості. Щоб вивчити їх детальніше, нам потрібно дізнатися ще деякі аспекти JavaScript. Тому ми повернемось до стрілкових функцій пізніше у розділі <info:arrow-functions>.

А поки-що, ми можемо використовувати стрілкові функції для однорядкових дій та колбеків.
```

## Підсумки

Стрілкові функції зручні для однорядкових дій. Вони бувають двох видів:

1. Без фігурних дужок: `(...args) => expression` — права частина є виразом: функція виконує його і повертає результат.
2. З фігурними дужками: `(...args) => { body }` — дужки дозволяють включити в функцію більше однієї інструкції, але при цьому потрібно явно вказати `return`, щоб що-небудь повернути.