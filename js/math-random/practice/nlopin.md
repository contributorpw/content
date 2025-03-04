🛠 Не используй генерацию числа в критичных местах, например для ключа доступа — для этого лучше использовать [Web Cryptography API](https://www.w3.org/TR/WebCryptoAPI/). Он работает медленнее, но криптографически устойчив:

```js
window.crypto.getRandomValues(new Uint32Array(1))[0] //  вернет случайное число от 0 до 2^32
```

🛠 Используется, когда нужно сгенерировать случайное число в заданном диапазоне. Функция возвращает число от 0 до 1, но диапазон можно расширить с помощью формулы:

```js
Math.floor(Math.random() * (max - min)) + min // от минимума до максимума, не включая максимум
```

<iframe title="Название — Math.random() — Дока" src="../demos/Lopinopulos-ewOxWV/"></iframe>

🛠 Используется для выбора случайного элемента из массива. Например, вы хотите отобразить случайный товар дня из списка или же показать пользователю несколько элементов из его коллекции любимых песен.

https://codepen.io/Lopinopulos/pen/KjPJey
