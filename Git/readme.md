#                   Git курс

## 1. Введение 
   Git - 1. Система контроля версий. 2. Хранилище истории разработки.

--- Установка windows. https://git-scm.com/book/en/v2/Getting-Started-Installing-Git?source=post_page

команда изменения редактора по умолчанию
```
git config --global core.editor \
"'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
```
 __Открыть папку с проектом__ - ПКМ на папке -> *Git bash here*      
 
## 2. Основы
#### 2.1 конфигурации
   - __Создание git-репозитория__ `git init`
   - __Настройка имени__ `git config user.name Badma`
   - __Настройка почты__ `git config user.email Badma@mail.ru`
   - __Просмотр локальных настроек__ `cat .git/config`
   - __Глобальные настройки__ `git config --global user.name Boris`
   - __Вывод всех настроек__ `git config --list`
   - __Вывод только глобальных настроек__ `git config --list --global`
   - __Удаление настройки пользователя__ `git config --unset user.name`
   - __Удаление секции пользователя__ `git config --remove-section user`
   -  __Редакторы:__ https://docs.github.com/en/github/getting-started-with-github/associating-text-editors-with-git
   - __Alias__ 
   - __Вывод команд config__ `git config -h`
   - __Вывод подробности команды__ `git help config`
   ` 
#### 2.2 Создание репозитория
   - __Создание git-репозитория__ `git init`
   - 2-х ступенчатая система хранения: 1) Index; 2) Repository.
   - `git add index.html` файл _index.html_ добавляется в Index
   - `git commit` добавляем в Repository
   - `git status` статус
   - Коммит 1-я строка заголовочная без точки
   - Коммит 2-я строка должна быть пустая
   - Коммит 3-я строка подробности
 
#### 2.3 Права на файлы
   - git сохраняет право только _Есть право исполнять файл_ или _Нет права исполнять файл_
   - create mode 100644 Index.html
   - 100 - файл
   - 644 - _нет права исполнять файл_
   - 755 - _есть право исполнять файл_
   - windows filemode по умолчанию false. 644  

#### 2.4 Автор коммиттер
   - `git commit --author='buda <buda@mail.ru> --date '...'` - поменять автора

#### 2.5 Добавление файлов
   - добавление каталога. в катологе должен быть файл, git не работает с пустыми каталогами. Например помещают файл .gitkeep 
   - `git add.` - передать весь текущий каталог
   - `git reset HEAD dst_katalog` - сбрасывает изменения в индексе для dst_katalog
   - `.gitignore` указываем файлы к-е git будет игнорировать
   - `git add -f dst_katalog/pr.txt` добавляет файл в обход gitignore
   - `git commit -m 'Поправили проблему 34'` коммит без редактора.

#### 2.6 Хороший коммит
    Принцип атомарности и консистентности.

#### 2.7 Индекс
   `git add -p index.html` - добавление с выбором y-да, n - нет

#### 2.8 Коммиты без git add
   - `git commit -a -m`  коммит без редактора и без add
   - `git commit -am`
   - `git commit -all -m` 

#### 2.9 Удаление и переименование файлов
- Глобальный игнор-файл. `git config --global core.excludesFiles ~/.gitignore`
- Удаление файлов. 1) удаляем файл. 2) добавляем в индекс. 3) коммитим
- `git rm <путь>` - удаляет файл и добавляет изменения в индекс 
- `-r` - ключ для удаления папки
- `-f` - позволяет удалить файл с изменениями
- `-- cashed` удаление только из индекса
- Переименование файла git воспринимает как 2 операции удаление файла и добавление нового. 
- `git mv <old> <new> ` - Перименование и добавление в индекс одновременно.

## 3. Ветки    
#### 3.1 Введение
#### 3.2 Создание и переключение