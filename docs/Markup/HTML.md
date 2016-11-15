# HTML

**Статус:** актуально.

## Оглавление

- [HTML](#html)
  - [Синтаксис](#html-syntax)
  - [HTML5 doctype](#html-doctype)
  - [Атрибут языка](#html-lang)
  - [Режим совместимости Internet Explorer](#html-ie-compatibility-mode)
  - [Кодировка символов](#html-encoding)
  - [Подключение CSS и JavaScript](#html-style-script)
  - [Относительные и абсолютные пути до ресурсов](#html-absolute-and-relative-paths)
  - [Название файлов](#html-file-name)
  - [Идентификаторы](#html-identificators)
  - [Порядок атрибутов](#html-attribute-order)
  - [Логические атрибуты](#html-boolean-attributes)
  - [Элементы и атрибуты элементов форм](#html-form)
  - [Ссылки с протоколами](#html-links-and-protocol)
  - [Сокращение разметки](#html-reducing-markup)
  - [Изображения](#html-images)
  - [Взаимодействие HTML и JavaScript](#html-javascript)
  - [Комментарии](#html-comments)

## <a name="html">HTML</a>

Старайтесь соблюдать стандарты HTML и семантику, но не за счет практичности. Используйте меньшее количество разметки с наименьшим числом тонкостей, когда это возможно.



### <a name="html-syntax">Синтаксис</a>

- Для вложенных элементов отступы должны быть только табами. В любом редакторе можно задать индивидуальный размер. Оптимальный размер - 4.<br>
В этом примере `∙∙` - два пробела, а `――――` - один отступ с табуляцией.
```html
<!-- Плохо -->
<div class="block">
∙∙<div class="block__element">CSSSR</div>
</div>

<!-- Хорошо -->
<div class="block">
――――<div class="block__element">CSSSR</div>
</div>
```

- Блочные элементы должны иметь перенос на новую строку, один строчный элемент можно оставлять на месте. Если строчных элементов больше одного или контента достаточно много, то следует переносить.
```html
<!-- Плохо -->
<div class="block"><div class="block__element">CSSSR</div></div>

<!-- Хорошо -->
<div class="block">
  <div class="block__element">CSSSR</div>
</div>
```

- Группа однотипных блоков должна иметь два переноса.
```html

<!-- Плохо -->
<div class="project">
  <div class="project__name">Lorem</div>
  <div class="project__desc">Lorem ipsum dolor sit amet, consectetur adipisicing elit.</div>
</div>
<div class="project">
  <div class="project__name">Ipsum.</div>
  <div class="project__desc">Lorem ipsum dolor sit amet, consectetur adipisicing elit.</div>
</div>

<!-- Хорошо-->
<div class="project">
  <div class="project__name">Lorem</div>
  <div class="project__desc">Lorem ipsum dolor sit amet, consectetur adipisicing elit.</div>
</div>

<div class="project">
  <div class="project__name">Ipsum.</div>
  <div class="project__desc">Lorem ipsum dolor sit amet, consectetur adipisicing elit.</div>
</div>
```

- Блочные элементы не должны находиться в строчных.
```html
<!-- Плохо -->
<span>
  <div>:(</div>
</span>

<!-- Хорошо -->
<span>
  <span>:)</span>
</span>
```

- После закрывающихся тегов не должно быть лишних пробелов и/или табов. Для автоудаления можно настроить свой редактор кода. Для Sublime Text можно посмотреть в репе [sputnik](https://github.com/CSSSR/sputnik/wiki/Софт).
```html
<!-- Плохо -->
<div class="block">∙
  <div class="block__element">CSSSR</div>∙∙∙∙
</div>――――――――

<!-- Хорошо -->
<div class="block">
  <div class="block__element">CSSSR</div>
</div>
```

- Названия тегов, атрибутов и значений свойств (кроме текстовых данных) должны быть в нижнем регистре.
```html
<!-- Плохо -->
<INPUT TYPE="TEXT" VALUE="CSSSR">

<!-- Хорошо -->
<input type="text" value="CSSSR">
```

- Всегда используйте двойные кавычки `""` для значений атрибутов.
```html
<!-- Плохо -->
<div class=block>
  <div class=block__element>CSSSR</div>
</div>

<div class='block'>
  <div class='block__element'>CSSSR</div>
</div>

<!-- Хорошо -->
<div class="block">
  <div class="block__element">CSSSR</div>
</div>
```

- Не добавляйте слэш `/` в конец одиночного тега — в HTML5 он необязателен.
```html
<!-- Плохо -->
<input type="text" value="CSSSR"/>

<!-- Хорошо -->
<input type="text" value="CSSSR">
```

- Не пропускайте необязательные закрывающие теги (например, `</li>`, `</p>` или `</body>`).
```html
<!-- Плохо -->
<body>
  <p>Полезные инструменты
  <ul>
    <li>Grunt
    <li>Jade
    <li>Stylus
  </ul>


<!-- Хорошо -->
<body>
  <p>Полезные инструменты</p>
  <ul>
    <li>Grunt</li>
    <li>Jade</li>
    <li>Stylus</li>
  </ul>
</body>
```



### <a name="html-doctype">HTML5 doctype</a>

Укажите в начале каждой вашей HTML-страницы этот тип документа. Это заставит браузер работать в режиме соответствия стандартам, что обеспечит единообразное отображение ваших страниц в разных браузерах.
```html
<!DOCTYPE html>
<html>
	<head>
	  <!-- ... -->
	</head>
	<body>
	  <!-- ... -->
	</body>
</html>
```



### <a name="html-lang">Атрибут языка</a>

Из спецификации HTML5:
> Для указания языка документа авторам рекомендуется прописывать атрибут языка в корневом элементе HTML. Это поможет инструментам синтеза речи определить какое произношение использовать, а инструментам перевода - какие правила, и так далее.

```html
<html lang="ru">
	<!-- ... -->
</html>
```

Подробнее познакомиться с атрибутом `lang` можно в [спецификации](http://www.w3.org/html/wg/drafts/html/master/semantics.html#the-html-element).

Список кодов различных языков на [Sitepoint](http://reference.sitepoint.com/html/lang-codes).



### <a name="html-ie-compatibility-mode">Режим совместимости Internet Explorer</a>

IE поддерживает использование специального `<meta>`-тега, который указывает в режиме совместимости с какой версией IE следует отрендерить страницу. Если обстоятельства не требуют какой-то специальной версии IE, то самым правильным будет заставить браузер использовать режим самой последней версии (**edge mode**).

```html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```

Если сайт будет находиться на собственном хостинге, то следует убрать этот `meta`-тег и настроить хостинг для определения IE и добавления специальных заголовков.

Для получения дополнительной информации можно ознакомиться с обсуждением на [Stack Overflow](http://stackoverflow.com/questions/6771258/whats-the-difference-if-meta-http-equiv-x-ua-compatible-content-ie-edge-e).



### <a name="html-encoding">Кодировка символов</a>

Явно объявив кодировку символов, вы быстро и легко обеспечите правильное отображение вашего контента. При этом, вы сможете избежать использования [символьных сущностей](http://www.w3schools.com/html/html_entities.asp) в вашем HTML-коде, при условии, что их кодировка совпадает с кодировкой документа (как правило, utf-8).

```html
<head>
	<meta charset="utf-8">
</head>
```



### <a name="html-style-script">Подключение CSS и JavaScript</a>

Все стили и скрипты должны быть только в отдельных файлах. Встроенных и внедрённых в тег стилей (в атрибуте style) не должно быть.

Согласно спецификации HTML5, при подключении CSS и JavaScript файлов не требуется указание атрибута `type`, так как `text/css` и `text/javascript` являются значениями по умолчанию.

```html
<!-- Внешний CSS -->
<link rel="stylesheet" href="styles/main.css">

<!-- CSS внутри документа, внедрять в страницу не нужно -->
<style>
	/* ... */
</style>

<!-- Внешний JavaScript -->
<script src="scripts/main.js"></script>

<!-- JavaScript внутри документа, внедрять в страницу не нужно -->
<script>
	console.log('CSSSR');
</script>
```

Ссылки на спецификацию HTML5:
* [Использование тега `link`](http://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-link-element)
* [Использование тега `style`](http://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-style-element)
* [Использование тега `script`](http://www.w3.org/TR/2011/WD-html5-20110525/scripting-1.html#the-script-element)



### <a name="html-absolute-and-relative-paths">Абсолютные и относительные пути к ресурсам</a>

По умолчанию пути до ресурсов должны быть относительного текущего расположения страницы для просмотра на GitHub Pages.

Относительно корня или абсолютные пути можно использовать в некоторых случаях:
- Для страниц сайта, находящихся в поддиректории (обычно на хостинге CSSSR или заказчика).
- В JavaScript, например, для указания изображения метки на Яндекс.Картах или Google Maps.

Подробнее можно почитать на [htmlbook.ru](http://htmlbook.ru/samhtml/ssylki/absolyutnye-i-otnositelnye-ssylki).



### <a name="html-file-name">Название файлов</a>

Называйте файлы страниц по-английски без ошибок, не используйте кириллицу, транслит и комбинацию транслита и английского.

Само название должно отражать содержимое файла.

Плохо:
```
Главная страница.html
Stranica novostey.html
01_about-NEW!!!.html
page-kontakti.html
```

Хорошо:
```
main.html
news.html
about.html
contacts.html
```



### <a name="html-identificators">Идентификаторы</a>

Идентификатор - это атрибут с уникальным названием элемента, которое в документе должно быть единственным. Не допускайте элементов с одинаковыми идентификаторами.



### <a name="html-attribute-order">Порядок атрибутов</a>

Для удобства чтения HTML-атрибуты должны быть указаны именно в этом порядке:
- `class`
- `id`, `name`
- `data-*`
- `src`, `for`, `type`, `href`
- `title`, `alt`
- `aria-*`, `role`

Классы создаются для многократно используемых компонентов верстки, поэтому они идут первыми. Идентификаторы более специфичны и должны использоваться умеренно (например, для закладок на странице), поэтому они следуют вторыми.
```html
<a class="link" id="toggle" data-modal="toggle" href="javascript:void(0);">Меню</a>

<input class="input-text" type="text">

<img class="logo" src="images/logo.png" alt="CSSSR">
```



### <a name="html-boolean-attributes">Логические атрибуты</a>

Логические атрибуты одни из тех, которые не требуют объявленного значения. XHTML требует от вас задать значение, но в HTML5 нет такого требования.

За подробной информацией обратимся к разделу [о логических атрибутах на WhatWG](http://www.whatwg.org/specs/web-apps/current-work/multipage/common-microsyntaxes.html#boolean-attributes):

> Наличие логического атрибута у элемента говорит об истинном его значении, а отсутствие атрибута — о ложном.

Если вы *должны* указать значение атрибута, но **вам это не нужно**, следуйте этой рекомендации от WhatWG:

> Если атрибут присутствует, его значение должно быть либо пустой строкой или [...] каноническим именем атрибута без начальных или конечных пробелов.

**Если коротко, то не указывайте значение логическому атрибуту.**

```html
<!-- Плохо -->
<input class="input-text" type="text" disabled="disabled">

<input class="input-checkbox" type="checkbox" value="on" checked="checked">

<select class="select">
	<option value="0" selected="selected">Grunt</option>
	<option value="1">Jade</option>
	<option value="2">Stylus</option>
</select>

<!-- Хорошо -->
<input class="input-text" type="text" disabled>

<input class="input-checkbox" type="checkbox" value="on" checked>

<select class="select">
	<option value="0" selected>Grunt</option>
	<option value="1">Jade</option>
	<option value="2">Stylus</option>
</select>
```



### <a name="html-form">Формы, элементы и атрибуты элементов форм</a>

- Формы логично должны быть в теге `form`.

- Формы не должны вкладываться друг в друга. Если они разные, то должны быть раздельны друг от друга.

- Форма должна иметь атрибуты:
  - `action` - для указания адреса отправки данных.
  - `method` - метод передачи данных, обычно в значении указывается `post`.
```html
<!-- Плохо -->
<form>
  <!-- ... -->
  <button type="submit">Подать заявку</button>
</form>

<!-- Хорошо -->
<form action="send.php" method="post">
  <!-- ... -->
  <button type="submit">Подать заявку</button>
</form>
```

- Кнопки подтверждения формы логично должны быть кнопками с атрибутом `type="submit"`, а не ссылками, строчными или блочными элементами.
```html
<!-- Плохо -->
<form action="send.php" method="post">
    <!-- ... -->
    <a href="send.php">Подать заявку</a>
</form>

<!-- Хорошо -->
<form action="send.php" method="post">
    <!-- ... -->
    <button type="submit">Подать заявку</button>
</form>
```

- Если нестандартные элементы форм типа списков или слайдеров генерируются с помощью JavaScript, то выбранное значение должно сохраняться в специальном теге `<input type="hidden">`, если испольузется тег `select`, то сохраняться в дочернем теге `option`.

- Элементы формы должны иметь атрибуты:
    - `name` и `value` - для ключа и значения.
    - `for` и `id` - для связи надписи и элемента, при клике на надпись элемент будет фокусироваться.
```html
<label for="skype">Skype</label>
<input id="skype" name="skype" value="csssr.ru">
```



### <a name="html-links-and-protocol">Ссылки и протоколы</a>

- Для ссылок без адреса вместо `#` вставлять `javascript:void(0);`, чтобы страницу не скроллило вверх.
```html
<!-- Плохо -->
<a href="#">Портфолио CSSSR</a>

<!-- Хорошо -->
<a href="javascript:void(0);">Портфолио CSSSR</a>
```

- Если элемент, похожий на ссылку, не является ею и событие клика обрабатывается в JavaScript, то стоит заменить тег `a` на `span` или `div` и убрать атрибуты `href` и `target`, для фокусировки можно задать атрибут `tabindex`.

- Для внешних ссылок нужно добавлять атрибуты `target="_blank"` для открытия в новой вкладке и `rel="nofollow"` для запрета отслеживания.
```
<!-- Плохо -->
Мы пользуемся поисковой системой <a href="http://yandex.ru/">Яндекс</a>.

<!-- Хорошо -->
Мы пользуемся поисковой системой <a href="http://yandex.ru/" target="_blank" rel="nofollow">Яндекс</a>.
```

- Телефоны, email-адреса и Skype-контакт должны быть ссылками:
	- `tel:+79876543210` - для указания телефона, номер должен начинаться с плюса и состоять только из чисел без спецсимволов типа пробелов, круглых скобок или дефиса.
	- `mailto:sales@csssr.com` - для указания e-mail.
	- `skype:csssr.ru?chat` - для указания Skype-контакта.

```html
<a href="tel:+79876543210">+7-987-654-32-10</a>
<a href="mailto:sales@csssr.com">Напишите нам на почту</a>
<a href="skype:csssr.ru?chat">Напишите нам в Skype</a>
```



### <a name="html-reducing-markup">Сокращение разметки</a>

Всякий раз, когда это возможно, избегайте лишних родительских элементов. Во многих случаях это требует повторения и рефакторинга, но позволяет создать меньшее количество разметки. Посмотрите на следующий пример:

```html
<!-- Неплохо -->
<span class="avatar">
	<img src="avatars/csssr.png" alt="CSSSR">
</span>

<!-- Лучше -->
<img class="avatar" src="avatars/csssr.png" alt="CSSSR">
```



### <a name="html-images">Изображения</a>

При размещении изображений следует учитывать то, чем они являются:
- Если изображение - стилевое оформление сайта, то реализуется в CSS фонах через свойство `background`. Например:
	- Фон сайта;
	- Паттерн;
	- Декоративные элементы;
	- И прочее.
	
- Используйте тег `img` для изображений:
	- Аватарок;
	- Продуктов в витрине;
	- Фотографий;
	- Любых изображений находящихся в контентной части:
		- Статьи;
		- Записи в блоге;
		- Комменатрия.
	
	Такие изображения должны быть отдельными файлами и находиться в папке `images/temp/`.
	
- В тегах `img` обязательно должен быть атрибут `alt`. Если изображение не меняет свой размер (не *резиновое*), то нужно его указать в атрибутах `width` и `height`.
```html
<!-- Плохо -->
<img src="images/csssr.png">

<!-- Хорошо -->
<img src="images/csssr.png" alt="CSSSR">

<img src="images/csssr.png" alt="CSSSR" width="128" height="64">
```



### <a name="html-javascript">Взаимодействие HTML и JavaScript</a>

- Создание разметки с помощью JavaScript делает её менее производительной, сложной для поиска и редактирования. По возможности избегайте этого.

- В зависимости от поддерживаемых браузеров используйте CSS по максимуму (анимации, табы, псевдоэлементы), не используйте JavaScript.

- Если JavaScript изменяет вид страницы, обязательно делать это при помощи смены CSS-классов, а не путём правки атрибута `style` элемента.

- Если в форме элемент удаляется (скрывается), он должен удаляться и из [DOM](http://ru.wikipedia.org/wiki/Document_Object_Model).



### <a name="html-comments">Комментирование кода</a>

По мере необходимости можно писать комментарии для пометки назначения какого-либо куска кода или причины выбора того или иного решения, которое может быть неочевидными, пометки для заказчика, если код при определённых условиях должен быть изменён. Комментировать всё не нужно.
Для русскоязычных проектов комментарии пишутся на русском языке, для иностранных - на английском.
