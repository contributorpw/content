---
title: "`:checked`"
authors:
  - solarrust
contributors:
  - skorobaeus
editors:
  - tachisis
keywords:
  - псевдокласс
  - :checked
tags:
  - doka
---

## Кратко

Псевдокласс, который активируется, когда пользователь отмечает чекбокс или выбирает одну из радиокнопок.

С его помощью удобно стилизовать эти элементы в их активном состоянии.

## Пример

Будем менять обводку и цвет текста у чекбокса, когда он отмечен:

```html
<label>
  <input type="checkbox">
  <span class="input-text"> Чекбокс (нажми!) </span>
</label>
```

```css
/* Белая обводка в дефолтном состоянии */
input[type="checkbox"] {
  outline: 2px solid #ffffff;
}

/* Обводка становится синей, когда на чекбокс кликнули */
input[type="checkbox"]:checked {
  outline: 2px solid #1a5ad7;
}

/* Цвет текста тоже меняется на синий */
input[type="checkbox"]:checked ~ .input-text {
  color: #1a5ad7;
}
```

<iframe title="Чекбоксы" src="demos/check/" height="350"></iframe>

## Как пишется

После селектора, который выбирает элемент чекбокса или радиокнопки, ставим двоеточие и пишем ключевое слово `checked`.

## Как это понять

Браузер присваивает чекбоксу или радиокнопке псевдокласс `:checked`, когда они отмечены. Мы можем использовать это для стилизации элемента.

## Подсказки

💡 Этот псевдокласс есть только у тех элементов, которые можно _отметить_: `<input type="checkbox">`, `<input type="radio">`.

💡 По задумке должен работать и с `option`, но поскольку выпадающий список сильно отличается от системы к системе и от браузера к браузеру, то пока работает только в браузере Chrome на Windows. Так что ждём и надеемся, но особо не используем.
