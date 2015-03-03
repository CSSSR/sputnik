# Grunt - сборщик проектов

**Статус:** черновик.

При разработке сайтов мы используем систему сборки - [Grunt](http://gruntjs.com/), которая легко расширяется.

Про Grunt можно подробно почитать по ссылкам:
* [gruntjs.com](https://gruntjs.com/) - официальный сайт Grunt.
* [Grunt для тех, кто считает штуки вроде него странными и сложными](http://frontender.info/grunt-is-not-weird-and-hard/).
* [Сборка сайтов на независимых блоках из Jade и Stylus с использованием Grunt.js](http://oleggromov.com/slides/independent-blocks-assemble/).
* [Grunt: система сборки для фронтенд-разработчиков](http://sapegin.ru/pres/grunt/).

Для старта проекта нам понадобится уже готовый шаблон - **[CSSSR Project Template](https://github.com/CSSSR/csssr-project-template)**.

Ставьте :star: Star и подписывайтесь на обновления шаблона, чтобы всегда использовать последнюю версию.

## 1. Старт

### 1.1. Установка программ

1. Устанавливаем [Node.js](http://nodejs.org/download/), включающий в себя NPM (Node Packet Manager).
2. `npm i -g grunt-cli` - устанавливаем Grunt CLI (интерфейс командной строки).<br>
После этого следует закрыть и заново открыть окно терминала (Bash/Git-Bash).<br>
Если при вызове команды `grunt` пишет ошибку `Command Not Found`, то нужно перезагрузиться или выйти из системы и зайти снова.
3. Устанавливаем [Git](http://git-scm.com/book/ru/Введение-Установка-Git) под Вашу ОС, если ещё не установлен.

Эти 3 шага выполняются один раз.


### 1.2. Скачивание шаблона

1. `git clone git@github.com:CSSSR/csssr-project-template.git new-project` - cкачать в папку `new-project`.
2. `cd new-project` - переход в папку `new-project`.
3. `git remote add origin git@github.com:CSSSR/new-project.git` - установка репозитория `new-project` для последующей отправки изменений `git push -u origin master`.

### 1.3. Команды для работы с NPM

- `npm i` - установка пакетов, заданных в `package.json` в секции `devDependecies` (устанавленные в текущей папке) и `dependecies` (используются глобально установленные пакеты). Обычно установка выполняется один раз, если пакеты не изменяются.
- `npm i -D package-name` - установка пакета `package-name`, добавляя его в `package.json`.
- `npm un -D package-name` - удаление пакета `package-name`, удаляя его из `package.json`.
- `npm up -D` - обновление версий пакетов и их зависимостей, обновляя версии в `package.json`.

### 1.4. Команды для работы с Grunt

* `grunt` - очищается папка `dist/`, компилируются и копируются файлы в `dist/`, запускается сервер с доступом к сайту по адресу [`http://localhost:3000`](http://localhost:3000) и отслеживаются изменения файлов. Для выключения нажать `ctrl + c` или закрыть консоль.
* `grunt build` - очищается папка `dist/`, компилируются и копируются файлы в `dist/` только один раз.

Перед коммитом обязательно сделать `grunt build`, чтобы папка очистилась от лишних файлов.


## 2. Что включено в шаблон CSSSR Project Template

### 2.1. Пакеты NPM

Для повседневных задач нам достаточно:
* [`bump`](https://www.npmjs.org/package/grunt-bump) - обновление версии проекта.
* [`clean`](https://www.npmjs.org/package/grunt-contrib-clean) - очистка папки от файлов.
* [`spritesmith`](https://www.npmjs.org/package/grunt-spritesmith) - генератор спрайтов и CSS переменных.
* [`imagemin`](https://www.npmjs.org/package/grunt-contrib-imagemin) - сжатие картинок.
* [`stylus`](https://www.npmjs.org/package/grunt-contrib-stylus) - препроцессор CSS.
* [`autoprefixer`](https://www.npmjs.org/package/grunt-autoprefixer) - подстановка префиксов для заданных браузеров.
* [`combine-media-queries`](https://www.npmjs.org/package/grunt-combine-media-queries) - комбинирование медиа-запросов в CSS.
* [`csscomb`](https://www.npmjs.org/package/grunt-csscomb) - форматирование CSS.
* [`jade`](https://www.npmjs.org/package/grunt-contrib-jade) - препроцессор HTML.
* [`prettify`](https://www.npmjs.org/package/grunt-prettify) - форматирование HTML.
* [`jshint`](https://www.npmjs.org/package/grunt-contrib-jshint) - проверка JavaScript на качество кода с подсказками.
* [`copy`](https://www.npmjs.org/package/grunt-contrib-copy) - создание копий файлов.
* [`uglify`](https://www.npmjs.org/package/grunt-contrib-uglify) - минифицирование и обфускация скриптов.
* [`replace`](https://www.npmjs.org/package/grunt-replace) автозамена паттернов на заданные значения.
* [`newer`](https://www.npmjs.org/package/grunt-newer) - выполнение задач только с новыми файлами.
* [`browser-sync`](https://www.npmjs.org/package/grunt-browser-sync) - локальный сервер и автоперезагрузка страницы с уведомлениями.
* [`watch`](https://www.npmjs.org/package/grunt-contrib-watch) - отслеживание изменений файлов и их компиляция.

В зависимости от проекта дополнительно могут пригодиться такие пакеты:
* Для объединения и минификации:
    * [`cssmin`](https://www.npmjs.org/package/grunt-contrib-cssmin) - минификация CSS.
    * [`concat`](https://www.npmjs.org/package/grunt-contrib-concat) - объединение скриптов в один файл.<br>
      *Если возникают ошибки при конкатенации скриптов, то нужно установить порядку их зависисмости*.
    * [`uglify`](https://www.npmjs.org/package/grunt-contrib-uglify) - обфускация скриптов.

* Препроцессоры:
    * [`coffee`](https://www.npmjs.org/package/grunt-contrib-coffee) - CoffeeScript препроцессор JavaScript.
    * [`less`](https://www.npmjs.org/package/grunt-contrib-less) - Less препроцессор CSS.
    * [`sass`](https://www.npmjs.org/package/grunt-contrib-sass)/[`compass`](https://www.npmjs.org/package/grunt-contrib-compass) - Sass препроцессор CSS.


* Если этого будет недостаточно, можно поискать подходящие по ссылкам:
    * [gruntjs.com/plugins](https://gruntjs.com/plugins)
    * [npmjs.org](https://www.npmjs.org/)


### 2.2. Структура папок и файлов

```
├── app/                               # Исходники
│   ├── images/                        # Папка изображений
│   │   ├── sprite/                    # PNG изображения для генерации спрайта
│   │   └── sprite.png                 # Спрайт
│   ├── resources/                     # Статические файлы для копирования в dist/
│   ├── scripts/                       # Папка со скриптами
│   │   ├── libs                       # Папка с библиотеками и плагинами
│   │   │   └── jquery-2.1.1.min.js    # Библиотека jQuery
│   │   |── debug.js                   # Идентификация отладки на локальном сервере
│   │   └── common.js                  # Главный скрипт
│   ├── styles/                        # Папка со стилями Stylus
│   │   ├── base/                      # Базовые стили
│   │   │   ├── base.styl              # Базовый стилевой файл
│   │   │   ├── fonts.styl             # Подключение шрифтов
│   │   │   └── normalize.styl         # Сброс стилей
│   │   ├── blocks/                    # Стили блоков
│   │   |   └── main.styl              # Стили блока главной страницы
│   │   ├── components/                # Компоненты (кнопки, тестовые поля и т.п.)
│   │   ├── helpers/                   # Помощники
│   │   │   ├── mixins.styl            # Премиси
│   │   │   ├── sprite.styl            # Переменные с данными спрайта
│   │   │   └── variables.styl         # Переменные
│   │   ├── partials/                  # Стили частиц страниц
│   │   │   ├── footer.styl            # Стили подвала
│   │   │   └── header.styl            # Стили шапки
│   │   └── common.styl                # Главный стилевой файл
│   ├── templates/                     # Папка с шаблонами Jade
│   │   ├── blocks/                    # Папка с подключаемыми блоками
│   │   ├── helpers/                   # Папка с помощниками
│   │   │   ├── mixins.jade            # Миксины
│   │   │   └── variables.jade         # Переменные
│   │   ├── layouts/                   # Папка с шаблонами раскладки
│   │   │   └── default.jade           # Шаблон раскладки по умолчанию
│   │   ├── pages/                     # Папка с генерируемыми страницами
│   │   │   └── index.jade             # Шаблон одной из страниц
│   │   └── partials/                  # Папка с подлючаемыми шаблонами
│   │       ├── footer.jade            # Шаблон подвала
│   │       ├── head.jade              # Шаблон с ресурсами, SEO и мета-тегами
│   │       ├── header.jade            # Шаблон шапки
│   │       └── scripts.jade           # Шаблон со скриптами
│   └── favicon.ico                    # Иконка сайта
├── dist/                              # Сборка для заказчика
│   ├── assets/                        # Подключаемые ресурсы
│   │   ├── images/                    # Папка изображений
│   │   ├── scripts/                   # Папка скриптов
│   │   └── styles/                    # Папка стилей
│   └── index.html                     # Индексная страница
├── .csscomb.json                      # Конфигурация форматирования CSS
├── .editorconfig                      # Конфигурация настроек редактора кода
├── .gitignore                         # Список исключённых файлов из Git
├── Gruntfile.js                       # Список задач для Grunt
├── package.json                       # Список пакетов и прочей информации
└── readme.md                          # Документация шаблона
```

Описание для некоторых папок:
* `app/` - папка с иходниками, из которой генерируюется `dist/`.
* `app/images/` - папка с фонами, паттернами и прочими стилевыми изображениями.
* `app/images/blocks/` - папка для картинок, относящихся к определённм блокам, по умолчанию папки нет.
* `app/images/sprite/` - папка с PNG-изображениями для генерации спрайта в `app/images/sprite.png` и файла стилей с CSS-переменными в `app/styles/sprite.styl`.
* `app/images/temp/` - папка для временного контента, например, для товаров, аватарок, обложек и т.п., *по умолчанию папки нет*.
* `app/resources/assets/data/` - папка для данных в формате `json`, *по умолчанию папки нет*.
* `app/resources/assets/fonts/` - папка для шрифтов, *по умолчанию папки нет*.
* `app/images/resources/assets/images/svg/` - папка для векторных изображений SVG, *по умолчанию папки нет*.
* `dist/` - сборка сайта для заказчика, по умолчанию её может не быть и можно без страха и риска её удалить, т.к. она генерируется каждый раз заново, при сборке всё её содержимое удаляется, поэтому руками в неё класть ничего не нужно.


## 3. Autoprefixer - автоподстановка префиксов для стилей

Для автоматической подстановки префиксов в зависимости от заданных минимальных версий браузеров используется [grunt-autoprefixer](https://www.npmjs.org/package/grunt-autoprefixer), при этом самим указывать префиксы в стилях, делать для них миксины или использовать готовые не нужно.

Версии браузеров указываются в [`package.json`](https://github.com/CSSSR/csssr-project-template/blob/master/package.json#L55-L63).

```javascript
"browsers": {
    "android": 4,
    "chrome": 36,
    "firefox": 31,
    "ie": 10,
    "ios": 6,
    "opera": 12,
    "safari": 6
}
```


## 4. BrowserSync - автоперезагрузка страницы и оповещения

Каждый раз, когда изменяются и компилируются исходники происходит автоперезагрузка страницы с помощью [`grunt-browser-sync`](https://www.npmjs.org/package/grunt-browser-sync), при этом в окне браузера наверху справа будет появляться уведомление.


## 5. Список страниц

Если на проекте страниц больше одной, то необходимо сделать список со страницами.

В качестве списка используется индексная страница `index.jade` (`index.html`).

Список страниц должен быть оформлен в соответсвии с дизайном сайта:
* Логотип сайта.
* Ссылки по цветовой гамме сайта.
* Список и логотип должны быть отцентрированы.
* **Стили должны быть встроены в страницу, подключать внешний стилевой файл или использовать стили сайта не нужно**.
* Страница должна быть валидной и корректно отображаться на мобильных устройствах.
