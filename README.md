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
    
#### Переход по коммитам ветки    

Переход на один коммит назад  

    git checkout HEAD^
    
Переход на два коммита назад  

    git checkout HEAD^^
    
Возвращаемся на последний коммит ветки  

    git checkout <branch_name>  
    
#### Создаem ветку из определённого коммита    
Перейдем в ветке на один коммит назад

    git checkout HEAD^
    
Создаём новую ветку командой  

    git branch <new_branch_name>
    
Переходим во вновь созданную ветку <new_branch_name>  

    git checkout <new_branch_name>
    
В этой ветке последнего коммита ветки <branch_name> не будет    

    git checkout HEAD^


## Обмен изменениями с удалёнными репозиториями

#### Обыкновенный push в origin
Делаем коммит в ветке в локальном репозитории. Затем отправляем изменения в ветке в удаленный репозиторий  

    git push origin

#### Отправка изменений всех веток в удалённый репозиторий
Для этого переходим в ветки, где были сделаны коммиты изменения, и пушим каждую из них, например

`git checkout master + git add . + git commit`
`git checkout develop + git add . + git commit`
`git checkout master + git push`
`git checkout develop + git push`




    
#### Добавление дополнительного удалённого репозитория по ssh

Скопируем команду добавления репозитория со страницы удаленного репозитория, и заменим в ней "origin" на нужное нам.  
Т.е. будет нечто вроде этого:  

`git remote add` ~~origin~~ `second https://gitlab.com/deepsey/learning_git.git`

    
    
    

