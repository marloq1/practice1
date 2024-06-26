# Краткий конспект по работе с гитом

### 1. Командная строка

Необходимо овладеть коммандной строкой. Для этого необходимо [отсюда](https://git-scm.com/download/win) скачать **Standalone installer** для своей операционной системы (только Windows) 
Далее, открываем ее. Она находится: *C:\Program Files\Git\bin\bash.exe*. 

Основные команды здесь:
- cd (переход в нужную директорию)
- pwd (отображение текщего положения)
- ls (просмотр содержимого текущей дериктории)
- touch (создание файла)
- mkdir (создание папки)
- cp (копирование файлов)
- mv (перемещение файлов)
- cat (чтение содержимого файла *только для .txt*)
- rm (удаление файла)
- rmdir (удаление папки)

Также значком **&&** можно объединять команды.  
Стрелки вниз и вверх помогают быстро переключаться между уже использованными командами.  
TAB может подсказать ключевое слово по первым буквам.

### 2. Установка и настройка гита.

Для Windows гит устанавливается вместе с командной строкой. Кодом снизу можно задать свой ник и электронную почту.

```bash
git config --global user.name "User Namovich"
git config --global user.email username@yandex.ru
```

Для проверки записи используем:

```bash
cat ~/.gitconfig 
```

### 3. Создание git-проекта.

Необходимо сделать из обычной папки git-репозиторий. Для этого:

```bash
cd ~/dev/first-project # перешли в нужную папку
git init # создали репозиторий 
```

Далее добавляем файлы в репозиторий и сохранаем их:


```bash
git add --all #Добавляем файлы
git commit -m "Первый коммит" #сохраняем
```

### 4. Связь git и github

Регирстрируемся на [гитхабе](https://github.com)

Создаем первый репозиторий

Мучаемся с ключом

Связываем локальный проект и удаленный репозиторий:


```bash
cd ~/dev/first-project
git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git 
```


Синхронизируем локальный проект и удаленный репозиторий:

```bash
cd ~/dev/first-project
git push -u origin main
```

### 5. Хэш

Хэш - главный идентификатор коммита. Его можно увидеть, если ввести команду:

```bash
git log
```

### 6. Лог

Лог отображает краткую информацию по всем коммитам. А именно:

- Хэш
- данные автора коммита (ник и почта)
- дата создания коммита
- сообщение отображающее краткую инфу об изменениях в документе

### 7. Head

Head - это файл находящий в скрытой папке *.git*. Он содержит указатель на дерикторию хранения хэша последнего коммита

### 8. Статусы файлов

Существует 4 статуса:

- untracked
- staged
- modified
- tracked

Описать их работу можно следующей диаграммой:

```mermaid
graph LR;
  untracked -- "git add" --> staged;
  staged    -- "git commit"     --> tracked;
  tracked   --> modified;
  modified -- "git add" --> staged;

```


