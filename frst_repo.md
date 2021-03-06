[< к содержанию](./readme.md)

![repo-logo](./assets/repo-logo.jpg)

## Создание репозитория и первый «коммит»

Для того чтобы создать репозиторий, для начала, создайте папку, в которой он будет располагаться. В нашем случае это будет каталог с названием *repo*.  
`> mkdir repo`  
Теперь перейдем в этот каталог.  
`>cd repo`  
Создадим в нем пустой *git* репозиторий.  
`> git init`  
Если мы посмотрим на список коммитов, которые были отправлены в репозиторий, то увидим, что он пустой – это правильно, т.к. мы пока только создали репозиторий и ничего ещё туда не отправляли.
```bash=
> git log
fatal: your current branch 'master' does not have any commits yet
```
Для просмотра состояния рабочего каталога воспользуемся командой *git status*.
```bash=
> git status
On branch master

Initial commit

nothing to commit (create/copy files and use "git add" to track)
```
Создадим в нашем каталоге пустой файл.  
`> touch README.md`  
Теперь, если мы выполним команду *git status*, то увидим, что в нашем каталоге появился один неотслеживаемый файл: *README .md*.
```bash=
> git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        README.md

nothing added to commit but untracked files present (use "git add" to track)
```
Добавим, созданный файл в *stage*. *Stage* (или *cache*) – это хранилище для файлов с изменениями, информация о которых попадет в единый коммит. *Stage* является элементом архитектуры трех деревьев, на базе которой построен *Git*, более подробно смотрите [здесь](https://devpractice.ru/git-for-beginners-part-4-git-arch/). Для добавления файла *README .md* в stage необходимо воспользоваться командой *git add*.  
`> git add README .md`  
Если изменение было произведено в нескольких файлах, и мы хотим их все отправить в *stage*, то вместо имени файла поставьте точку.
Выполним *git status* для того, чтобы посмотреть на то, что сейчас происходит в нашем каталоге.
```bash= 
> git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   README.md
```
Как видно, в *stage* был добавлен один файл с именем README. md и теперь представленный набор изменений готов к отправке в репозиторий – т.е. к "коммиту". Сделаем это.
```bash=
> git commit -m "[create repository]"
[master (root-commit) 500067c] [create repository]
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
```
Проверим статус каталога.  
```bash=
> git status
On branch master
nothing to commit, working tree clean
```
Как видно с момента последнего коммита никаких изменений в рабочем каталоге не производилось.
Теперь взглянем на список коммитов.
```bash=
> git log
commit 500067cc0b80643d38e2a24e9e0699031ada6be3
Author: Writer <writer@someserver.com>
Date:   Mon Feb 12 22:51:14 2018 +0500

    [create repository]
```
Из приведенной информации видно, что был отправлен один коммит, который имеет *ID*: 500067cc0b80643d38e2a24e9e0699031ada6be3. Автор данного коммита *Writer*, он (коммит) был создан Mon Feb 12 22:51:14 2018 +0500, с сообщением:  *[create repository]*. Это довольно подробная информация, когда коммитов станет много, такой формат вывода будет не очень удобным, сокращенный вариант выглядит так.
```bash=
> git log --oneline
500067c [create repository]
```
Подведем небольшое резюме вышесказанному.  
Создание пустого репозитория:  
`> git init`  
Добавление файлов в stage:  
`> git add filename`  
Создание коммита:  
`> git commit -m “message”`  
Просмотр статуса каталога:  
`> git status`  
Просмотр коммитов в репозитории:  
`> git log`  
Просмотр коммитов в репозитории с сокращенным выводом информации:  
`> git log --oneline`  
Файл(-ы) находятся в *HEAD* вашей рабочей локальной копии. В вашем удаленном репозитории их все еще нет.  
Пуш в репозиторий:  
`git push origin master`  
Работа с удалёнными репозиториями:  
`git remote add origin [сервер]`

[< к содержанию](./readme.md)