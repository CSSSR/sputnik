# Короткие команды

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
