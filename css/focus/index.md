---
title: "`:focus`"
authors:
  - solarrust
editors:
  - tachisis
keywords:
  - :focus
  - LVHA
  - псевдокласс
tags:
  - doka
---

## Кратко

Сайтом можно пользоваться не только с использованием мышки, но и при помощи клавиатуры. При переключении клавишей <kbd>Tab<kbd> элементу добавляется псевдокласс `:focus`, и мы можем задать для него красивые стили.

Элементы формы могут получить фокус и при клике мышкой на него. Например, если кликнуть по кнопке или в поле ввода текста, то им будет добавлен псевдокласс `:focus`.

![Пример псевдокласса :focus](images/focus.gif)

## Пример

При попадании фокуса на кнопку будем показывать точечную рамку красного цвета:

```css
button:focus {
  border: 1px dotted red;
}
```

## Как пишется

После любого селектора ставим двоеточие и пишем ключевое слово `focus`.

### Селектор по тегу в состоянии :focus

```css
a:focus {
  /* Стили */
}
```

### Селектор по классу в состоянии :focus

```css
.link:focus {
  /* Стили */
}
```

### Составной селектор в состоянии :focus

```css
li .link:focus {
  /* Стили */
}
```

### Селектор по идентификатору в состоянии :focus

```css
#id:focus {
  /* Стили */
}
```

### Селектор по классу и его псевдоэлемент в состоянии :focus

```css
.link:focus::before {
  /* Стили */
}
```

## Как это понять

При попадании элемента в фокус браузер подставляет элементу дополнительный автоматический класс, чтобы пометить изменение состояния. Этому классу мы можем задавать любые стили, подходящие по дизайну. При этом логика подставления или удаления этого класса скрыта под капотом движка браузера.

Важно знать, что в стандартных стилях браузера уже прописаны дефолтные стили для фокуса интерактивных элементов. Например, в Google Chrome вокруг элемента появляется прямоугольная фиолетовая рамка. Стили для неё:

```css
:focus {
  outline: -webkit-focus-ring-color auto 1px;
}
```

Важно! Не удаляйте стили для фокуса полностью. Если вам не нравятся дефолтные стили — измените их. При полном удалении фокуса пользователь не будет понимать, в какой части страницы он находится, если его сценарий пользования сайтом отличается от привычного.

## Подсказки

💡 Смену стилей между состояниями можно анимировать при помощи [`transition`](/css/transition) 🎉

💡 В браузер встроены дефолтные стили для фокуса.

💡 Нельзя полностью удалять стили для фокуса, заменяйте их на свои, если дефолтные не нравятся.

💡 Стили для фокуса можно увидеть, открыв сайт и несколько раз нажав клавишу <kbd>Tab</kbd>. Или нажмите на кнопку, поставьте курсор в поле ввода.
