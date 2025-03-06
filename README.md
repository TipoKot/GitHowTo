# GitHowTo

Эта инструкция должна помочь в первоначальной установке Git и настройке первого репозитория.

> Это руководство рассчитано на то, что вы уже имеете базовое представление о работе с командной строкой.

## Что такое Git?

Система контроля версий, или VCS (англ. Version Control System, или коротко VCS), — это программное обеспечение, которое помогает отслеживать изменения в программах, текстовых файлах, больших документах, веб-сайтах и так далее.

> Для обозначения систем контроля версий используют не только аббревиатуру VCS, но и SCM (от англ. Source Control Management — «система управления исходным кодом»).

Git один из таких продуктов.

## Установка Git

В зависимости от вашей операционной системы, процесс установки может отличаться, но сам процесс довольно простой.

### Windows
Если вы пользователь Windows, то Git у вас уже есть. Вы установили его в составе пакета Git for Windows вместе с командной строкой.

Убедитесь в этом. Откройте консоль и выполните эту команду.
```bash
git version
```
Если Git установлен правильно, консоль выведет его текущую версию. 

### macOS

Для установки Git на macOS существует два способа. Здесь я расскажу только про первый.

Откройте консоль и выполните команду `/usr/bin/git`. Она запустит установщик. Нажмите *Install* и дождитесь окончания установки.

Когда установка завершится, для проверки выполните эту команду.
```bash
git version
```
Если на экран выводится текущая версия Git, значит, установка прошла успешно.

## Как сделать папку репозиторием

Чтобы Git начал отслеживать изменения в проекте, папку с файлами этого проекта нужно сделать Git-репозиторием.

Для этого следует переместиться в неё и ввести команду `git init`.

Если вы видите сообщение `Initialized empty Git repository in <*ваша папка с проектом*>/.git/`, значит все прошло хорошо.

Готово! Репозиторий инициализирован.

Команда `git init` — одна из редко применяемых, ведь репозиторий создаётся один раз, а пользоваться им можно сколько угодно долго.

### «Разгитить» папку, если что-то пошло не так

Если вы случайно сделали Git-репозиторием не ту папку, её можно «разгитить». Для этого нужно удалить скрытую подпапку `.git`.

	$ cd <папка с репозиторием> # перешли в папку

	$ rm -rf .git # удалили подпапку .git

Будьте осторожны: в подпапке `.git` хранится история изменений. Если удалить `.git`, то вся история проекта будет стёрта без возможности восстановления — останется только последняя версия файлов.

## Проверить состояние репозитория — git status

После инициализации репозитория запустите команду `git status` — она показывает текущее состояние репозитория.

Команда `git status` выведет:
- название текущей ветки: `On branch master` или `On branch main`;
- сообщение о том, что в репозитории ещё нет коммитов: `No commits yet`;
- сообщение, которое говорит: «чтобы что-нибудь закоммитить, нужно сначала это создать» — `nothing to commit (create/copy files and use "git add" to track)`.

В отличие от `git init`, команду `git status` используют часто. В любой непонятной ситуации стоит посмотреть состояние (статус) репозитория, а потом решить, что делать дальше.

## Подготовить файлы к сохранению

Команда `git add` запоминает текущее содержимое (контент) файла (подготавливает файлы к коммиту).

> Команда `git add` используется в Git для добавления изменений в *индекс (staging area)* перед фиксацией (`git commit`). Это первый шаг в процессе сохранения изменений.

1. Добавить конкретный файл
```bash
git add file.txt
```
Добавляет `file.txt` в индекс.

2. Добавить несколько файлов
```bash
git add file1.txt file2.txt
```
Добавляет несколько указанных файлов.

3. Добавить все измененные файлы в текущей папке
```bash
git add
```
Добавляет *все новые и измененные файлы* (не включает удаленные файлы).

4. Добавить все файлы (включая удаленные)
```bash
git add -A
```
Эквивалентно `git add --all`. Добавляет *все файлы*, включая удаленные.

5. Добавить все файлы в текущей папке и вложенных папках
```bash
git add *
```
Добавляет все файлы, кроме скрытых (.gitignore тоже влияет).

---

Есть и другие команды, но это основные.

## Выполнить коммит

Сделать коммит можно командой `git commit` c ключом `-m`, который присваивает коммиту сообщение.

Обычно в таком сообщении поясняется, в чём именно состояли изменения. Это как заметки на полях: благодаря им проще читать и понимать текст. Сообщение коммита выполняет те же функции — улучшает понимание и упрощает навигацию. Оно пишется после ключа `-m` в кавычках.

Например:
```bash
git commit -m ‘Мой первый коммит!’
```

## Просмотреть историю коммитов

Чтобы увидеть историю коммитов, введите команду `git log`.

Обратите внимание, что по умолчанию `git log` выводит коммиты в обратном хронологическом порядке — последние коммиты оказываются первыми сверху. В этом можно убедиться, если посмотреть на дату и время их создания.