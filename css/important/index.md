---
title: "!important"
authors:
  - solarrust
editors:
  - tachisis
keywords:
  - модификатор
  - переопределение специфичности
tags:
  - doka
---

## Кратко

Уникальный модификатор, позволяющий применить значение свойства вопреки обычной [специфичности](/css/specificity) и [каскаду](/css/cascade).

## Пример

```css
.text {
  color: green !important;
}

.text {
  color: red;
}
```

По логике каскада текст в блоке с классом `text` должен быть красного цвета, потому что это правило стоит ниже в коде. Но из-за модификатора `!important` цвет текста будет зелёным.

```css
#main-title {
  color: purple;
}

.title {
  color: blue !important;
}
```

В этом примере селектор `#main-title` более специфичный, чем `.title`. Но цвет текста будет голубым из-за `!important`.

## Как пишется

Модификатор `!important` можно написать после любого значения, чтобы _прибить это значение гвоздями_. Важно написать его через пробел после значения и до точки с запятой.

## Как понять

Модификатор `!important` — последний аргумент в споре стилей. С ним нужно обращаться очень аккуратно. Перед тем как использовать его в своём коде, убедитесь, что иначе никак.

Вот часто встречающийся сценарий:

1. Хм, почему мои великолепные стили не применяются?
1. Использую-ка `!important`.
1. Теперь всё отлично!

Но делать так не стоит. Лучше потратить время и разобраться в исходной причине.

Использовав `!important`, вы подставите подножку себе или следующему разработчику, пришедшему на проект — перебить его будет катастрофически сложно.

## Зачем он нужен?

Раз инструмент существует, значит, для его появления были причины. Иногда `!important` действительно оказывался полезным.

### Легаси

Если вы работаете с проектом, в котором большая и старая кодовая база, то бывает опасно править существующие стили — кто знает, что может посыпаться. В таких ситуациях новые стили дописывают, чтобы переопределить старые, а если не хватает специфичности — добавляют `!important`.

### Браузерные расширения

Предположим, вы участвуете в разработке браузерного расширения, которое добавляет на страницу какой-то элемент. Чтобы стили вашего расширения не конфликтовали и не были переопределены стилями самого сайта, допустимо использовать `!important`.

## Как перебить правило с `!important`

### Специфичный селектор

Используйте более специфичный селектор в сочетании с `!important`:

```css
h2 span {
  font-size: 50px !important;
}

#main-title span {
  font-size: 20px !important;
}

.title span {
  font-size: 10px !important;
}
```

Хотя во всех трёх CSS-правилах используется `!important`, размер шрифта будет 20 пикселей, потому что селектор `#main-title span` «весит» больше остальных.

### Каскад

Напишите ниже в коде точно такое же правило вместе с `!important`, но с другим значением свойства.

```css
h2 span {
  font-size: 50px !importnat;
}

h2 span {
  font-size: 10px !importnat;
}
```

В этой борьбе выиграет правило, стоящее ниже — из-за каскадной натуры стилей. Размер текста будет 10 пикселей.

## Подсказки

💡 Если вам пришлось использовать `!important` в коде, то это сигнал о серьёзных проблемах. Потратьте время и найдите первопричину. Приложите усилия, чтобы не использовать этот модификатор.
