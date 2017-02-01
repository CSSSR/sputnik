# Git - система контроля версий
![git](http://git-scm.com/images/logo@2x.png)


## 1. Устанавливаем Git

### 1.1. Устанавливаем консольную версию
#### macOS
Если у вас macOS и установлены XCode или Command Line Tools, Git уже установлен.
Чтобы убедиться в этом, наберите в терминале `git --version`.

```
$ git --version
git version 2.9.3 (Apple Git-75)
```

Если вы хотите установить более новую версию, есть несколько способов:

##### Установка через [Homebrew](http://brew.sh/) (рекомендуемый способ)
Если вы используете [Homebrew](http://brew.sh/), установите Git, набрав следующую команду в консоли.

```
$ brew install git
```

##### Установка через [Git for Mac Installer](https://sourceforge.net/projects/git-osx-installer/files/)
1. Скачайте [Git for Mac Installer](https://sourceforge.net/projects/git-osx-installer/files/)
2. Запустите и следуйте инструкциям

#### Windows
Если у вас Windows - скачайте и установите [msysgit.github.io](http://msysgit.github.io/).

#### Linux
Если у вас Linux, скорее всего, вы знаете что делать.  
Если нет, вам помогут эти команды:

```
$ sudo apt-get update
$ sudo apt-get install git
```

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

* Если конфликтов больше нет и `rebase` завершился, то на этом всё. Если конфликты есть, то повторить итерацию.

### 3.5. Создаём фичу в отдельной ветке

#### 3.5.1. Создаём ветку

* `git pull --rebase origin master` - обновляем ветку `master` с ключом `--rebase`, чтобы избежать промежуточных коммитов.
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
