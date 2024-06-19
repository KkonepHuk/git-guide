# Добро пожаловать в гайд по Git!
## Ниже будут представлены различные команды и инструкции для работы с Git.
----
### Важные обозначения:
- символ "**~**" (*тильда*) обозначает домашнюю директорию.
- символы "**..**" обозначают родительскую директорию.

----

```bash
$ pwd
```
(*print working directory*) выводит рабочую директорию.

----

```bash
$ cd
```
(*change directory*) с помощью данной команды происходит смена директории. Достаточно указать адресс нужной.

Например

```bash
$ cd ~
```
переместит вас в домашнюю директорию.

----

```bash
$ ls
```
(*list directory contents*) выводит содержимое директории.

----


## **Важная информация о связывании локального и удаленного репозиториев**

- Для начала создаем локальный репозиторий с помощью команды:

```bash
$ git init
```

- Заходим на GitHub и создаем новый репозиторий там.
- Копируем его SSH.
- Связываем репозитории с помощью команды:

```bash
$ git remote add origin "URL"
# Вместо "URL" вставляем скопированный SSH
```

- Проверяем, что сделали все верно:

```bash
$ git remote -v
```

*Ура! Мы связали репозитории!*


Теперь при первой отправке изменений на удаленный репозиторий нужно воспользоваться командой:

```bash
$ git push -u origin master
# Вместо 'master' может быть 'main', в зависимости от названия главной ветки
```

В дальнейшем для этой же цели используем:

```bash
$ git push
```

----

## **Типичный жизненный цикл файла в Git**

```mermaid
flowchart TD
	A[untracked] --> B{$ git add};
	B --> C{staged + tracked *в списке на коммит*};
	C --> D{$ git commit};
	D --> E{tracked};
	E --> F{изменения};
	F --> G{modified};
	G --> H{$ git add};
	H --> C
```