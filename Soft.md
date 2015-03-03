### [Sublime Text](http://www.sublimetext.com/) - кроссплатформенный редактор кода.
![Sublime Text](http://beta.hstor.org/storage2/8a4/83f/7a7/8a483f7a7efcf995491cb6d6a6474010.png)<br>

* [Скачать с официального сайта.](http://www.sublimetext.com/3)<br>
_Рекомендую установить **portable** версию для пользователей Windows._

* [Установка Package Control.](https://sublime.wbond.net/installation)<br>
Самый простой способ установки - это прямо в консоли Sublime Text. Консоль доступна с помощью `` ctrl+` `` или<br>
`View > Show Console menu`. После открытия вставьте соответствующий Python код для Вашей версии Sublime Text в консоль.

Для Sublime Text 3:
```python
import urllib.request,os,hashlib; h = '2deb499853c4371624f5a07e27c334aa' + 'bf8c4e67d14fb0525ba4f89698a6d7e1'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```

Для Sublime Text 2:
```python
import urllib2,os,hashlib; h = '2deb499853c4371624f5a07e27c334aa' + 'bf8c4e67d14fb0525ba4f89698a6d7e1'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler()) ); by = urllib2.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); open( os.path.join( ipp, pf), 'wb' ).write(by) if dh == h else None; print('Error validating download (got %s instead of %s), please try manual install' % (dh, h) if dh != h else 'Please restart Sublime Text to finish installation')
```

* Установка пакетов доступна с помощью `Preferences > Package Control`, в списке выбрать `Install Package`. Через несколько секунд появится список доступных пакетов.
Нас интересуют следующие пакеты:<br>
	* `Emmet` - [плагин для ускорения разработки](http://emmet.io/).
	* `Jade` - подсветка кода для Jade.
	* `Less` - подсветка кода для Less.
	* `Stylus` - подсветка кода для Stylus.
	* `CoffeeScript` - подсветка кода для CoffeeScript.

* Настройте редактор для удобства с помощью `Preferences > Settings - User`. После открытия файла пользовательских настроек вставьте код ниже и сохраните.
```js
{
	// Всегда отображается карта кода с рамкой текущего положения
	"always_show_minimap_viewport": true,

	// Карта с рамкой
	"draw_minimap_border": true,

	// Папки будут отображаться жирным шрифтом
	"bold_folder_labels": true,

	// Подсветка кода по умолчанию Monokai
	"color_scheme": "Packages/Color Scheme - Default/Monokai.tmTheme",

	// Переносы строк по умолчанию в стиле Unix.
	"default_line_ending": "unix",

	// Если кодировка файла не будет распознана, то файл будет открыт в Кириллице (Windows 1251)
	"fallback_encoding": "Cyrillic (Windows 1251)",

	// Исключение файлов и папок в боковой панели
	"folder_exclude_patterns": [
		".svn",
		".git",
		"node_modules"
	],

	// Размер шрифта
	"font_size": 8,

	// Подсветка текущей линии
	"highlight_line": true,

	// Подсветка табов редактируемых файлов
	"highlight_modified_tabs": true,

	// Добавляет вертикальную линию после 120 символов
	"rulers": [120],

	// Горячие клавиши `shift + tab` убирают 1 уровень отступа
	"shift_tab_unindent": true,

	// Отображает отступы табуляции и пробелов
	// Включать данный параметр необязательно, т.к. может затруднять чтение кода
	"draw_white_space": "all",

	// Убирает лишние табы и пробелы в конце строки
	"trim_trailing_white_space_on_save": true,

	// Добавляет новую строку в конце файла
	"ensure_newline_at_eof_on_save": true
}

```

* Добавляем проект в Sublime Text с помощью `Project > Add Folder to Project`. Выбрав папку с проектом, он появится на панели проектов слева, которую можно открыть с помощью последовательных комбинаций горячих клавиш `ctrl+k` и `ctrl+b` или `View > Side Bar > Show Side Bar`.<br>
В панели проектов будет доступно дерево папок и файлов проекта.

***

### [Fenix Web Server](http://fenixwebserver.com/)
![Fenix Web Server](https://camo.githubusercontent.com/a9eb02f67254c031f817674a02144b01b01ada2a/687474703a2f2f66656e69787765627365727665722e636f6d2f696d672f77696e33322f62616e6e65725f6465766963652e706e67)

### [Open Server](http://open-server.ru/) - платформа для веб-разработчика
![Open Server](http://open-server.ru/files/l2.png)
