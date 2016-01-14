# Git - система контроля версий
![git](http://git-scm.com/images/logo@2x.png)


## 1. Устанавливаем Git

### 1.1. Устанавливаем консольную версию
Если у вас OS X - в консоли набрать `$ sudo port install git-core +doc +bash_completion +gitweb`.

Если у вас Windows - скачать и устанвоить из [msysgit.github.io](http://msysgit.github.io/).

### 1.2. По желанию устанавливаем Git клиент с GUI интерфейсом (не обязательно)

* [GitHub Windows](https://windows.github.com/) - Git-клиент с GUI от GitHub для Windows 7, 8 и 8.1.

* [GitHub Mac](https://mac.github.com/) - Git-клиент с GUI от GitHub для Mac OS X 10.9+.

* [Git для Windows](http://msysgit.github.io/) - 3 в 1: Git, bash-консоль и простой GUI-клиент.

* [SourceTree](http://www.sourcetreeapp.com) - бесплатный Git-клиент. Позволяет работать с Git без консоли в графической среде. Работает под Windows 7+ и Mac OS X 10.7+. Мультиязычное приложение.
Чтобы использовать SourceTree, обязательно нужно изучить основы Git и уметь работать с ним в консоли.

## 2. Знакомимся с Git

### 2.1. Проходим обучающийся курс
Для новичков рекомендуется пройти небольшой обучающийся курс [Git How To](http://githowto.com/ru).

### 2.2. Полезные ссылки

#### 2.2.1. Разбираемся с Git
* [Git How To](http://githowto.com/ru) — это интерактивный тур, который познакомит вас с основами Git. Тур создан с пониманием того, что лучшим способом научиться чему-нибудь — сделать это своими руками.
* [Команды git](http://git-scm.com/book/commands) - полный список команд на официальном сайте
* [git - the simple guide](http://rogerdudler.github.io/git-guide/)
* [Ежедневная работа с Git](http://habrahabr.ru/post/174467/) - статья на Хабре
* [Что нам стоит Git настроить!](http://habrahabr.ru/post/164297/) - статья на Хабре

#### 2.2.2. Видео
* [Git & GitHub Tutorials](https://www.youtube.com/playlist?list=PLEACDDE80A79CE8E7)

#### 2.2.3. Книги
* [Pro Git](http://git-scm.com/book/ru/v2) - официальная книга Git
* [Магия Git](http://dl.dropboxusercontent.com/u/281916/delete/book.pdf)

#### 2.2.4. Шпаргалки
* [GitHub Cheatsheet](https://raw.githubusercontent.com/github/training-kit/master/downloads/github-git-cheat-sheet.pdf)


## 3. Работаем с Git

### 3.1. Стартуем проект из [шаблона](https://github.com/CSSSR/csssr-project-template):

* `git clone git@github.com:CSSSR/csssr-project-template.git new-project && cd new-project` - клонируем в папку `new-project` и переход в неё.
* `rm -rf .git` - удаляем папку `.git`, избавляясь от избыточной истории коммитов шаблона.
* `git init` - инициализируем Git.
* `git add -A` - индексируем все файлы.
* `git commit -m 'chore(project): init project'` - коммитим и комментируем в соответствии с соглашением по коммитоименованию.
* `git remote add origin <url>` - добавляем удалённый репозиторий, где `<url>` - ссылка на git-репозиторий.
* `git push origin master` - заливаем проект в удалённый репозиторий в ветку `master`.
* Если залить не удалось, проект уже не пустой и может содержать `readme.md`, поэтому нужно сделать `rebase`:
```
git pull --rebase origin master
```
* Если есть конфликты, то см. п. 3.4.
* Заливаем снова.

### 3.2. Разворачиваем уже имеющийся проект

* `git clone <url>` - клонируем проект.

### 3.3. Повседневная работа с проектом

* `git pull --rebase origin master` - обновляем ветку `master` с ключём `--rebase`, чтобы избежать промежуточных коммитов.
* Если конфликтов не произошло, то пропускаем этот пункт. Если есть, то правим руками (см. п. 3.4).
* Делаем изменения в коде, например, добавляем главную страницу.
* `git add -A` - индексируем изменения.
* `git commit -m 'feat(main): add main page'` - закоммитили в соответствии с соглашением по коммитоименованию.
* `git push origin master` - заливаем изменения в удалённый репозиторийй в ветку `master`.

### 3.4. Разрешаем конфликты

* Правим руками файлы, содержащие конфликты (посмотреть их можно через `git status`):
```
<<<<<<< HEAD
// 1 секция: Код текущей ветки
=======
// 2 секция: Наш изменения в коде
>>>>>>> master
```

Чтобы разрешить конфликт, нужно *внимательно* сравнить изменения в 1 секции и добавить недостающий (новый) код в свою (2 секцию). После этого удаляем всё, кроме 2 секции.

```
// 2 секция: Наш изменения в коде
```

* После этого индексируем изменения.
```
git add -A
```

* Далее нужно продолжить `rebase` с помощью команды:
```
git rebase --continue
```

* Если конфликтов больше нет и `reabase` завершился, то на это всё, если конфликты есть, то повторить итерацию.

### 3.5. Создаём фичу в отдельной ветке

#### 3.5.1. Создаём ветку

* `git pull --rebase origin master` - обновляем ветку `master` с ключём `--rebase`, чтобы избежать промежуточных коммитов.
* `git checkout -b feature/<name>` - создаём ветку с `feature/<name>`, где `<name>` - название фичи.
* Делаем изменения в коде, например, добавляем главную страницу.
* `git add -A` - индексируем изменения.
* `git commit -m 'feat(main): add main page'` - закоммитили в соответствии с соглашением по коммитоименованию.
* `git push origin feature/<name>` - заливаем нашу ветку в удалённый репозиторий.


#### 3.5.2. Делаем `rebase` нашей фичи в основную ветку `master`.

* Находясь в ветке фичи выполняем команду:
```
git rebase master
```
* Если конфликтов нет, то пропускаем этот пункт. Если есть, то разрешаем конфликты (см. п. 3.4).
* Переходим в ветку `master` и сливаем в неё фичу:
```
git merge feature/<name>
```
* `git push origin master` - заливаем итоговые изменения в удалённый репозиторий.

### 3.6. Полезные команды на всякий случай

* `git commit --amend` - позволяет изменить название коммита. Если нужно включить ещё и изменённые файлы, то перед этим проиндексировать файлы.
* `git reset --hard HEAD^` - полное удаление последнего коммита.

## 4. Настройка коротких команд
Чтобы было удобней работать, можно настроить алиасы для коротких команд.

**Для пользователей OS X.**

1. В консоли набрать `nano ~/.bash_profile`.
2. Добавить нужные строки.
3.  Ctrl+X  — Выйти.<br>
    Y       — Сохранить.<br>
    [Enter] — Да, заменить.


**Для пользователей Windows.**

Алиасы находятся в файле [`.profile`](https://gist.github.com/felixexter/ad648218634f9491a5b9).

в папке профиля `c:\users\<profile>\`, где `<profile>` - имя вашего профиля, если такого файла нет, то его нужно создать.

[**Список коротких команд:**](https://gist.github.com/felixexter/ad648218634f9491a5b9)
```php
# Отображение текущего состояния.
alias gs='git status '
 
# Отображение коммитов с коротким названием, датой, комментарием и автором.
alias gl='git --no-pager log --pretty=format:"%h | %ad | %s%d [%an]" --graph --date=short'
alias glo=gl
alias glog=gl
 
# Добавление всех файлов с учётом удалённых и отображение текущего состояния.
alias gall='git add --all && git status'
alias gal=gall
alias ga=gall
 
# Добавление всех файлов с учётом удалённых и коммит с комментарием.
alias gam='git commit -am '
 
# Коммит с комментарием.
# Пример: gc 'Fixed bug.'
alias gc='git commit -m '
 
# Отображает текущую ветку среди всех имеющихся.
alias gb='git branch '
 
# Отправка в произвольную ветку.
# Пример: gpo master
alias gpo='git push origin '
 
# Отправка в ветку master.
alias gpm='git push origin master'

# Скачивание обновлений в ветку по умолчанию.
alias gpl='git pull '
 
# Скачивание обновлений в произвольную ветку.
# Пример: gplo mybranch
alias gplo='git pull origin '
 
# Скачивание обновлений в произвольную ветку и ребэйз.
# Пример: gpro master
alias gpro='git pull --rebase origin '
 
# Слияние ветки с ребэйзом
# Пример: gr mybranch
alias gr='git rebase '
 
# Продолжить ребэйз
# Пример: grc
alias grc='git rebase --continue '
 
# Скачивание обновлений всех последних изменний во всех ветках.
alias gfo='git fetch origin '
 
# Слияние веток.
# Пример: gm mybranch
alias gm='git merge '
 
# Слияние веток с флагом --no-ff.
# Пример: gmnf mybranch
alias gmnf='git merge --no-ff '
alias gmnff=gmnf
 
# Отмена коммита.
# Пример: gback
alias gback='git reset --soft HEAD^'
 
# Переключение по веткам.
# Пример: go master
alias go='git checkout '
 
# Создание новой ветки.
# Пример: gob new-branch
alias gob='git checkout -b '
 
# Дополнительные алисы на случай опечатки.
alias got='git '
alias get='git '

```

Эти алиасы не являются обязательными, настроить их можно так, как вам удобно.

После создания/изменения алиасов необходимо закрыть консоль и открыть заново, чтобы алиасы были доступны.

### 5. Соглашение по именованию коммитов

Используется подход conventional changelog.

#### 5.1. Формат

Каждый коммит начинается с **типа (type)**, **области (scope)** и **сообщения (subject)**.

В самом конце может быть **описание (body)** с замечанием и т.п.

- `type` - тип изменений, который содержит коммит;
- `scope` - область кода, в которой производились изменения;
- `subject` - сообщение;
- `body` (не обязательно) - подробно описание изменнений или важное замечание.

```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
```

Примеры:

```
feat(ruler): add inches as well as centimeters
fix(protractor): fix 90 degrees counting as 91 degrees
refactor(pencil): use graphite instead of lead

Closes #640.

Graphite is a much more available resource than lead, so we use it to lower the price.
fix(pen): use blue ink instead of red ink

BREAKING CHANGE: Pen now uses blue ink instead of red.

To migrate, change your code from the following:

`pen.draw('blue')`

To:

`pen.draw('red')`
```

Каждая строка в коммите может содержать не более 100 символов.

#### 5.2. Типы

- `feat` - новая фича;
- `fix` - багофикс;
- `docs` - изменения в документации;
- `style` - форматирование кода или любые другие изменения, не влияющие на работу кода;
- `refactor` - изменения в коде, которые не относятся к фиксам или фиче;
- `test` - добавлен или обновлён тест;
- `chore` - измененения в сборщике, зависимостях и т.п.

#### 5.3. Область

Может быть любым специфичным местом в коде, в котором были изменения. **Не допускается более одной области.**

#### 5.4. Сообщения

- Только английский язык, никакого транслита;
- Используйте настоящее время, например, `change`, но не `changed` или `changes`;
- Первое слово с прописной буквы, не с заглавной;
- Не ставьте точку на конце.
