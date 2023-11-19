# git_help
## Содержание
[01. Удаленный репозиторий](#001) 
- [Привязать к локальному репозиторию удаленный](#0011)
- [Клонировать репозиторий](#0012)
  
[02. Коммитим изменения](#002) 
- [Создать коммит](#0021)
- [Удалить файл из Git и закоммитить изменение](#0022)
- [Сбросить ненужные изменения в файле до добавления в индекс](#0023)
- [Сбросить все ненужные изменения до добавления в индекс](#0024)
- [Сбросить все ненужные изменения в конкретной папке до добавления в индекс](#0025)
- [Сбросить изменения, которые уже были добавлены в индекс, но ещё не закоммичены](#0026)

---  
##  <a name='001'>01. Удаленный репозиторий</a> 
####  <a name='0011'>Привязать к локальному репозиторию удаленный</a> 

Для того, чтобы «привязать» к своему git-хранилищу другое, служит команда remote add:
```
git remote add произвольное-имя url-хранилища
```
Для первого (и часто единственного) из «привязанных» хранилищ обычно принято давать имя `origin`
```
git remote add origin url-хранилища
```
Чтобы просмотреть список имён уже привязанных хранилищ, служит команда remote show:
```
git remote show
```
чтобы посмотреть информацию о хранилище, служит та же команда, но с указанием имени:
```
$ git remote show -n имя
```
Опция -n служит для того, чтобы не устанавливать при выполнении команды связь с самим хранилищем, а использовать только локально кэшированную информацию.
  
#### <a name='0012'>Клонировать репозиторий</a>
```
git clone <Repository URL> -b <branch name>
```

---

## <a name='002'>02. Коммитим изменения</a>
#### <a name='0021'>Создать коммит</a>
Команда `git status` показывает список файлов, у которых прошли изменения:  
```
git status
```
    
Добавить сделанные изменения в индекс:  
```
git add . -p
```
, где `-p` - патч, ключ, позволяющий увидеть изменения в интерактивном формате    

Создать коммит-запись  
```
git commit -m "<Comment>":
```
    
Сделать пустой коммит:  

    git commit --allow-empty -m "Пустой коммит"    

Вывести список коммитов:  

    git log
    
#### <a name='0022'>Удалить файл из Git и закоммитить изменение</a>

Чтобы удалить файл с добавлением изменения в индекс коммита, выполняем команду: 

    git rm <file_name>

Далее:  

    git status

    git commit -m "<Comment>":    
     
#### <a name='0023'>Сбросить ненужные изменения в файле до добавления в индекс</a>

Вы сделали ненужные изменения, которые не будете коммитить, и требуется от них избавиться, вернув файлы в состояние, в котором они были до изменений.
```
git checkout <file_name>
```
   
Проверим, что изменения отсутствуют:  

    git status
    
#### <a name='0024'>Сбросить все ненужные изменения до добавления в индекс</a>    

    git checkout .
    
#### <a name='0025'>Сбросить все ненужные изменения в конкретной папке до добавления в индекс</a>

    git checkout <folder_name>
    
#### <a name='0026'>Сбросить изменения, которые уже были добавлены в индекс, но ещё не закоммичены</a>

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

`git checkout master ; git add . ; git commit`  
`git checkout develop ; git add . ; git commit`  
`git checkout master ; git push`  
`git checkout develop ; git push`  
    
#### Добавление дополнительного удалённого репозитория по https

Скопируем команду добавления репозитория со страницы удаленного репозитория, и заменим в ней "origin" на нужное нам.  
Т.е. будет нечто вроде этого:  

`git remote add` ~~origin~~ `second https://gitlab.com/deepsey/learning_git.git`

#### Удаление связи с удалённым репозиторием
Вы можете увидеть в локальном репозитории связи с удалёнными репозиториями. Это можно проверить командой  
`git remote`  

    gitlab-learning   
    origin

Давайте с вами удалим связь с удалённым репозиторием gitlab-learning
Выполняем команду

`git remote remove gitlab-learning`

Как вы можете понимать из команды: remote означает, что мы сейчас будем работать со связями с удалённым репозиторием, remove означает, что мы удаляем запись связи с удалённым репозиторием.  

Теперь вводим снова команду  

`git remote`  

Она нам покажет только одну связь origin.

Для полноценного теста давайте попробуем сделать push в наш уже несуществующий удалённым репозиторий

`git push gitlab-learning`

    fatal: 'gitlab-learning' does not appear to be a git repository
    fatal: Could not read from remote repository.

    Please make sure you have the correct access rights
    and the repository exists.

#### Создание новой ветки и пуш новой ветки

Давайте сделаем новую ветку в локальном репозитории и запушим её в удалённый репозиторий.
Создаём ветку new_branch командой

`git branch new_branch`

Переходим в новую ветку  

`git checkout new_branch`

Выполняем команду  

`git push`

Система отвечает нам, что нет upstream ветки, которая организует связь между веткой в локальной ветке и ветки в удалённом репозитории.  
Копируем команду, которую предложил нам Git и выполняем  

`git push --set-upstream origin new_branch`

    info: detecting host provider for 'https://gitlab.com/'...
    info: detecting host provider for 'https://gitlab.com/'...
    Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
    remote:
    remote: To create a merge request for new_branch, visit:
    remote:   https://gitlab.com/deepsey/slurm_clone/-/merge_requests/new?merge_request%5Bsource_branch%5D=new_branch
    remote:
    To https://gitlab.com/deepsey/slurm_clone.git
     * [new branch]      new_branch -> new_branch
    Branch 'new_branch' set up to track remote branch 'new_branch' from 'origin'.  

Открываем страницу нашего репозитория на Gitlab и обновляем страницу.  
Смотрим на список веток, которые нам предлагаются. Там появилась наша новая ветка new_branch.  
Новая ветка будет создана на основе текущей ветки.

#### Создание и пуш тэгов

Давайте сделаем новый тэг в локальном репозитории и запушим его в удалённый репозиторий.
Создаём тэг командой

`git tag -a 0.1 -m "my first tag"`

Как вы можете видеть из этой команды: -a - это флаг говорит о том, что мы создаём tag, -m - это комментарий к тэгу.  

Теперь вводим команду

`git tag `

И видим наш созданный тэг.  

Давайте отправим в удалённым репозиторий наш созданный тэг. Выполняем команду  

`git push --tags`

Где флаг --tags говорит о том, что мы отправляем сейчас именно тэги.
    
#### Обыкновенный пулл текущей ветки
Изменим какой-нибудь файл в ветке main в удаленном репозитории.
А теперь давайте заберём эти изменения. В локальном репозитории переходим в ветку main 

`git checkout main`

и выполняем обыкновенную команду

`git pull`

Система покажет нам, что были загружены изменения из удалённого репозитория.

#### Забираем новую ветку. Использование команды git fetch

Создадим в удаленном репозитории две новые ветки - fetch_01 и ftech_02.  
Нам нужно забрать новую ветку fetch_01 из удалённого репозитория.  

Обновим список веток удаленного репозитория

`git fetch --prune`

Выведем список веток удаленного (remote) репозитория с использованием ключа -r  

`git branch -r`

Забираем ветку fetch_01. Для этого выполняем команду  

`git fetch origin fetch_01`

Попробуем перейти на эту ветку  

`git checkout fetch_01`

Проверяем список веток в локальном репозитории  

`git branch`  

И видим ветку fetch_01.

#### Забираем новую ветку с присвоением нового имени

Нам нужно забрать новую ветку fetch_02 из удалённого репозитория и присвоить ей новое имя в нашем локальном репозитории.  
Выполняем команду

`git fetch origin fetch_02:MyNewFetch`

После этого проверяем список веток в локальном репозитории  

`git branch`

И видим ветку MyNewFetch.


## Сложные кейсы слияния веток
#### Обыкновенное слияние веток
Создадим ветку main3 из ветки main и перейдем в нее

`git checkout main ; git branch main3 ; git checkout main3`  

Создадим в main3 новый файл file_new и добавим его в индекс git и закоммитим изменения

`git add file_new ; git commit -m "07. Added file_new in main3 branch"`

Добавим нашу новую ветку в удаленный репозиторий

`git push --set-upstream origin main3`

Проверяем коммиты в ветках main и main3

`git checkout main ; git log`  
`git checkout main3 ; git log`

Видим, что логи отличаются на один коммит "07. Added file_new in main3 branch"
Проведём простое слияние веток (merge). А если быть точным мерджим ветку main3 в ветку main. Переходим в ветку main

`git checkout main`

Выполняем команду 

`git merge main3`

Система ответила, что merge прошёл.
Давайте теперь проверим, какие коммиты есть в ветке main. Выполняем команду

`git log`

Обнаруживаем в ней "07. Added file_new in main3 branch", который пришёл сюда из ветки main3.  
Пушим ветку в удаленный репозиторий

`git push`

#### Решение конфликтов с изменениями одних и тех же строк в одних и тех же файлах





