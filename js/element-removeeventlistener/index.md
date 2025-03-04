---
title: "`Element.removeEventListener()`"
authors:
  - vindi-r
contributors:
  - nlopin
  - skorobaeus
  - akellbl4
tags:
  - doka
---

## Кратко

Удаляет обработчик события с элемента, установленный с помощью [`Element.addEventListener`](/js/element-addeventlistener).

## Как пишется

Добавим обработчик на элемент, а затем удалим его.

Например, будем обрабатывать клики на любое место на странице, а затем удалим обработчик, передав в `removeEventListener` те же аргументы, что и при добавлении:

```js
function handleMouseClick(event) {
  console.log('Вы нажали на элемент:', event.target)
}

// Добавляем обработчик события
window.addEventListener('click', handleMouseClick)

// Убираем обработчик события
window.removeEventListener('click', handleMouseClick)
```

<iframe title="Удаление обработчика событий — Element.removeEventListener() — Дока" src="demos/index/"></iframe>

`Element.removeEventListener` принимает три аргумента. Первые два обязательные:

- название события в виде строки
- функция-обработчик, которую нужно убрать с указанного события

Третий аргумент необязательный — это объект с настройками в котором могут содержаться свойства `capture` и `passive` с булевыми значениями `true` либо `false`. Точно такие же опции, можно передать и в `Element.addEventListener`.

```js
window.addEventListener('click', handleMouseClick, {
  capture: true,
  passive: true
})

// Аналогичные опции при удалении обработчика
window.removeEventListener('click', handleMouseClick, {
  capture: true,
  passive: true
})
```

Переданные настройки влияют на удаление обработчика события. Мы рекомендуем повторять в точности те же параметры, которые использовались в `Element.addEventListener`, чтобы браузер точно знал какой обработчик нужно удалить.

Например, создадим обработчик события и передадим третьим аргументом в опциях значение `true`. Если попробовать убрать событие, но ничего не передать в опциях в `Element.removeEventListener`, то событие не уберётся.

```js
function handleMouseClick(event) {
  console.log('Вы нажали на элемент:', event.target)
}

window.addEventListener('click', handleMouseClick, true)

// Ничего не передаем в опциях в третьем аргументе
window.removeEventListener('click', handleMouseClick)
```

Аналогичная ситуация, если делать наоборот.

## Как это понять

Браузер даёт возможность не только устанавливать обработчик события, но и убирать их.

Очищать обработчики событий важно, потому что каждый обработчик занимает место в памяти и выполняется всякий раз, когда срабатывает событие. Если не убирать неиспользуемые обработчики событий, то можно столкнуться с неожиданным поведением. Например, один из старых обработчиков будет мешать всплытию события наверх, и другой обработчик не будет работать.

::: callout 👇

Хорошим тоном считается убирать обработчик сразу же, как он перестал быть нужен.

:::

Будет ли на самом деле удалён обработчик события зависит от того, какую функцию и какие опции передали вторым и третьим аргументами в `Element.removeEventListener`.

Функции относятся к [ссылочным типам данных](/js/ref-type-vs-value-type), а значит две одинаково написанные функции будут считаться различными. Поэтому, если ранее в `Element.addEventListener` использовалась анонимная функция, то убрать обработчик с помощью `Element.removeEventListener` не получится.

```js
window.addEventListener('click', (event) => {
  console.log('Клик!')
})

// Обработчик не будет удалён!
window.removeEventListener('click', (event) => {
  console.log('Клик!')
})
```

Всегда сохраняйте функцию-обработчик в переменную чтобы позже убрать обработчик. Делать это необязательно только если вы делаете быстрый прототип или проверяете свою идею прямо в браузере.

Браузер сравнивает опции, когда ищет обработчик события для удаления. Посмотрим ещё раз на пример выше, когда в `addEventListener` передали в опциях `true`, а в `removeEventListener` нет опций.

```js
function handleMouseClick(event) {
  console.log('Вы нажали на элемент:', event.target)
}

window.addEventListener('click', handleMouseClick, true)

// Обработчик не удалится, потому что опции не совпадают
window.removeEventListener('click', handleMouseClick)
```

Так происходит потому что третий аргумент неявно устанавливается в `undefined`, а `undefined` превращается в `false` при конвертации в булевый тип. Когда браузер ищет обработчик на удаление, он сравнивает опции и видит, что `true !== false`, значит обработчик не будет удалён.
