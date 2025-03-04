---
title: "`<article>`"
cover:
  desktop: 'images/covers/desktop.svg'
  mobile: 'images/covers/mobile.svg'
  alt: 'Фотоальбом с фотографиями, слева — большая с мальчиком, справа сверху — меч, справа снизу — девочка'
authors:
  - realetive
contributors:
  - furtivite
editors:
  - tachisis
keywords:
  - статья
  - артикл
  - семантический тег
tags:
  - doka
---

## Кратко

Тег `<article>` обозначает законченный и самодостаточный раздел документа, описывающий какую-то сущность: статью, товар, карточку пользователя и т. д.

## Пример

```html
<article>
  <h1>Тег <code>&lt;article&gt;</code>, и с чем его едят</h1>
  <h2>Кратко</h2>
  <p>
    Тег <code>&lt;article&gt;</code> обозначает законченный и самодостаточный
    раздел документа, описывающий какую-то сущность: статью, товар, карточку
    пользователя и т. д.
  </p>
  <h2>Пример</h2>
  <pre>
    <code>Рекурсия! 💥</code>
  </pre>
</article>
```

## Как пишется

```html
<article>
  <!-- Содержимое -->
</article>
```

## Как это понять

Тег `<article>` семантически «помечает», что его содержимое — это какая-то одна конкретная сущность. Никакого поведенческого или иного оформления это не даёт, визуально выглядит как блочный `<div>`-элемент.

## Подсказки

### `<article>` или `<section>`?

В отличие от тега `<article>`, который помечает самодостаточный элемент документа, `<section>` является частью какого-то раздела. Но единственного и абсолютного правила тут нет — всё на усмотрение автора.

Например, если мы верстаем книгу с главой «Бран», повествующей «о 7-летнем юноше, сыне лорда Винтерфелла», то это скорее всего `<section>`, т. к. в книге наверняка есть и другие разделы (главы, не обязательно только об этом персонаже).

С другой стороны, можно представить твит, статью на «Хабре» или страницу на «КиноПоиске», на которой написано что-нибудь вроде «Сериал снят по мотивам серии романов Джорджа Р. Р. Мартина» — тогда каждая из этих публикаций будет уже `<article>`, потому что каждая из них полноценна и самодостаточна по своему содержанию.
