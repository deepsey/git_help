# git_help

## Коммитим изменения
Команда git status показывает список файлов, у которых прошли изменения:  

    git status
    
Добавить сделанные изменения:  

    git add . -p
    
Сделать коммит  

    git commit -m "<Comment>":
    
Сделать пустой коммит:  

    git commit --allow-empty -m "Пустой коммит"    

Вывести список коммитов:  

    git log
    
#### Удалить файл из Git и закоммитить изменение

Чтобы удалить файл с добавлением изменения в индекс коммита, выполняем команду: 

    git rm <file_name>

Далее:  

    git status

    git commit -m "<Comment>":    
     
#### Сбросить ненужные изменения в файле до добавления в индекс

    git checkout <file_name>
   
Проверим, что изменения отсутсвуют:  

    git status
    
#### Сбросить все ненужные изменения добавления в индекс    

    git checkout .
    
#### Сбросить все ненужные изменения в конкретной папке до добавления в индекс

    git checkout <folder_name>
    
#### Сбросить изменения, которые уже были добавлены в индекс, но ещё не закоммичены

    git reset <file_name>
    git status
    git checkout <file_name>


## Работаем с ветками
#### Создаем ветки

Список веток репозитория:  

    git branch

Создать новую ветку:  

    git branch <branch_name>
    
#### Создать ветку и сделать в ней коммит
Создаем ветку new_branch:  

    git branch new_branch
    
Переходим в ветку new_branch  

    git checkout new_branch
    
Далее изменяем и коммитим уже в новой ветке    
#### Создаём новую ветку командой и сразу же переходим в неё

    git checkout -b <branch_name>

#### Удаляем ветку

    git branch -D <branch_name>

#### Переименование веток

Переходим в ветку <branch_name>  

    git checkout <branch_name>
    
Переименовываем ветку  

    git branch -m <branch_newname>
    
    
