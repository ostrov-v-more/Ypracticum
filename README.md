

## Про GIT шпаргалОчка

### Git команды
Поменять vim на nano по умолчанию
```
git config --global core.editor nano
nano $HOME/.gitconfig
```

```git clone``` - клонирование репозитория вместе со всей его историей изменений

```git init {название}``` - создаёт новый локальный репозиторий с заданным именем

```git status``` - перечисляет все новые или изменённые файлы, которые нуждаются в фиксации

Показывает различия по внесённым изменениям в ещё не проиндексированных файлах
```
git diff
	git diff --staged Показывает различия между проиндексированной и последней зафиксированной версиями файлов
	git diff HEAD...origin/master - где HEAD локальная ветка, а origin/master удаленная  
```

```git add {файл}``` - индексирует указанный файл для последующего коммита

Создает коммит
```
git commit
	-a  добавляем все файлы в коммит
	-m «комментарий» добавляем комментарий
git commit --amend --reset-author - поправить сообщение в коммите
```
Возврат к предыдущему коммиту
```
git reset HEAD~1
git reset {файл] отменяет индексацию указанного файла, при этом сохраняет его содержимое
```
Показать все удаленные репозитори связанные с локальным
```
git remote -v
git remote add [имя_репы] [ssh|https] добавляем новый (второй) удаленный репозиторий
```

``git cat`` - предоставляет информацию о содержимом, типе и размере объектов из репозитория Git.



```git Fetch``` - собирает все коммиты из целевой ветки, которых нет в текущей ветке, и сохраняет их в локальном реопзитории, но не сливает их в текущую ветку.

```git merge``` - перенос изменений из одной ветки в другую
```git merge {имя ветки}``` переносит изменения из ветки в мастерветку (HEAD на мастерветке)
```--abort``` прерывание слияния

```git pull``` - извлекает изменения из указанного удаленного репозитория и сливает с текущей веткой

```git push``` - отправка изменений на удаленный сервер

```
git push -u origin {имя ветки} - уоздание ветки в удаленном репозиторие которая соответствует локальной ветке
git push origin --delete {имя_ветки}  - удаление ветки из удаленного репозитория
Или
git push origin :{имя ветки} - удаление ветки из удаленного репозитория
```

```git log``` - посмотреть историю коммитотв
```git log -- author {имяавтора}``` - коммиты этого автора

```git show {хэш коммита}``` - пишет какие изменения проводились: автор, дата, разницу в файлах, изменялось ли имя файла, в каких строках проводились изменения, какие изменения проводились в файле


```git blame {имя_файла}``` - информация какие изменения вводил тот или иной автор в файл
```
git blame имя_файла | grep 123 кто вносил текущее изменение
git blame имя_файла | grep имя_автора какие изменения вводил автор
```

```git checkout {имя файла}``` - откатить изменения в файле
```
git checkout . - все файлы в папке
git checkout {имя_ветки} - переключение на нужную ветку
git checkout - (с тире) переход на мастерветку
git checkout -b имя_ветки создает ветку и переключается на нее
git checkout -b локальная_ветка origin/удаленная_ветка копирование удаленной ветки себе
```

```git stash``` - скрываем изменение в файле (временное удаление к которому можно вернуться)
```
git stash pop - возврат изменения в файл
git stash clear - очистка временного хранилища
```

```git branch {имя ветки}``` - создание новой ветки
```
git branch показывает названия всех веток
    -r показать удаленные ветки
    -a  показать все ветки
git branch -m имя_ветки имя2_ветки переименовываем ветку
git branch -d имя_ветки удаление ветки
```

### Схема статустов в git
```mermaid
graph TD
    untracked --> staged
    staged --> tracked
    modified --> staged
    tracked --> modified
```
