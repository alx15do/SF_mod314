## git log

**git log** покажет список последних коммитов и их хеши *SHA1*. Список выводится начиная с последнего коммита.


Существует множество вариантов отображения истории. 

**Например**:

```bash=
git log --pretty=oneline
git log --oneline --max-count=2
git log --oneline --since="5 minutes ago"
git log --oneline --until="5 minutes ago"
git log --oneline --author="Your Name"
git log --oneline --all
```

Полный список команд на странице руководства [git-log](https://git-scm.com/docs/git-log)

**Например:**

```bash=
git log --pretty=format:"%h %ad | %s%d [%an]" --date=shor
```

Рассмотрим данный пример в деталях:

+    --pretty="..." — определяет формат вывода.
+    %h — укороченный хеш коммита.
+    %ad — дата коммита.
+    | — просто визуальный разделитель.
+    %s — комментарий.
+    %d — дополнения коммита («головы» веток или теги).
+    %an — имя автора.
+    --date=short — сохраняет формат даты коротким и симпатичным.


Предпочитаемый формат вывода по умолчанию можно определить в конфигурации Git с помощью команды **[git config](./config.md)**, например:

```bash=
git config --global format.pretty '%h %ad | %s%d [%an]'
git config --global log.date short
```

---
[[Содержание]](./README.md)