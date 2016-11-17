# Соглашение по именованию коммитов

Используется подход conventional changelog.

## Формат

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

### Типы

- `feat` - новая фича;
- `fix` - багофикс;
- `docs` - изменения в документации;
- `style` - форматирование кода или любые другие изменения, не влияющие на работу кода;
- `refactor` - изменения в коде, которые не относятся к фиксам или фиче;
- `test` - добавлен или обновлён тест;
- `chore` - изменения в сборщике, зависимостях и т.п.

### Область

Может быть любым специфичным местом в коде, в котором были изменения. **Не допускается более одной области.**

### Сообщения

- Только английский язык, никакого транслита;
- Используйте настоящее время, например, `change`, но не `changed` или `changes`;
- Первое слово с прописной буквы, не с заглавной;
- Не ставьте точку на конце.
