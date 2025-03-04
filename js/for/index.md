---
title: "`for()`"
authors:
  - vindi-r
keywords:
  - итерация
  - обход
  - пробежать
  - cycle
  - iteration
  - фор
tags:
  - doka
---

## Кратко

Управляющая конструкция, которая создаёт [цикл](/js/loop/) .

## Как пишется

Описание цикла в коде выглядит так:

```js
for (инициализация; условие; завершающая операция) {
  // тело цикла
}
```

1. Инициализация — в этой части задаётся начальное значение счётчика цикла.

2. Условие — тут задаётся условие по которому выполняется цикл. Если условие ложно, работа цикла прекращается и тело цикла не выполняется.

3. Завершающая операция — в этой части задаётся выражение, которое будет исполнено после выполнения тела цикла. Обычно здесь содержится выражение изменения счётчика.

4. Тело цикла — это блок операций, которые будут выполнены в случае если условие истинно.

```js
for (let count = 5; count > 0; count--) {
  console.log(count)
}

// напечатает 5, 4, 3, 2, 1
```

## Пример

Создание разноцветных квадратов через цикл for:

<iframe title="Название — for() — Дока" src="demos/vindi-r-bJejME/"></iframe>

## Как это понять

Рассмотрим пример:

```js
for (let i = 0; i < 5; i++) {
  console.log("Счётчик равен: " + i)
}
```

Что произойдёт при запуске этого кода?

1. Один раз выполнится инициализация.

2. Потом создастся переменная `i` и ей присвоится значение 0, `let i = 0`. Эта переменная доступна только пока работает цикл, так как мы её объявили через `let`. Переменные созданные через `let` доступны только в рамках блока, где они созданы. В нашем случае блок — это тело цикла и шаги инициализации, условия и итоговой операции.

3. Идёт проверка условия `i < 5`. Значение переменной в текущий момент времени это 0, а 0 меньше 5, значит условие истинно.

4. Так как условие истинно, выполняется тело цикла: `console.log("Счётчик равен: " + i);`

В консоль будет выведено `"Счётчик равен: 0"`

5. После выполнения тела цикла идёт завершающая операция `i++` после которой значение переменной `i` увеличивается и становится равным 1.

Последующие шаги повторения цикла уже не включают в себя инициализацию. Сразу идёт проверка условия `i < 5` : 1 меньше 5, поэтому условие истинно.

Выполняется тело цикла. В консоль будет выведено `"Счётчик равен: 1"`

6. Выполняется завершающая операция `i++`. Переменная i становится равной 2

Пропустим описание шагов, когда переменная равна 2, 3 и 4, перейдём к этапу когда переменная i станет равной 5.

😴

7. Проверка условия `i < 5`. 5 < 5 и условие ложно. Выполнения тела цикла не происходит, как и завершающей операции.

На этом работа цикла заканчивается. Далее программа переходит к следующей за циклом инструкции.
