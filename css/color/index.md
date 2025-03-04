---
title: "`color`"
authors:
  - grachev
contributors:
  - vladimir
  - pepelsbey
  - furtivite
  - skorobaeus
keywords:
  - color
  - цвет
  - rgb
  - rgba
  - hsl
  - hsla
  - hex
  - currentColor
  - transparent
tags:
  - doka
---

## Кратко

Свойство `color` задаёт цвет текста.

## Пример

Наследует значение свойства `color` у ближайшего родителя, у которого оно указано:

```css
.element {
  color: currentColor;
}
```

Задаёт значение по названию цвета:

```css
.element {
  color: red;
  color: orange;
  color: tan;
  color: rebeccapurple;
}
```

HEX-код цвета, 3- или 6-символьные для сплошных и 4- и 8-символьные для полупрозрачных:

```css
.element {
  color: #090;
  color: #009900;
  color: #090a;
  color: #009900aa;
}
```

Значение RGB в старом синтаксисе `rgb` для сплошных и `rgba` для полупрозрачных:

```css
.element {
  color: rgb(34, 12, 64);
  color: rgba(34, 12, 64, 0.6);
}
```

Значение RGB в новом синтаксисе `rgb` для сплошных и для полупрозрачных:

```css
.element {
  color: rgb(34 12 64);
  color: rgb(34 12 64 / 0.6);
  color: rgb(34 12 64 / 60%);
}
```

Значение HSL в старом синтаксисе `hsl` для сплошных и `hsla` для полупрозрачных:

```css
.element {
  color: hsl(30, 100%, 50%);
  color: hsla(30, 100%, 50%, 0.6);
}
```

Значение HSL в новом синтаксисе `hsl` для сплошных и для полупрозрачных:

```css
.element {
  color: hsl(30 100% 50% / 0.6);
  color: hsl(30 100% 50% / 60%);
}
```

Наследует цвет у родительского элемента:

```css
.element {
  color: inherit;
}
```

## Как это понять

Любому элементу веб-страницы можно задать свой цвета текста. Свойство `color` задаёт его для текста, а также для элементов его оформления, например, подчёркивания, линии над текстом, перечёркивания и других.

Чтобы задать фон текста, используйте свойство [`background-color`](/css/background-color/), а рамки элемента можно раскрасить с помощью `border-color`.

## Как пишется

Цвет можно задать с помощью названия цвета, в формате HEX, RGB, HSL или с помощью ключевых слов.

### Название цвета

Можно использовать название цвета или его оттенка на английском [из списка именованных цветов](https://www.w3.org/TR/css-color-4/#named-colors). Это базовый набор непрозрачных цветов, например, красный `red`, синий `blue`, оранжевый `orange`, чёрный `black`, тёмно-серый `darkgray`, светло-серый, `lightgrey`, белый `white`, а также смешанные цвета, вроде цвета морской волны `lightseagreen`, василькового `cornflowerblue` или томатного `tomato`.

### HEX-код

Шестнадцатеричный код цвета в цветовой модели RGB, который начинается с `#`, например, `#ff0000`. Сплошные цвета записываются в формате `#RRGGBB` или в сокращённом `#RGB` (если символы каждой группы одинаковые). Например `#009900` или `#090`. Если нужно указать прозрачность, она добавляется в конце в HEX-формате `#RRGGBBAA` или `#RGBA`, например `#00990055` или `#0905`.

Раньше нельзя было задать цвет в нотации `#RGBA` и приходилось использовать функцию `rgba()`, но сегодня у этого способа [неплохая кроссбраузерность](https://caniuse.com/css-rrggbbaa). Проблема одна: мало кто сходу сможет рассчитать 50% в шестнадцатеричном формате, поэтому для указания прозрачности цвета чаще всего используют функцию `rgb()`, где прозрачность можно задать в дробях или процентах.

### Формат RGB

Для задания цвета используется функция `rgb()`, например, `rgb(0 63 255)` для синего. Каждое из трёх значений отвечает за отдельный канал RGB и может быть записано числом от 0 до 255 или в процентах. Для добавления прозрачности, после записи каналов нужно поставить слэш и записать нужное значение от 0 до 1 или в процентах, например `rgb(0 63 255 / 0.5)` для полупрозрачного синего.

Раньше синтаксис RGB отличался от современного и вы всё ещё можете встретить его в коде или выбрать для лучшей кроссбраузерности, [см. Can I Use](https://caniuse.com/mdn-css_types_color_rgb_function_accepts_alpha). Для разделения каналов внутри функции нужно было использовать запятые `rgb(0, 63, 255)`, а для добавления прозрачности — специальную функцию `rgba()`, которая принимала последним параметром прозрачность цвета, например `rgba(255, 0, 0, 0.5)`.

### Формат HSL

Цветовая модель HSL описывает те же цвета, что и HSL, но иначе: H — Hue (оттенок), S — Saturation (насыщенность), L — Lightness (светлота). Например, `hsl(120 100% 50%)` для зелёного. Первое значение оттенка задаётся в градусах и его можно записать просто как `120` (как чаще всего и делают) или с указанием единицы `120deg`, второе и третье значение указываются в процентах. Прозрачность добавляется так же, как в `rgb`, с помощью слэша со значением, например `hsl(120 100% 50% / 0.5)` полупрозрачный зелёный.

Синтаксис `hsl()` отличался от современного точно так же, как `rgb()`: нужны были запятые и специальная функция `hsla()` для задания прозрачности цвета. Используйте старый синтаксис для лучшей совместимости и не удивляйтесь, если встретите его в коде.

### Ключевые слова

Ключевое слово `transparent` задаёт прозрачный цвет текста. Технически это равносильно записи любого цвета с нулевой прозрачностью `rgb(0 0 0 / 0)`, но бывают случаи, когда просто прозрачность и прозрачность цвета могут работать иначе, например, в градиентах.

## Подсказки

💡 Ничего лучше чёрного текста на белом фоне пока не придумали. Или белого на чёрном, если читаешь ночью. Убедись, что цвет текста выглядит контрастно на заданном фоне, [лучше даже проверить](https://contrast-ratio.com/).

💡 Лучше всегда доверять выбор цвета профессионалам, но иногда мы делаем проект для себя и нам нужно сделать хорошую подборку цветов для проекта. В этом случае лучше всего не изобретать велосипед, а воспользоваться уже подходящими опенсорсными подборками:

  - [Material Design Color System](https://material.io/design/color/the-color-system.html#color-theme-creation)
  - [Ubuntu Color System](https://design.ubuntu.com/brand/colour-palette/)
  - [Color Hex Color Codes](https://www.color-hex.com/)

  - [RGBto](http://rgb.to/)
  - [Colormind](http://colormind.io/)

  Или создать что-то своё, но под руководством профессионалов. Например:

  - [Paletton](http://paletton.com/)

  И отдельно присмотритесь к сервисам, которые умеют подбирать безопасные цвета для людей с особенностями их восприятия:

  - [Colorsafe](http://colorsafe.co/)
  - [Цветовое колесо от Adobe](https://color.adobe.com/ru/create/color-wheel)
  - [Color Scheme](https://colorscheme.ru/)

💡 Ключевое слово `currentColor` нужно, чтобы использовать текущий или унаследованный цвет текста в других местах, где можно указать цвет фона, рамки и прочего, например:

```html
<div class="parent">
  Мы сделали этот текст зелёным с помощью свойства «color». Рамки блока
  наследуют цвет от текста.
  <div class="child"></div>
  Блок выше 👆 тоже наследует фоновый цвет от текста, для которого задано
  свойство «color».
</div>
```

```css
.parent {
  color: #49a16c;
  border-top: 1px solid currentColor;
  border-bottom: 1px solid currentColor;
}

.child {
  background: currentColor;
  height: 110px;
}
```

<iframe title="Текущий цвет" src="demos/currentcolor/" height="430"></iframe>

## Подсказки

💡 Свойство цвета можно анимировать при помощи `transition` 🎉

💡 Если вам нужно задать полупрозрачный текст, используй значение с указанием альфа-канала. Не используй для этих целей `opacity`. Иначе при добавлении в элемент другого контента, например, иконки, он тоже станет полупрозрачным. Это, скорее всего, не входило в твои планы.
