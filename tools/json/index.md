---
title: "JSON"
authors:
  - stegur
tags:
  - doka
keywords:
  - селектор
  - найти элемент по селектору
  - selector
  - найти элемент в html
---

## Кратко

JSON — самый популярный формат обмена данными между приложениями. Этот формат очень похож на объекты JavaScript. Объекты легко трансформируются в JSON для отправки на сервер.

## Как пишется

```json
{
  "brand": "Apple",
  "model": "iPhone 11 Pro",
  "isAvailable": true,
  "display": 5.8,
  "memories": [64, 256, 512],
  "features": {
    "tripleCamera": true,
    "faceId": true,
    "touchId": false,
    "eSIM": true
  }
}
```

JSON состоит из пар ключ-значение. Пары разделяются между собой запятыми — `,`, а ключ отделяется от значения через двоеточие — `:`. Ключом может быть **только** строка, обёрнутая в двойные кавычки. А вот значением — что угодно:

- Строка в двойных кавычках — `"I love JSON!"`
- Число — `21`
- Логическое значение — `true`
- Массив — `[18, true, "lost", [4, 8, 15, 16, 23, 42]]`
- Объект — `{"isValid": true, "isPayed": false}`

Если нужно сохранить JSON в файл, то используют расширение `.json`

## Как понять

JSON используется для того чтобы получить данные от сервера. Типичная схема работы:

1. Отправляем запрос на сервер
2. Ждём ответ
3. Получаем JSON с набором данных
4. Превращаем JSON в объект JavaScript
5. Используем данные

Пример:

<iframe title="Название — JSON — Дока" src="demos/Stegur-XWddLpK/"></iframe>

### Преобразование в JSON

Для того что бы превратить данные в JSON-код, используйте метод `JSON.stringify()`. Первым аргументом метод принимает значение, которое нужно преобразовать.

Преобразуем JavaScript-объект в JSON:

```js
let hero = {
  nickname: "BestHealerEver",
  level: 7,
  age: 141,
  race: "Gnome",
  isImmortal: false,
  things: ["sword", "helmet", "belt"],
  money: {
    gold: 6387,
    silver: 1264,
    bronze: 931,
    diamonds: 2,
  },
}

console.log(typeof hero) // object
console.log(typeof JSON.stringify(hero)) // string
console.log(JSON.stringify(hero))
```

Результатом конвертации будет строка:

```json
{
  "nickname": "BestHealerEver",
  "level": 7,
  "age": 141,
  "race": "Gnome",
  "things": ["sword", "helmet", "belt"],
  "isImmortal": false,
  "money": { "gold": 6387, "silver": 1264, "bronze": 931, "diamonds": 2 }
}
```

### Преобразование из JSON

Преобразовать строку с JSON в объект JavaScript можно с помощью метода `JSON.parse()`. Он принимает JSON-строку в качестве аргумента.

Попробуем преобразовать JSON:

```json
{
  "name": "Luke Skywalker",
  "height": "172",
  "mass": "77",
  "hair_color": "blond",
  "skin_color": "fair",
  "eye_color": "blue",
  "birth_year": "19BBY",
  "gender": "male"
}
```

С помощью `JSON.parse()` мы получим стандартный объект, с которым можно взаимодействовать:

```js
let json =
  '{"name":"Luke Skywalker","height":"172","mass":"77","hair_color":"blond","skin_color":"fair","eye_color":"blue","birth_year":"19BBY","gender":"male"}'
let jedi = JSON.parse(json)

console.log(jedi.name) // Luke Skywalker
console.log(jedi.gender) // male
console.log(jedi.birth_year) // 19BBY
```

В случае, если строка не является валидным JSON-кодом, метод `JSON.parse()` выбросит ошибку **SyntaxError.**
