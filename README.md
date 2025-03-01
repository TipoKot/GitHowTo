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

`git version`

Если Git установлен правильно, консоль выведет его текущую версию. 

### macOS

Для установки Git на macOS существует два способа. Здесь я расскажу только про первый.

Откройте консоль и выполните команду `/usr/bin/git`. Она запустит установщик. Нажмите *Install* и дождитесь окончания установки.

Когда установка завершится, для проверки выполните эту команду.

`git version`

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