---
title: "`Element.style`"
authors:
  - bespoyasov
tags:
  - doka
---

## Кратко

[`HTMLElement.style`](http://htmlelement.style) получает и устанавливает инлайновые стили элемента, то есть те, что записываются через атрибут `style`.

С помощью него можно управлять стилем элемента. [Специфичность](https://developer.mozilla.org/ru/docs/Web/CSS/Specificity) этого свойства такая же, как у атрибута `style`.

## Как пишется

Чтобы получить значения инлайновых стилей с помощью свойства `style`, мы можем записать:

```js
const element = document.getElementById("someElement")
const inlineStyles = element.style
```

В этом случае в значение `inlineStyles` запишется объект [`CSSStyleDeclaration`](https://developer.mozilla.org/ru/docs/Web/API/CSSStyleDeclaration), который будет в себе содержать все инлайновые стили, которые содержит элемент `element`.

Чтобы задать стили для элемента, мы можем использовать несколько способов. Либо через `cssText`, чтобы указать несколько свойств разом. (Тем же эффектом обладает установка стиля через `setAttribute()`.) Либо через отдельные свойства в `style.[propertyName]`.

```js
// Следующие две записи работают одинаково
// и устанавливают несколько стилей в одном выражении:
element.style.cssText = "color: blue; border: 1px solid black"
element.setAttribute("style", "color:red; border: 1px solid blue;")

// Следующая — устанавливает значение определенного свойства,
// оставляя другие значения стиля нетронутыми:
element.style.color = "blue"
```

## Как понять

[`HTMLElement.style`](http://htmlelement.style) — это механизм для работы со стилями на элементе. С его помощью можно управлять отображением элементов в «рантайме», то есть во время выполнения скрипта.

Этот механизм позволяет «перетирать» стили, описанные в CSS-таблицах, так как специфичность стилей в атрибуте `style` выше (за исключением стилей с `!important`).

Чтобы указать значение конкретного CSS-свойства, мы можем использовать одноимённое отображение в `style`:

```js
// Если мы хотим указать color:
element.style.color = "red" // или 'rgb(255,0,0)', или '#f00'

// Если хотим указать font-family:
element.style.fontFamily = "Arial"
```

Обратите внимание, что имена свойств в `style.[propertyName]` записываются в camelCase, в отличие от CSS-свойств, которые записываются через дефис.

Таким образом `font-family` превращается в `fontFamily`, а, например, `background-color` — в `backgroundColor`.

При сомнениях в том, как правильно называется то или иное свойство, воспользуйтесь списком соответствий:

<details class="article__table article__table_all-half">
  <summary>CSS-свойства в JS-нотации</summary>

| CSS | JavaScript |
| --- | --- |
| [background]() | background |
| [background-attachment]() | backgroundAttachment |
| [background-color](/css/background-color/) | backgroundColor |
| [background-image](/css/background-image/) | backgroundImage |
| [background-position](/css/background-position/) | backgroundPosition |
| [background-repeat](/css/background-repeat/) | backgroundRepeat |
| [border](/css/border/) | border |
| [border-bottom](/css/border/#как-это-понять) | borderBottom |
| [border-bottom-color](/css/border/#как-это-понять) | borderBottomColor |
| [border-bottom-style](/css/border/#как-это-понять) | borderBottomStyle |
| [border-bottom-width](/css/border/#как-это-понять) | borderBottomWidth |
| [border-color](/css/border/#border-color) | borderColor |
| [border-left](/css/border/#как-это-понять) | borderLeft |
| [border-left-color](/css/border/#как-это-понять) | borderLeftColor |
| [border-left-style](/css/border/#как-это-понять) | borderLeftStyle |
| [border-left-width](/css/border/#как-это-понять) | borderLeftWidth |
| [border-right](/css/border/#как-это-понять) | borderRight |
| [border-right-color](/css/border/#как-это-понять) | borderRightColor |
| [border-right-style](/css/border/#как-это-понять) | borderRightStyle |
| [border-right-width](/css/border/#как-это-понять) | borderRightWidth |
| [border-style](/css/border/#border-style) | borderStyle |
| [border-top](/css/border/#как-это-понять) | borderTop |
| [border-top-color](/css/border/#как-это-понять) | borderTopColor |
| [border-top-style](/css/border/#как-это-понять) | borderTopStyle |
| [border-top-width](/css/border/#как-это-понять) | borderTopWidth |
| [border-width](/css/border/#border-width) | borderWidth |
| [clear]() | clear |
| [clip]() | clip |
| [color](/css/color/) | color |
| [cursor](/css/cursor/) | cursor |
| [display](/css/display/) | display |
| [filter]() | filter |
| [float]() | cssFloat |
| [font]() | font |
| [font-family](/css/font-family/) | fontFamily |
| [font-size](/css/font-size/) | fontSize |
| [font-variant]() | fontVariant |
| [font-weight](/css/font-weight/) | fontWeight |
| [height](/css/height/) | height |
| [left]() | left |
| [letter-spacing](/css/letter-spacing/) | letterSpacing |
| [line-height](/css/line-height/) | lineHeight |
| [list-style]() | listStyle |
| [list-style-image](/css/list-style-image/) | listStyleImage |
| [list-style-position](/css/list-style-position/) | listStylePosition |
| [list-style-type](/css/list-style-type/) | listStyleType |
| [margin](/css/margin/) | margin |
| [margin-bottom](/css/margin/#кратко) | marginBottom |
| [margin-left](/css/margin/#кратко) | marginLeft |
| [margin-right](/css/margin/#кратко) | marginRight |
| [margin-top](/css/margin/#кратко) | marginTop |
| [overflow]() | overflow |
| [padding](/css/padding/) | padding |
| [padding-bottom](/css/padding/#кратко) | paddingBottom |
| [padding-left](/css/padding/#кратко) | paddingLeft |
| [padding-right](/css/padding/#кратко) | paddingRight |
| [padding-top](/css/padding/#кратко) | paddingTop |
| [page-break-after]() | pageBreakAfter |
| [page-break-before]() | pageBreakBefore |
| [position]() | position |
| [stroke-dasharray]() | strokeDasharray |
| [stroke-dashoffset]() | strokeDashoffset |
| [stroke-width]() | strokeWidth |
| [text-align](/css/text-align/) | textAlign |
| [text-decoration](/css/text-decoration/) | textDecoration |
| [text-indent]() | textIndent |
| [text-transform](/css/text-transform/) | textTransform |
| [top]() | top |
| [vertical-align](/css/vertical-align/) | verticalAlign |
| [visibility](/css/visibility/) | visibility |
| [width](/css/width/) | width |

</details>
