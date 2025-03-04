---
title: "`<html>`"
authors:
  - grachev
contributors:
  - solarrust
keywords:
  - тэг
  - тег
  - хтмл
  - html
  - "<html>"
tags:
  - doka
---

## Кратко

Элемент `<html>` открывает контейнер, в котором находится всё содержимое страницы. Это корневой, или родительский, элемент всего документа.

## Пример

```html
<!DOCTYPE html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
</html>
```

## Как пишется

Тег `<html>` ставят сразу после `<!DOCTYPE>`.

### Атрибуты

- `manifest` — указывает URI (унифицированный идентификатор ресурса) манифеста, который сообщает браузеру, какие элементы страницы могут быть закэшированы.
- `title` — добавляет всплывающую подсказку, которая появляется, когда курсор мыши задерживается в окне веб-страницы.
- `version` — определяет версию шаблона HTML-документа, но необходимости в этом нет _(устарел в HTML4.01; вышел из употребления с версии HTML5)_.
- `xmlns` — необязательный для HTML5, но необходимый для XHTML-документов атрибут. Определяет пространство имён XML, в котором находится документ.
- `prefix` — здесь прописывают open-graph разметку, типа `<html lang="ru-RU" prefix="og: [http://ogp.me/ns#](http://ogp.me/ns#)">`. Это чтобы при репосте с сайта в VK, Facebook и другие соцсети передавались те заголовки, картинки и описания, которые мы укажем.

## Подсказки

💡 В HTML есть атрибут `lang`, который подсказывает браузеру язык, на котором написан текст на странице. Если добавить `lang` в `<html>`, браузер правильно отобразит текст и подберёт подходящую для этого языка пунктуацию. Например, в английском тексте будут такие кавычки `“ ”`, а в русском такие `«»`. Пишется так: `lang="en"`.

Кроме того атрибут `lang` позволяет браузеру понять, отличается ли язык страницы от языка вашей системы. Если да, то браузер предложит пользователю использовать онлайн-переводчик.

```html
<html lang="ru">
  ...
</html>
```

<details class="article__table article__table_all-half">
  <summary>Коды всех языков</summary>

| Язык                             | Код   |
| -------------------------------- | ----- |
| Абхазский                        | ab    |
| Азербайджанский                  | az    |
| Аймарский                        | ay    |
| Албанский                        | sq    |
| Английский                       | en    |
| Американский английский          | en-us |
| Арабский                         | ar    |
| Армянский                        | hy    |
| Ассамский                        | as    |
| Африкаанс                        | af    |
| Башкирский                       | ba    |
| Белорусский                      | be    |
| Бенгальский                      | bn    |
| Болгарский                       | bg    |
| Бретонский                       | br    |
| Валлийский                       | cy    |
| Венгерский                       | hu    |
| Вьетнамский                      | vi    |
| Галисийский                      | gl    |
| Голландский                      | nl    |
| Греческий                        | el    |
| Грузинский                       | ka    |
| Гуарани                          | gn    |
| Датский                          | da    |
| Зулу                             | zu    |
| Иврит                            | iw    |
| Идиш                             | ji    |
| Индонезийский                    | in    |
| Интерлингва (искусственный язык) | ia    |
| Ирландский                       | ga    |
| Исландский                       | is    |
| Испанский                        | es    |
| Итальянский                      | it    |
| Казахский                        | kk    |
| Камбоджийский                    | km    |
| Каталанский                      | ca    |
| Кашмирский                       | ks    |
| Кечуа                            | qu    |
| Киргизский                       | ky    |
| Китайский                        | zh    |
| Корейский                        | ko    |
| Корсиканский                     | co    |
| Курдский                         | ku    |
| Лаосский                         | lo    |
| Латвийский, латышский            | lv    |
| Латынь                           | la    |
| Литовский                        | lt    |
| Малагасийский                    | mg    |
| Малайский                        | ms    |
| Мальтийский                      | mt    |
| Маори                            | mi    |
| Македонский                      | mk    |
| Молдавский                       | mo    |
| Монгольский                      | mn    |
| Науру                            | na    |
| Немецкий                         | de    |
| Непальский                       | ne    |
| Норвежский                       | no    |
| Пенджаби                         | pa    |
| Персидский                       | fa    |
| Польский                         | pl    |
| Португальский                    | pt    |
| Пуштунский                       | ps    |
| Ретороманский                    | rm    |
| Румынский                        | ro    |
| Русский                          | ru    |
| Самоанский                       | sm    |
| Санскрит                         | sa    |
| Сербский                         | sr    |
| Словацкий                        | sk    |
| Словенский                       | sl    |
| Сомали                           | so    |
| Суахили                          | sw    |
| Суданский                        | su    |
| Тагальский                       | tl    |
| Таджикский                       | tg    |
| Тайский                          | th    |
| Тамильский                       | ta    |
| Татарский                        | tt    |
| Тибетский                        | bo    |
| Тонга                            | to    |
| Турецкий                         | tr    |
| Туркменский                      | tk    |
| Узбекский                        | uz    |
| Украинский                       | uk    |
| Урду                             | ur    |
| Фиджи                            | fj    |
| Финский                          | fi    |
| Французский                      | fr    |
| Фризский                         | fy    |
| Хауса                            | ha    |
| Хинди                            | hi    |
| Хорватский                       | hr    |
| Чешский                          | cs    |
| Шведский                         | sv    |
| Эсперанто (искусственный язык)   | eo    |
| Эстонский                        | et    |
| Яванский                         | jw    |
| Японский                         | ja    |

</details>

:::callout 🙈

💡 Если после открывающего тега `<html>` или перед закрывающим тегом `<html>` нет комментария, но внутри есть заполненная конструкция `<body> ... </body>`, теги `<html>` и `</html>` можно не писать.

:::
