---
title: "Функции фильтров"
description: "Список функций, с помощью которых можно задать фильтры картинкам. Почти как в Инстаграме"
authors:
  - solarrust
tags:
  - doka
---

## Кратко

CSS позволяет накладывать поверх картинок или фонов различные фильтры. Почти как в Инстаграме. Можно, например, размыть или обесцветить изображение, сделать его более контрастным.

Функции используются в качестве значений для свойств [`filter`](/css/filter) и [`backdrop-filter`](/css/backdrop-filter).

## Пример

```css
div {
  filter: saturate(2.2);
}
```

## Как пишется

### `blur()`

Примеряет размытие Гаусса к изображению. Значение в скобках указывает сколько пикселей сливаются друг с другом. Чем больше значение, тем больше размытие. Можно указать положительное значение в любых единицах измерения, кроме процентов.

```css
img {
  filter: blur(3px);
}
```

<iframe title="Функция blur()" src="demos/blur/" height="150"></iframe>

### `brightness()`

Меняет яркость изображения. В скобках можно указать любое значение от 0% и выше. Значение 0% сделает изображение полностью чёрным. Значение 100% вернёт изображению исходную яркость. Значение больше 100% _выкрутит_ яркость картинки. Значением может быть целое или дробное число без единиц измерения.

```css
img {
  filter: brightness(30%);
}
```

<iframe title="Функция brightness()" src="demos/brigtness/" height="150"></iframe>

### `contrast()`

Меняет контраст изображения. В скобках можно указать любое значение от 0% и выше. Значение 0% сделает изображение полностью чёрным. Значение 100% вернёт изображению исходный контраст. Значение больше 100% усилит исходный контраст. Значением может быть целое или дробное число без единиц измерения.

```css
img {
  filter: contrast(250%);
}
```

<iframe title="Функция contrast()" src="demos/contrast/" height="150"></iframe>

### `drop-shadow()`

Задаёт тень для картинки. Тень располагается снаружи элемента. Эта функция очень похожа на [`box-shadow`](/css/box-shadow) по допустимым значениям и результату. Разница лишь в том, что нельзя указывать ключевое слово `inset`.

```css
img {
  filter: drop-shadow(4px 4px red);
}
```

<iframe title="Функция drop-shadow()" src="demos/drop-shadow/" height="150"></iframe>

### `grayscale()`

Делает изображение чёрно-белым. В скобках можно указать значение от 0% до 100%. Значение 100% сделает изображение полностью чёрно-белым. Значение 0% вернёт изображению исходные цвета. Значением может быть целое или дробное число без единиц измерения.

```css
img {
  filter: grayscale(80%);
}
```

<iframe title="Функция grayscale()" src="demos/grayscale/" height="150"></iframe>

### `hue-rotate()`

Меняет цвета изображения за счёт поворота цветового круга. Угол поворота указывается в скобках функции. Можно указывать угол в градусах `deg` или в поворотах `turn`.

```css
img {
  filter: hue-rotate(0.5turn);
}
```

<iframe title="Функция hue-rotate()" src="demos/hue-rotate/" height="150"></iframe>

### `invert()`

Инвертирует цвета изображения, как бы выворачивает их, превращая в противоположные. В результате получается что-то вроде негатива. Можно указать процент инверсии от 0% до 100%. При 100% цвета на картинке полностью инвертированы. Отрицательные значения или значения больше 100% не допускаются.

```css
img {
  filter: invert(100%);
}
```

<iframe title="Функция invert()" src="demos/invert/" height="150"></iframe>

### `opacity()`

Меняет прозрачность изображения. Можно указать процент прозрачности от 0% до 100%. 0% делает картинку полностью прозрачной. 100% не меняет прозрачность изображения. Отрицательные значения или значения больше 100% не допускаются.

Очень похоже на работу свойства [`opacity`](/css/opacity) с той разницей, что для фильтра браузер, как правило, применяет аппаратное ускорение для улучшения производительности.

```css
img {
  filter: opacity(40%);
}
```

<iframe title="Функция opacity()" src="demos/opacity/" height="150"></iframe>


### `saturate()`

Меняет насыщенность цветов изображения. Значение 0% полностью убирает насыщенность цветов. Значение 100% не изменяет исходное изображение. Допускаются значения больше 100% что приводит к перенасыщенности. Нельзя указать отрицательное значение.

```css
img {
  filter: saturate(390%);
}
```

<iframe title="Функция saturate()" src="demos/saturate/" height="150"></iframe>

### `sepia()`

Меняет цвета изображения на сепию — коричневые оттенки. Значение 100% полностью преобразует изображение в сепию. Значение 0% не изменяет исходное изображение. Отрицательные значения или значения больше 100% не допускаются. Можно использовать целое или дробное число без единиц измерения в качестве значения.

```css
img {
  filter: sepia(0.6);
}
```

<iframe title="Функция sepia()" src="demos/sepia/" height="150"></iframe>

## Подсказки

💡 Можно указать сразу несколько фильтров для одного элемента, перечислив их через пробел.
