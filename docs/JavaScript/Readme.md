# JavaScript

## Общее

- Не используйте магические числа. Выносите все значения в именованые
  константы, имя которых позволяет понять предназначение этого числа
  или то, откуда оно взялось

  ```javascript
  /* Недопустимо */
  setTimeout(callback, 86400000)

  /* Правильно */
  var MILLISECONDS_IN_DAY = 86400000
  setTimeout(callback, MILLISECONDS_IN_DAY)
  ```

## Условия

- Используйте строгое сравнение (`===`), вместо `==`.
  Строгое сравнение не приводит оба операнда к одному типу,
  что позволяет избежать ряда различных неочевидных проблем.

  ```javascript
  /* Недопустимо */
  if (a == b) {
    ...
  }

  /* Правильно */
  if (a === b) {
    ...
  }
  ```

- Если всё тело или большая часть тела функции содержится внутри
  какого-либо `if`, то заменяйте условие на обратное и делайте
  ранний выход из функции. Это позволяет уменьшить вложенность кода,
  что делает его проще для чтения.

  ```javascript
  /* Недопустимо */
  function fn(arg) {
    if (arg) {
     // ...
    }
  }

  /* Правильно */
  function fn(arg) {
    if (!arg) {
      return
    }

    // ...
  }
  ```

- Избавляйтесь от условия, если ветки условия отличаются только каким-либо
  булевым значением. Присвойте переменной само условие или его отрицание:

  ```javascript
  /* Недопустимо */
  function fn1(arg) {
    if (argument === 5) {
      return true
    } else {
      return false
    }
  }
  function fn2(arg) {
    var needCheck

    if (argument === 5) {
      needCheck === false
    } else {
      needCheck === true
    }

    if (needCheck) {
      ...
    }

    ...
  }

  /* Правильно */
  function fn1(arg) {
    return argument === 5
  }
  function fn2(arg) {
    var needCheck = argument !== 5 // обратное условие

    if (needCheck) {
      ...
    }

    ...
  }
  ```
- Избавляйтесь от условия, если в ветках содержится только присвоение значения
  переменной. В таких случаях условие можно заменить на тернарный оператор.

  ```javascript
  /* Недопустимо */
  function fn1(arg) {
    var a

    if (argument === 5) {
      a = 7
    } else {
      a = 8
    }
  }
  function fn2(arg) {
    var a = 8

    if (argument === 5) {
      a = 7
    }
  }

  /* Правильно */
  function fn(arg) {
    var a = argument === 5 ? 7 : 8
  }
  ```

- Избавляйтесь от множественных условий, если проверки заключаются в проверке
  какой-либо переменной на какое-то значение и если ветки содержат только
  одно действие. Заменяйте условие на объект \ массив:

  ```javascript
  /* Недопустимо */
  function fn1(arg) {
    var a

    if (arg === 0) {
      a = 5
    } else if (arg === 1) {
      a = 3
    } else if (arg === 2) {
      a = 4
    } else {
      a = 1
    }
  }
  function fn2(arg) {
    switch(arg) {
      case 'A':
        return someFunc1()
      case 'B':
        return someFunc2()
      case 'C':
        return someFunc3()
      default:
        return someDefaultFunc()
    }
  }

  /* Правильно */
  function fn1(arg) {
    var values = [5, 3, 4]
    var a = values[arg] || 1
  }
  function fn2(arg) {
    var fnByArg = {
      A: someFunc1,
      B: someFunc2,
      C: someFunc3,
    }
    var fn = fnByArg[arg] || someDefaultFunc

    return fn()
  }
  ```

## Циклы, работа с коллекциями

Не используйте циклы. В большинстве случае они не нужны и заменяются
на `map`, `filter`, `reduce` и прочие методы. Стандартные методы работают
только с массивами, но есть отдельные библиотеки для работы с данными,
которые позволяются работать и с объектами — Lodash или Ramda.

В этих же библиотеках содержится множество полезных методов,
которые решают частовстречаемые задачи по работе с коллекциями.

- Используйте `map` когда необходимо преобразовать один массив (или объект)
  в другой одинаковой длины и когда каждому элементу исходного
  массива соответствует один элемент из нового массива.

  ```javascript
  /* Недопустимо */
  var newArr = []
  for (var i = 0; i < oldArr.length; i++) {
    var newItem = oldArr[i] + 1
    newArr.push(newItem)
  }

  /* Правильно */
  var newArr = oldArr.map(function(item) {
    return item + 1
  })
  ```

- Используйте `filter`, когда нужно отфильтровать массив
  по какому-либо критерию.
  Аналогом метода `filter` для объектов является функция `pickBy`.

  ```javascript
  /* Недопустимо */
  var newArr = []
  for (var i = 0; i < oldArr.length; i++) {
    if (item % 2 === 0) {
      newArr.push(item)
    }
  }

  /* Правильно */
  var newArr = oldArr.filter(function(item) {
    return item % 2 === 0
  })
  ```

- Используйте `reduce` для всех остальных преобразований.
  Например, преобразовать массив в число или массив в объект.

  ```javascript
  /* Недопустимо */
  var sum = 0
  for (var i = 0; i < oldArr.length; i++) {
    sum += oldArr[i]
  }

  /* Правильно */
  var newArr = oldArr.reduce(function(acc, item) {
    return acc + item
  })
  ```

- Не используйте `forEach` в тех случаях, когда вы меняете какие-то значения
  в глобальных переменных, объявленных ранее.
  Такое преобразование, как правило, можно заменить на `reduce`.

  ```javascript
  /* Недопустимо */
  var sum = 0
  oldArr.forEach(function(item) {
    sum += item
  })

  /* Правильно */
  var newArr = oldArr.reduce(function(acc, item) {
    return acc + item
  })
  ```

- Не используйте `reduce` в тех случаях, когда преобразование можно
  записать через цепочку `map` и `filter`. Лучше использовать цепочку,
  каждый элемент которой будет делать одну задачу.

  ```javascript
  /* Недопустимо */
  var newArr = oldArr.reduce(function(acc, item) {
    if (item % 2 === 0) {
      return acc
    }

    var newItem = item * 2
    acc.push(newItem)
    return acc
  }, [])

  /* Правильно */
  var newArr = oldArr
    .filter(function(item) {
      return item % 2 !== 0
    })
    .map(function(item) {
      return item * 2
    })
  ```

## Функции

- Создавайте функции, которые решают только одну задачу.
- Обращайте внимание на [цикломатическую сложность][complexity] ваших функций.
  Большое число указывает на то, что у функции есть много вариантов выполнения,
  а значит такая функция сложна для чтения и понимания.
- Делайте большинство функций чистыми — такими, которые получают все
  необходимые данные через свои аргументы (то есть, они не берут никаких
  данных из глобальных переменных) и которые только возвращают результат
  (и никак не влияют на внешнее состояние). Такие функции, как правило,
  более просты и понятны и их легче тестировать.


[complexity]: https://ru.wikipedia.org/wiki/%D0%A6%D0%B8%D0%BA%D0%BB%D0%BE%D0%BC%D0%B0%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F_%D1%81%D0%BB%D0%BE%D0%B6%D0%BD%D0%BE%D1%81%D1%82%D1%8C
