---
title: "`height`"
authors:
  - solarrust
contributors:
  - skorobaeus
keywords:
  - высота
  - размер
tags:
  - doka
---

## Кратко

Любой HTML-элемент сам по себе по высоте равен нулю. Обычно элементы подстраиваются по высоте под то количество контента, которое лежит у него внутри. Но что делать, если дизайнер придумал иначе, или если внутри вообще ничего нет?

При помощи свойства `height` можно задать высоту любому блочному (block) или строчно-блочному (inline-block) элементу. Высоту можно задавать как в абсолютных единицах (пикселях `px`) так и в относительных (проценты, `vh`, `vmin`, `rem` и так далее).

Помимо фиксированной высоты мы можем задать минимальную высоту элемента — `min-height`. В этом случае элемент сможет растягиваться на большую высоту, если того требует контент, размещённый внутри, но никогда не сожмётся по высоте меньше, чем указано в свойстве `min-height`.

Для максимальной высоты мы пишем свойство `max-height`. И тогда элемент будет иметь возможность растягиваться по высоте до тех пор, пока не достигнет размера, указанного в свойстве `max-height`. И дальше не растянется ни на пиксель.

## Пример

```html
<div class="container">
  <div class="item"></div>
</div>
```

```css
.container {
  height: 150px; /* высота родителя */
  padding: 25px;
  background-color: #AFC9DA;
}

.item {
  height: 50px; /* высота вложенного блока */
  margin: 0 10px;
  background-color: #FFFFFF;
}
```

<iframe title="Высота для блока" src="demos/basic/" height="200"></iframe>

Поскольку оба блока — `.container` и `.item` — пустые, в них нет контента, то без стилей их высота будет равна нулю. Мы изменили это, задав элементу `.container` высоту `150px`, а элементу `.item` высоту `50px`.

Добавим контент в элемент `.item`:

<iframe title="Высота для блока с текстом" src="demos/basic-w-text/" height="200"></iframe>

Из-за фиксированной высоты контент вываливается из блока. Как можно это исправить? Заменить `height` на `min-height`!

```css
.item {
  min-height: 50px; /* Меняем фиксированную высоту на минимальную */
  margin: 0 10px;
  background-color: #FFFFFF;
}
```

Теперь, если контента внутри не будет, то высота блока будет равна `50px`, но как только появится контент — элемент растянется по высоте так, чтобы уместить в себе весь контент!

<iframe title="Минимальная высота для блока с текстом" src="demos/min-height-w-text/" height="200"></iframe>

## Как это понять

С английского языка **height** переводится как высота.

Свойство `height` даёт возможность менять высоту любого блока на своё усмотрение.

## Как пишется

Пишем свойство `height` для фиксированной высоты, `min-height` для минимальной высоты и `max-height` для максимальной высоты.

Для элемента можно написать только одно из них, два или все три сразу, если это нужно для решения конкретной задачи.

В качестве значения пишем число, а за ним без пробела единицу измерения: `px`, `%`, `vh`, `rem`, `em` или любую другую единицу измерения, доступную в вебе.

```css
selector {
  height: 10px;
  min-height: 100%;
  max-height: 100vh;
}
```

## Подсказки

💡 Свойство высоты не наследуется.

💡 По умолчанию задаётся значение `auto`.

Это ключевое слово бывает полезно, когда нужно _сбросить_ высоту, заданную ранее. Например, оно пригодится при доработке сайта, к исходным стилям которого нет доступа.

Стили, до которых нет доступа с фиксированной высотой:

```css
.container {
  height: 150px;
}
```

Твои стили, где перезаписывается предыдущее значение: теперь высота подстраивается под контент.

```css
.container {
  height: auto;
}
```

Также оно может пригодится при адаптивной вёрстке.

💡 Не задавай фиксированную высоту блокам, в которых есть контент. Если контента завтра станет больше, то блок не растянется и контент из него выпадет. Не надо так. Если без высоты никак не обойтись, то используйте `min-height`.

💡 Строчные элементы не реагируют на `height`. Хочешь изменить высоту? Меняй элемент со строчного (inline) на блочный (block) или строчно-блочный (inline-block)!

💡 Пишешь `height: 100%` и ничего не работает? Помни, что высота в процентах рассчитывается от высоты родителя. И сработает, только если у родителя задана эта самая высота.

Отношения родительский-дочерний элемент проще объяснить на примере.

```html
<div class="parent">
  <div class="child child-1">
    <div class="grandchild"></div>
  </div>
  <div class="child"></div>
  <div class="child"></div>
</div>
```

В примере выше элемент с классом `parent` является родительским для элементов с классом `child`. Они, в свою очередь, будут называться дочерними по отношению к элементу с классом `parent`.

Для элемента с классом `grandchild` родительским будет элемент с классом `child-1`.

Применительно к нашей ситуации элемент `grandchild` будет наследовать свою высоту от элемента `child-1`.
