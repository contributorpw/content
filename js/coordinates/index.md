---
title: "Координаты"
authors:
  - windrushfarer
keywords:
  - координаты
  - позиционирование
tags:
  - doka
---

## Кратко

Чтобы перемещать и [позиционировать](/js/element-positioning-js/) элементы на экране в браузере имеется система координат. Оси координат начинаются в левом верхнем углу экрана и идут вправо для оси _x_ и вниз для оси _y_.

Позиционирование с помощью координат может быть относительно окна браузера или относительно отдельного элемента. Всего существует две системы координат: одна начинается от угла HTML-страницы  (документа), а вторая от угла окна браузера. С помощью первой можно определять как элемент расположен относительно всей страницы, а с помощью второй – как элемент расположен относительно окна браузера и того что там находится. Объекты события мыши и тач-события содержат координаты места на экране и в документе, где событие произошло: `pageX/pageY` – для документа, `clientX/clientY` – для экрана.

Координатами элемента является расстояние в пикселях от осей системы координат до его левого верхнего угла. С помощью метода элемента `getBoundingClientRect` можно получить подробные данные о координатах элемента и его размере.

## Как пишется

```js
document.addEventListener('click', event => {
  console.log('Позиция x относительно документа', event.pageX)
  console.log('Позиция y относительно документа', e.pageY)

  console.log('Позиция x относительно экрана', event.clientX)
  console.log('Позиция y относительно экрана', e.clientY)
}, false)

// { x: ..., y: ..., top: ..., left: ..., right: ..., bottom: ... }
const rect = element.getBoundingClientRect()
```

## Как понять

Система координат в браузера аналогична плоской системе координат из школьной алгебры. Есть две оси: ось _y_ и ось _x_, на этой плоскости располагаться все элементы сайта. Единственным отличием от классической системы координат является то, что положительное направление оси _y_ в браузере повёрнуто вниз. Это значит, что элементы с положительным значением по оси _y_ будут находится внизу относительно оси _x_, а с отрицательным – наверху.

Позиция элемента задаётся числом пикселей от начала системы координат по соответствующей оси.

Начало системы координат можно отсчитывать относительно окна браузера, либо относительно всего документа. Когда страница не прокручена, то начала этих осей совпадают в левом верхнем углу окна. Если прокручивать страницу вниз, то соответственно начало координат документа останется таким же, а начало оси координат окно будет смещаться. Такое разделение может быть полезно для разных задач, например можно анимировать элементы, только когда они попадают на экран, считая координаты относительно документа. А можно давать перетаскивать какой-либо элемент, но только в пределах окна браузера.

На рисунках `pageX` и `pageY` – оси системы координат относительно документа, а `clientX` и `clientY` – оси системы координат относительно окна браузера. Соответственно `pageXOffset` и `pageYOffset` – это смещение относительно всего документа, а `clientXOffset` и `clientYOffset` – относительно окна. На практике используются очень похожие названия, потому для текущих примеров будем использовать их.

Ниже схема осей координат, когда страница не прокручена. В таком состоянии оси совпадают, и координаты элементов относительно окна и относительно документа будут совпадать.

![схема когда оси координат совпадают](images/same_xy.png)

Но если прокрутить страницу (например вниз), но ситуация изменится. Начало документа уйдёт наверх, а значит и начало осей координат. Оси координат окна теперь будут начинаться там, где мы остановим прокрутку.

![схема когда оси координат совпадают](images/page_shift.png)

💡 Стоит обратить внимание на то, что координаты – это расстояние от осей до его верхнего левого угла. Потому стрелки на схеме начинаются от угла элемента с текстом Button.

## Смещение относительно окна браузера

В объекте события мыши из полей `clientX/clientY` можно узнать в каком месте относительно системы координат окна произошло событие, например [клик](/js/element-click).

Если нужно узнать как элемент расположен относительно окна, то в этом поможет метод `getBoundingClientRect`. Вызов этого метода возвращает объект с полями `x`, `y`, `top`, `left`, `right`, `bottom`, `width` и `height`, то есть полная информация о геометрии элемента. В полях `x` и `y` содержаться координаты элемента.

💡 Позиционирование относительно окна гораздо проще понять, если посмотреть, как располагается элемент с `position: fixed`. Элемент с этим свойством будет находиться в окне в одних и те же координатах, вне зависимости от того насколько прокручен документ.

## Смещение относительно документа

Если нужно получить данные в каком месте документа произошло событие, то это можно узнать из полей `pageX/pageY` в объекте события.

Информацию о том, как элемент расположен относительно документа нельзя узнать из какого-то свойства или метода, её необходимо вычислять самостоятельно. Самым простым способом это можно сделать сложив координаты относительно окна из метода `getBoundingClientRect` со смещением самого окна относительно документа. Смещение окна браузера можно узнать из полей `window.pageXOffset` и `window.pageYOffset` – это число пикселей на которое прокручен документ по горизонтали и вертикали.

```js
const rect = element.getBoundingClientRect()

console.log('Смещение X относительно документа:', rect.x + pageXOffset)
console.log('Смещение Y относительно документа:', rect.y + pageYOffset)
```

💡 Позиционирование относительно документа так же можно понять, если посмотреть как располагается элемент с `position: absolute`. При прокрутке окна этот элемент будет смещаться вместе с ним.

Наглядно как работают оси, и как располагаются элементы можно посмотреть в демо. В начальном состоянии положения осей и элементов, которые расположены относительно них совпадают. Оси относительно экрана сделаны крупнее, чтобы их было видно всегда. Если прокрутить страницу по вертикали или горизонтали будет видно как оси относительно экрана остаются на месте, а оси относительно документа уходят вместе с движением прокрутки.

<iframe title="Оси координат в браузере — Координаты — Дока" src="demos/axis/"></iframe>
