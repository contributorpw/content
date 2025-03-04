---
title: "`<audio>`"
authors:
  - vladimir
contributors:
  - skorobaeus
editors:
  - tachisis
keywords:
  - audio
  - аудио
  - controls
  - source
  - loop
  - muted
  - preload
  - autoplay
  - тэг
  - тег
  - аудио
tags:
  - doka
---

## Кратко

Встраивает аудиофайл на страницу 🎧

## Пример

Попробуем добавить на нашу страницу приветствие Алисы и текст, который появится, если браузер не поддерживает встроенное аудио на странице:

```html
<figure>
  <figcaption>Привет, я Алиса</figcaption>
  <audio controls src="hi-alice.mp3">
    Ваш браузер не поддерживает встроенное аудио. Попробуйте скачать его
    <a href="hi-alice.mp3" download>по ссылке</a>.
  </audio>
</figure>
```

## Как это понять

Тег `<audio>` добавляет на страницу аудиоплеер, который может воспроизвести звуковой файл. Можно добавить несколько форматов одного файла, чтобы браузер воспроизвёл тот формат, который он поддерживает — для этого нужно добавить вложенные теги [`<source>`](/html/source).

## Как пишется

Тег `<audio>` всегда закрывается парным тегом `</audio>`.

Внутри контейнера `<audio>` пишется текст, который появится, если браузер не поддерживает встроенное аудио.

Адрес звукового файла задаётся с помощью атрибута `src` или тега [`<source>`](/html/source), который помещается внутри `<audio>`. Тег `<source>` позволяет добавить несколько форматов одного и того же файла на случай, если какой-то из них не будет поддерживаться браузером:

```html
<audio controls>
  <source src="audio.mp3" type="audio/mpeg">
  <source src="audio.ogg" type="audio/ogg">
  <p>
    Ваш браузер не поддерживает встроенное аудио. Попробуйте
    <a href="audio.mp3" download>скачать</a> файл.
  </p>
</audio>
```

## Атрибуты

С помощью атрибутов мы можем настроить кнопки управления, зацикливание файла и другие параметры:

- `autoplay` — аудио начнёт играть в момент загрузки страницы, не дожидаясь, когда файл скачается полностью. Но лучше так не делать, потому что никто не любит, когда что-то начинает играть без предупреждения, а браузеры типа Chrome вообще выключают такие звуки;
- `controls` — добавляет стандартные элементы управления аудиоплеером: кнопку воспроизведения и паузы, полосу прокрутки, уровень громкости и другие элементы, в зависимости от браузера;
- `loop` — зацикливает воспроизведение аудио, так что оно снова начинает играть каждый раз после завершения;
- `muted` — звук будет на нуле, пока пользователь его не увеличит;
- `preload` — подсказывает браузеру, нужно ли загружать аудио или информацию о нём сразу со страницей. Без этого атрибута предварительная загрузка файла будет зависеть от настроек конкретного браузера. У этого атрибута несколько значений:
  - `none` — аудиофайл не загружается предварительно;
  - `metadata` — загружается только информация о файле, например, размер и продолжительность. Рекомендуем использовать именно этот параметр, чтобы не загружать аудио, пока пользователь не захочет его прослушать;
  - `auto` — аудиофайл загружается со страницей, чтобы пользователь мог сразу начать его слушать. Если не указывать никакое значение `preload`, то атрибут будет работать как `auto`. Учти, что если стоит атрибут `autoplay`, то `preload` не работает.
- `src` — URL-адрес аудиофайла. Его ещё можно задать через тег `<source>`.

## Подсказки

💡 Если не указать атрибут `controls`, то браузер не будет показывать стандартные элементы управления аудиоплеером. Создать свои элементы управления можно с помощью JavaScript.

💡 Значение свойства `display` у тега `<audio>` по умолчанию `inline`, а значит внизу может появиться отступ, который зависит от высоты строки. Чтобы убрать этот отступ, напиши для плеера `display: block`.

💡 Используйте CSS-свойства, чтобы настроить общий внешний вид и расположение аудиоплеера. Например, `border` и `border-radius`, `padding`, `margin` и другие параметры. Отдельные элементы внутри плеера изменить не получится. К тому же, в разных браузерах они выглядят по-разному.

💡 С 2017 года практически все браузеры запретили автопроигрывание аудио.

## Ещё пример

Мы также добавили несколько форматов одного аудиофайла. Если браузер не поддерживает формат Opus, он попробует воспроизвести OGG. Если и с ним не получится, то воспроизведёт файл в MP3. Атрибут `type` поможет браузеру быстрее определить формат файла:

```html
<audio controls>
  <source src="audio.opus" type="audio/ogg; codecs=opus">
  <source src="audio.ogg" type="audio/ogg; codecs=vorbis">
  <source src="audio.mp3" type="audio/mpeg">
  Ваш браузер не поддерживает встроенные аудио. Попробуйте
  <a href="audio.mp3" download>скачать</a> файл.
</audio>
```

<iframe title="Аудио" src="demos/audio/" allow="autoplay" height="150"></iframe>
