---
title: "`<nav>`"
authors:
  - vladimir
contributors:
  - grachev
  - skorobaeus
  - solarrust
  - pepelsbey
editors:
  - tachisis
keywords:
  - тэг
  - тег
  - nav
  - навигация
tags:
  - doka
---

## Кратко

В контейнере `<nav>` можно собрать ссылки для навигации по сайту.

## Пример

Вот так выглядит простой блок `<nav>` со ссылками на разные разделы сайта. Мы использовали его с тегом `<ul>`, поскольку элементы меню однотипные по смыслу и связаны между собой:

```html
<nav class="menu">
  <ul>
    <li><a href="#">Главная</a></li>
    <li><a href="#">О нас</a></li>
    <li><a href="#">Контакты</a></li>
  </ul>
</nav>
```

## Как это понять

В контейнер `<nav>` помещаются основные ссылки, по которым пользователь сможет быстро перейти на нужный раздел сайта.

## Как пишется

Тег `<nav>` парный, всегда нужно закрывать `</nav>`.

На странице можно использовать несколько `<nav>`.

## Атрибуты

У `<nav>` нет уникальных атрибутов, применяются все [глобальные атрибуты](/html/global-attrs).

## Подсказки

💡 `<nav>` — это один из ориентиров (landmark), которые скринридеры могут использовать для навигации по странице. То есть можно перейти прямо в блок навигации по сайту, это очень удобно.

💡 Спецификация [рекомендует](https://html.spec.whatwg.org/multipage/sections.html#the-nav-element) не увлекаться разметкой всех ссылок на странице с помощью `<nav>`, достаточно указать самые важные.

## Ещё пример

Создадим так называемые «хлебные крошки» — ссылки на страницы, указывающие на разделы, в которых находится текущая страница:

```html
<nav class="crumbs">
  <ol>
    <li class="crumb"><a href="bikes">Велосипеды</a></li>
    <li class="crumb"><a href="bikes/bmx">BMX</a></li>
    <li class="crumb">Jump Bike 3000</li>
  </ol>
</nav>

<h1>Jump Bike 3000</h1>
<p>Отличный вариант для профессионалов. С ним вы научитесь круто прыгать.</p>
```

```css
nav {
  border-bottom: 1px solid black;
}

.crumbs ol {
  list-style-type: none;
  padding-left: 0;
}

.crumb {
  display: inline-block;
}

.crumb a {
  position: relative;
}

.crumb a::after {
  content: ">";
  position: absolute;
  padding: 0 5px;
  color: #ffffff;
  font-size: 80%;
}
```

<iframe title="Хлебные крошки" src="demos/breadcrumbs/" height="280"></iframe>
