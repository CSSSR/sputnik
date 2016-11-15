# Jade - HTML препроцессор

**Статус:** актуально.

На проекте используется шаблонизатор [Jade](http://jade-lang.com/) для компиляции в HTML.

Полезные ссылки для ознакомления:
* [jade-lang.com](http://jade-lang.com/) - документация Jade.
* [naltatis.github.io/jade-syntax-docs](http://naltatis.github.io/jade-syntax-docs/) - ещё одна документация Jade.
* [jsman.ru/jade/](http://jsman.ru/jade/) - ещё одна документация Jade.
* [html2jade.org](http://html2jade.org/) - конвертация HTML в Jade и Jade в HTML.
* [html2jade.aaron-powell.com](http://html2jade.aaron-powell.com/) - и еще один инструмент для конвертации HTML → Jade.


## 1. Назначение папок

```
templates/                     # Папка с шаблонами Jade
├── blocks/                    # Папка с подключаемыми блоками
├── helpers/                   # Папка с помощниками
│   ├── mixins.jade            # Примеси
│   └── variables.jade         # Переменные
├── layouts/                   # Папка с шаблонами раскладки
│   └── default.jade           # Шаблон раскладки по умолчанию
├── pages/                     # Папка с генерируемыми страницами
│   └── index.jade             # Шаблон одной из страниц
└── partials/                  # Папка с подлючаемыми шаблонами
    ├── footer.jade            # Шаблон подвала
    ├── head.jade              # Шаблон с ресурсами, SEO и мета-тегами
    ├── header.jade            # Шаблон шапки
    └── scripts.jade           # Шаблон со скриптами
```


## 2. Подключение частиц в страницы

* [`include header`](https://github.com/CSSSR/csssr-project-template/blob/master/app/templates/layouts/default.jade#L6) - используется для подключения частиц страницы, например, для шапок и подвалов.
* [`extends partials/default`](https://github.com/CSSSR/csssr-project-template/blob/master/app/templates/pages/index.jade#L1) - используется для внедрения контент в расширяемый шаблон. [`layouts/default.jade`](https://github.com/CSSSR/csssr-project-template/blob/master/app/templates/layouts/default.jade).
* [`block content`](https://github.com/CSSSR/csssr-project-template/blob/master/app/templates/pages/index.jade#L6) - используется для добавления строк кода в определённое место [другого шаблона](https://github.com/CSSSR/csssr-project-template/blob/master/app/templates/layouts/default.jade#L7).

Во всех случаях через пробел указывается путь от текущего расположения до шаблона без расширения `.jade`.


## 3. Теги, классы и идентификаторы

- Классы и идентификаторы пишутся в начале, а не в атрибутах. Указывать тег `div` не нужно, т.к. он используется по умолчанию.
```jade
//- Плохо
div(class='carousel' id="carousel")
nav(class='nav nav_pos_left')
div(id="carousel")

//- Хорошо
.carousel
nav.nav.nav_pos_left
#carousel
```

- Идентификатор ставится после классов.
```jade
//- Плохо
.carousel#carousel.carousel_theme_dark
#carousel.carousel

//- Хорошо
.carousel.carousel_theme_dark#carousel
.carousel#carousel
```


## 4. Атрибуты элемента и их значения

- Для нескольких атрибутов запятая не нужна.
```jade
//- Плохо
input.input-text(type='text', name='project', value='csssr', required)

//- Хорошо
input.input-text(type='text' name='project' value='csssr' required)
```

- Используйте одинарные кавычки для текстовых значений.
```jade
//- Плохо
input.input-text(type="text" name="project" value="csssr" required)

//- Хорошо
input.input-text(type='text' name='project' value='csssr' required)
```

- Не давайте необязательные значения атрибутам.
```jade
//- Плохо
input.input-checkbox(type='checkbox' name='browser[]' value='chrome' checked='checked')

//- Хорошо
input.input-checkbox(type='checkbox' name='browser[]' value='chrome' checked)
```

- Распологайте одиночные атрибуты в последнюю очередь.
```jade
//- Плохо
input.input-checkbox(type='checkbox' checked name='browser[]' value='chrome')

//- Хорошо
input.input-checkbox(type='checkbox' name='browser[]' value='chrome' checked)
```

- Для числовых значений кавычки не нужны.
```jade
//- Плохо
input.input-text(type="text" name="price" value="24999")

//- Хорошо
input.input-text(type='text' name='price' value=24999)
```

- Переносите атрибуты новую строку, если их много и/или значения длинные.
```jade
//- Плохо
input.input-text(type='text' name='project' value='csssr' data-required='Это поле обязательно для заполнения!'  data-hint='Допустимы только символы латинского алфавита `[a-z-A-Z]` и числа `[0-9]`.' required)

//- Хорошо
input.input-text(
    type='text'
    name='project'
    value='csssr'
    data-required='Это поле обязательно для заполнения!'
    data-hint='Допустимы только символы латинского алфавита `[a-z-A-Z]` и числа `[0-9]`.'
    required
)
```

## 5. Переносы строк

- Добавляйте перенос строки для однотипных блоков с множественным вложением элементов. В лучшем случае используйте [примесь (mixin)](http://jade-lang.com/reference/#mixins).
```jade
//- Плохо
.project
   .project__name Lorem
   .project__desc
      | Lorem ipsum dolor sit amet, consectetur adipisicing elit.
      | Unde doloremque neque facilis sed repudiandae tempore ipsum provident officia eaque quas.
.project
   .project__name Ipsum.
   .project__desc
      | Lorem ipsum dolor sit amet, consectetur adipisicing elit.
      | Unde doloremque neque facilis sed repudiandae tempore ipsum provident officia eaque quas.

//- Хорошо
.project
   .project__name Lorem
   .project__desc
      | Lorem ipsum dolor sit amet, consectetur adipisicing elit.
      | Unde doloremque neque facilis sed repudiandae tempore ipsum provident officia eaque quas.

.project
   .project__name Ipsum.
   .project__desc
      | Lorem ipsum dolor sit amet, consectetur adipisicing elit.
      | Unde doloremque neque facilis sed repudiandae tempore ipsum provident officia eaque quas.
```

- Строчные элементы можно записывать на одной строке через двоеточие `:`.<br>Не злоупотреблять с длинными классами.
```jade
//- Хорошо
ul.nav
   li.nav__item
      a.nav__link(href='/') Главная
   li.nav__item
      a.nav__link(href='/projects') Проекты
   li.nav__item
      a.nav__link(href='/contacts') Контакты

//- Лучше
ul.nav
    li.nav__item: a.nav__link(href='/') Главная
    li.nav__item: a.nav__link(href='/projects') Проекты
    li.nav__item: a.nav__link(href='/contacts') Контакты
```

## 6. Комментарии

- Комментарии в Jade, которые не должны попасть в HTML записываются через `//-`.
```jade
// Этот комментарий попадёт в HTML.

//- Этот комментарий не попадёт в HTML.
```

- Простые или условные комментарии можно записывать прямо в HTML-формате.
```html
<!--[if IE]>
meta(name='imagetoolbar' content='no')
meta(name='msthemecompatible' content='no')
<![endif]-->

<!--noindex-->
Это содержимое не будет индексироваться поисковиком.
<!--/noindex-->
```


## 7. Пиши меньше, делай больше или используйте примеси!

Для однотипных и повторяющихся строк кода имеет смысл использовать [примеси (mixins)](http://jade-lang.com/reference/#mixins) и указать только данные.
```html
mixin tools(list)
    ul.list
        each item in list
            li.list__item
                span.mark= item[0]
                = ' - ' + item[1]

+tools([
    ['spritesmith', 'генератор спрайтов и CSS переменных'],
    ['imagemin', 'сжатие картинок']
])
```

Скомпилирует

```html
<ul class="list">
    <li class="list__item">
        <span class="mark">spritesmith</span> - генератор спрайтов и CSS переменных
    </li>
    <li class="list__item">
        <span class="mark">imagemin</span> - сжатие картинок
    </li>
</ul>
```

## 8. Выделение активного пункта в меню навигации

### 8.1. Идентификаторы

На каждой странице в самом начале добавляем по идентфикатору страницы.

**pages/main.jade**
```javascript
- var pageId = 0;
```
**news.jade**
```javascript
- var pageId = 1;
```
**projects.jade**
```javascript
- var pageId = 2;
```
**about.jade**
```javascript
- var pageId = 3;
```
**contacts.jade**
```javascript
- var pageId = 4;
```


### 8.2. Активация пункта навигации

Активируем текущий пункт навигации в зависимости от идентификатора страницы.

**partials/header.jade**
```jade
//- Добавляем примесь для активации пункта навигации текущей страницы
mixin nav(items)
    ul.nav
        each item, i in items
            li.nav-item
                if i === pageId
                    span.nav-item__name.nav-item__name_state_active= item.name
                else
                    a.nav-item__name(href=item.href)= item.name

//- Используем примесь и добавляем в него данные навигации
+nav([{
    name: 'Главная',
    href: '/'
}, {
    name: 'Новости',
    href: '/news.html'
}, {
    name: 'Проекты',
    href: '/projects.html'
}, {
    name: 'О нас',
    href: '/about-us.html'
}, {
    name: 'Контакты',
    href: '/contacts.html'
}])

```


### 8.3. Результат

В итоге, если у нас текущая страница "Новости", то результат будет таким:
```html
<ul class="nav">
    <li class="nav-item">
        <a class="nav-item__name" href="/">Главная</a>
    </li>
    <li class="nav-item">
        <span class="nav-item__name nav-item__name_state_active">Новости</span>
    </li>
    <li class="nav-item">
        <a class="nav-item__name" href="/projects.html">Проекты</a>
    </li>
    <li class="nav-item">
        <a class="nav-item__name" href="/about-us.html">О нас</a>
    </li>
    <li class="nav-item">
        <a class="nav-item__name" href="/contacts.html">Контакты</a>
    </li>
</ul>

```
