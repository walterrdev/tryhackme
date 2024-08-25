[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)

# Комната [Intro to Docker](https://tryhackme.com/r/room/introtodockerk8pdqk) 

Всего 7 заданий:
## Задание 1
В этой комнате вы получите первый практический опыт развертывания и взаимодействия с контейнерами Docker.

А именно, к концу занятия вы будете знакомы со следующим:
- Базовый синтаксис для начала работы с Docker
- Запуск и развертывание вашего первого контейнера
- Понимание того, как контейнеры Docker распространяются с помощью образов
- Создание собственного образа с помощью Dockerfile
- Как Dockerfiles используются для создания контейнеров, а Docker Compose используется для оркестровки нескольких 
  контейнеров
- Применение полученных в классе знаний на практике в конце.
Обратите внимание: настоятельно рекомендуется, чтобы вы были знакомы хотя бы с базовым синтаксисом Linux (например, 
  с выполнением команд, перемещением файлов и знакомы с тем, как выглядит структура файловой системы). Если вы 
  завершили модуль Linux Fundamentals , то вы будете полностью готовы к этой комнате!  

Кроме того, важно помнить, что вам понадобится подключение к Интернету для извлечения образов Docker. Если вы 
являетесь бесплатным пользователем и хотите попрактиковаться в командах в этой комнате, вам нужно будет сделать это 
в своей собственной среде.  

### Ответьте на вопросы ниже
Завершите этот вопрос, прежде чем перейти к следующему заданию.
```commandline
Ответ не нужен
```

## Задание 2
Поначалу Docker может показаться сложным. Однако команды интуитивно понятны, и с небольшой практикой вы быстро станете мастером Docker.

Синтаксис Docker можно разделить на четыре основные группы:
- Запуск контейнера
- Управление и проверка контейнеров
- Управление образами Docker
- Статистика и информация о демоне Docker
В этом задании мы разберем каждую из этих категорий.

Управление образами Docker

#### Докер Тянет
Прежде чем мы сможем запустить контейнер Docker, нам сначала понадобится образ. Вспомните из комнаты « Введение в 
контейнеризацию », что образы — это инструкции о том, что должен выполнять контейнер. Нет смысла запускать контейнер,
который ничего не делает!  

В этой комнате мы будем использовать образ Nginx для запуска веб-сервера в контейнере. Перед загрузкой образа 
давайте разберем команды и синтаксис, необходимые для загрузки образа. Образы можно загрузить с помощью команды 
docker pullи указав имя образа.  

Например,  docker pull nginxDocker должен знать, где получить этот образ (например, из репозитория, с которым мы 
познакомимся в следующей задаче). 

Продолжая наш пример выше, давайте загрузим этот образ Nginx!

Терминал, показывающий загрузку образа «Nginx»
```commandline
cmnatic@thm:~$ docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
-- omitted for brevity --
Status: Downloaded newer image for nginx:latest
cmnatic@thm:~$

```
Запустив эту команду, мы загружаем последнюю версию образа под названием «nginx». Образы имеют эти метки, называемые 
тегами . Эти теги  используются для обозначения вариаций образа. Например, образ может иметь то же имя, но разные 
теги, указывающие на другую версию. Я привел пример того, как теги используются в таблице ниже:

Образ Докера	Ярлык	Пример команды	Объяснение
убунту	последний	
докер тянуть убунту

- ЭТО ТАК ЖЕ, КАК -

docker pull ubuntu:последняя версия

Эта команда вытащит последнюю версию образа "ubuntu". Если тег не указан, Docker предположит, что вам нужна "последняя" версия, если тег не указан.

Стоит помнить, что вам не всегда нужно "последнее". Это изображение буквально "последнее" в том смысле, что оно будет иметь самые последние изменения. Это может как исправить, так и сломать ваш контейнер.


При указании тега необходимо поставить двоеточие :между именем изображения и тегом, например,  ubuntu:22.04
(image:tag). Не забывайте о тегах — мы вернемся к ним в будущем задании! 

Образ Docker x/y/z
Команда docker imageс соответствующей опцией позволяет нам управлять изображениями в нашей локальной системе. Чтобы 
перечислить доступные опции, мы можем просто сделать, docker imageчтобы увидеть, что мы можем сделать. Я сделал это 
для вас в терминале ниже:  

Терминал, показывающий различные аргументы, которые мы можем предоставить с помощью «docker image»
```commandline
cmnatic@thm:~$ docker image

Usage:  docker image COMMAND

Manage images

Commands:
  build       Build an image from a Dockerfile
  history     Show the history of an image
  import      Import the contents from a tarball to create a filesystem image
  inspect     Display detailed information on one or more images
  load        Load an image from a tar archive or STDIN
  ls          List images
  prune       Remove unused images
  pull        Pull an image or a repository from a registry
  push        Push an image or a repository to a registry
  rm          Remove one or more images
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE

Run 'docker image COMMAND --help' for more information on a command.
cmnatic@thm:~$

```
В этой статье мы рассмотрим только следующие варианты образов Docker:
- тянуть (мы это уже делали выше!)
- ls (список изображений)
- rm (удалить изображение)
построить (мы рассмотрим это в задании «Создание вашего первого контейнера »)
#### Docker-образ ls
Эта команда позволяет нам вывести список всех изображений, хранящихся в локальной системе. Мы можем использовать эту 
команду, чтобы проверить, было ли изображение загружено правильно, и просмотреть немного больше информации о нем 
(такой как тег, когда изображение было создано и размер изображения).  

Терминал, в котором перечислены образы Docker, хранящиеся в операционной системе хоста.
```commandline
cmnatic@thm:~$ docker image ls
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
ubuntu       22.04     2dc39ba059dc   10 days ago   77.8MB
nginx        latest    2b7d6430f78d   2 weeks ago   142MB
cmnatic@thm:~$
```

Например, в терминале выше мы можем увидеть некоторую информацию о двух изображениях в системе:

#### Docker-образ rm
Если мы хотим удалить образ из системы, мы можем использовать docker image rm вместе с именем (или идентификатором 
образа). В следующем примере я удалю образ " ubuntu " с тегом " 22.04 ". Моя команда будет такой docker image rm 
ubuntu:22.04:  

Важно не забыть указать тег вместе с названием изображения.

Терминал, отображающий снятие тегов с изображения

```commandline
cmnatic@thm:~$ docker image rm ubuntu:22.04
Untagged: ubuntu:22.04
Untagged: ubuntu@sha256:20fa2d7bb4de7723f542be5923b06c4d704370f0390e4ae9e1c833c8785644c1
Deleted: sha256:2dc39ba059dcd42ade30aae30147b5692777ba9ff0779a62ad93a74de02e3e1f
Deleted: sha256:7f5cbd8cc787c8d628630756bcc7240e6c96b876c2882e6fc980a8b60cdfa274
cmnatic@thm:~$
```
Если бы мы запустили docker image ls, то увидели бы, что изображение больше не отображается:

Терминал, подтверждающий, что наш образ Docker был удален
```commandline
cmnatic@thm:~$ docker image ls
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
nginx        latest    2b7d6430f78d   2 weeks ago   142MB
cmnatic@thm:~$

```
### Ответьте на вопросы ниже
Если бы нам нужен был pull образ Docker, как бы выглядела наша команда?
```commandline
docker pull
```
Если бы мы хотели получить список всех образов на устройстве, на котором запущен Docker,  как бы выглядела наша команда?
```commandline
docker image ls
```
Допустим, мы хотим извлечь изображение «tryhackme» (без кавычек). Как будет выглядеть наша команда?
```commandline
docker pull tryhackme
```
Допустим, мы хотим вытащить изображение "tryhackme" с тегом "1337" (без кавычек). Как будет выглядеть наша команда?
```commandline
docker pull tryhackme:1337
```

## Задание 3
Команда Docker run создает работающие контейнеры из образов. Здесь запускаются команды из Dockerfile (а также наш 
собственный ввод во время выполнения). Из-за этого это должен быть один из первых синтаксисов, которые вы изучаете.  

Команда работает следующим образом: docker run [OPTIONS] IMAGE_NAME [COMMAND] [ARGUMENTS...]  параметры, заключенные 
в скобки, не являются обязательными для запуска контейнера. 

Контейнеры Docker могут быть запущены с различными параметрами - в зависимости от того, как мы будем использовать 
контейнер. Эта задача объяснит некоторые из наиболее распространенных параметров, которые вы можете захотеть 
использовать.  

#### Сначала просто запустите контейнер

Давайте вспомним синтаксис, необходимый для запуска контейнера Docker:  docker run [OPTIONS] IMAGE_NAME [COMMAND] 
[ARGUMENTS...]В этом примере я собираюсь настроить  контейнер для запуска: 

Изображение с названием "helloworld"
«Интерактивно», указав `-it` переключатель в команде [OPTIONS]. Это позволит нам напрямую взаимодействовать с контейнером.
Я собираюсь создать оболочку внутри контейнера, указав `/bin/bash` часть [COMMAND]. Этот аргумент — то место, где вы 
будете размещать команды, которые хотите запустить внутри контейнера (например, файл, приложение или оболочка!)
Итак, для достижения вышеизложенного моя команда будет выглядеть следующим образом: `docker run -it helloworld /bin/bash`

Терминал, показывающий запуск контейнера в «интерактивном» режиме
```commandline
cmnatic@thm-intro-to-docker:~$ docker run -it helloworld /bin/bash
root@30eff5ed7492:/#
```
Мы можем убедиться, что успешно запустили оболочку, поскольку наше приглашение изменится на другую учетную запись 
пользователя и имя хоста. Имя хоста контейнера — это идентификатор контейнера (который можно найти с помощью docker 
ps). Например, в терминале выше наше имя пользователя и имя хоста — это root@30eff5ed7492  

Запуск контейнеров...Продолжение

Как уже упоминалось, контейнеры Docker можно запускать с различными параметрами. Назначение контейнера и инструкции, 
заданные в Dockerfile (мы рассмотрим это в более поздней задаче), определяют, с какими параметрами нам нужно 
запустить контейнер. Для начала я поместил в таблицу ниже некоторые из наиболее распространенных параметров, которые 
могут вам понадобиться для запуска контейнера Docker.   

[ВАРИАНТ]	Объяснение	Соответствующая инструкция Dockerfile	Пример
- -d	Этот аргумент сообщает контейнеру, что нужно запуститься в "отсоединенном" режиме. Это означает, что контейнер 
будет работать в фоновом режиме.	Н/Д	`docker run -d helloworld`

- -it	Этот аргумент состоит из двух частей. «i» означает запуск в интерактивном режиме, а «t» говорит Docker 
запустить оболочку внутри контейнера. Мы бы использовали эту опцию, если бы хотели напрямую взаимодействовать с 
контейнером после его запуска.	Н/Д	  `docker run -it helloworld`

- -v	Этот аргумент является сокращением от "Volume" и сообщает Docker, что нужно смонтировать каталог или файл из 
операционной системы хоста в определенное место в контейнере. Место, где будут храниться эти файлы, определяется в 
  Dockerfile	ОБЪЕМ  `docker run -v /host/os/directory:/container/directory helloworld`

- -p	Этот аргумент сообщает Docker о необходимости привязать порт на хостовой операционной системе к порту, который 
предоставляется в контейнере. Эту инструкцию следует использовать, если вы запускаете приложение или службу 
  (например, веб-сервер) в контейнере и хотите получить доступ к приложению/службе, перейдя по IP-адресу.	
  РАЗОБЛАЧАТЬ	 `docker run -p 80:80 webserver`

- --rm	Этот аргумент сообщает Docker о необходимости удалить контейнер после того, как контейнер завершит выполнение 
порученных ему действий.	Н/Д	`docker run --rm helloworld`

- --name	Этот аргумент позволяет нам дать контейнеру дружелюбное, запоминающееся имя. Когда контейнер запускается 
  без этой опции, имя состоит из двух случайных слов. Мы можем использовать это открытие, чтобы назвать контейнер в 
  честь приложения, которое он запускает.	 Н/Д `docker run --name helloworld`

Это лишь некоторые аргументы, которые мы можем предоставить при запуске контейнера. Опять же, большинство аргументов,
которые нам нужно запустить, будут определяться тем, как построен контейнер. Однако такие аргументы, как  --rm и , 
--name будут указывать Docker, как запускать контейнер. Другие аргументы включают (но не ограничиваются!):  

Указываем Docker, какой сетевой адаптер должен использовать контейнер
К каким возможностям должен иметь доступ контейнер. Это рассматривается в комнате " Docker Rodeo " на TryHackMe.
Сохранение значения в переменной среды
Если вы хотите подробнее изучить эти аргументы, я настоятельно рекомендую вам прочитать документацию по запуску Docker .

Список запущенных контейнеров

Чтобы получить список запущенных контейнеров, мы можем использовать команду docker ps. Эта команда выведет список 
запущенных в данный момент контейнеров — например, так: 

Терминал, отображающий список работающих контейнеров и их информацию
```commandline
cmnatic@thm:~/intro-to-docker$ docker ps
CONTAINER ID   IMAGE                           COMMAND        CREATED        STATUS      PORTS     NAMES                                                                                      
                             
a913a8f6e30f   cmnatic/helloworld:latest   "sleep"   1 months ago   Up 3 days   0.0.0.0:8000->8000/tcp   helloworld
cmnatic@thm:~/intro-to-docker$
```

Эта команда также покажет информацию о контейнере, включая:
- Идентификатор контейнера
- Какую команду выполняет контейнер?
- Когда был создан контейнер
- Как долго контейнер работает?
- Какие порты сопоставлены
- Название контейнера
Совет: чтобы вывести список всех контейнеров (даже остановленных), можно использовать `docker ps -a`:

Терминал, отображающий список ВСЕХ контейнеров и их информацию
```commandline
cmnatic@thm:~/intro-to-docker$ docker ps -a
CONTAINER ID   IMAGE                             COMMAND                  CREATED             STATUS     PORTS    NAMES                                                                                  
00ba1eed0826   gobuster:cmnatic                  "./gobuster dir -url…"   an hour ago   Exited an hour ago practical_khayyam
```
### Ответьте на вопросы ниже
Как бы выглядела наша команда, если бы мы хотели запустить контейнер в интерактивном режиме ?

Примечание : Предположим, что мы не указываем здесь никакого изображения.
```commandline
docker run -it
```

Как бы выглядела наша команда, если бы мы хотели запустить контейнер в « отсоединенном » режиме?
Примечание : Предположим, что мы не указываем здесь никакого изображения.
```commandline
docker run -d
```

Допустим, мы хотим запустить контейнер, который будет работать и привязывать веб-сервер к порту 80. Как будет 
выглядеть наша команда? 

Примечание : Предположим, что мы не указываем здесь никакого изображения.
```commandline
docker run -p 80:80
```
Как нам составить список всех запущенных контейнеров?
```commandline
docker ps
```
Как теперь составить список всех контейнеров (включая остановленные)?
```commandline
docker ps -a
```

## Задание 4
Dockerfiles играет важную роль в Docker. Dockerfiles — это форматированный текстовый файл, который по сути служит 
инструкцией о том, что должны делать контейнеры, и в конечном итоге собирает образ Docker. 

Dockerfiles используются для хранения команд, которые контейнер должен выполнить при сборке. Чтобы начать работу с 
Dockerfiles, нам нужно знать базовый синтаксис и инструкции. Dockerfiles форматируются следующим образом: 

#### INSTRUCTION argument

Сначала давайте рассмотрим некоторые основные инструкции:

Теперь, когда мы понимаем основные инструкции, составляющие Dockerfile, давайте посмотрим на рабочий пример 
Dockerfile. Но сначала я объясню, что я хочу, чтобы делал контейнер: 

В качестве основы используйте операционную систему «Ubuntu» (версия 22.04).
Установите рабочий каталог как корень контейнера.
Создайте текстовый файл «helloworld.txt».
```commandline
# THIS IS A COMMENT
# Use Ubuntu 22.04 as the base operating system of the container
FROM ubuntu:22.04

# Set the working directory to the root of the container
WORKDIR / 

# Create helloworld.txt
RUN touch helloworld.txt

```
Помните, команды, которые вы можете запустить с помощью RUN инструкции, будут зависеть от операционной системы, 
которую вы используете в FROM инструкции. (В этом примере я выбрал Ubuntu. Важно помнить, что операционные системы, 
используемые в контейнерах, обычно очень минималистичны. То есть не ожидайте, что команда будет там с самого начала 
(даже такие команды, как curl , ping и т. д., могут потребовать установки.)   

Создание вашего первого контейнера

После того, как у нас есть Dockerfile, мы можем создать образ с помощью docker buildкоманды. Эта команда требует 
несколько фрагментов информации: 
- Хотите ли вы сами дать изображению имя (мы будем использовать -tаргумент (тег)).
- Имя, которое вы собираетесь дать изображению.
- Расположение Dockerfile, с помощью которого вы хотите выполнить сборку.
- Я предоставлю сценарий, а затем объясню соответствующую команду. Допустим, мы хотим создать изображение — давайте 
  заполним два обязательных фрагмента информации, перечисленных выше:
Мы собираемся назвать его сами, поэтому мы будем использовать этот -t аргумент.
Мы хотим дать изображению имя.
Dockerfile находится в нашем текущем рабочем каталоге ( .).
Dockerfile, который мы собираемся создать, выглядит следующим образом:
```commandline
# Use Ubuntu 22.04 as the base operating system of the container
FROM ubuntu:22.04

# Set the working directory to the root of the container
WORKDIR / 

# Create helloworld.txt
RUN touch helloworld.txt
```
Команда будет выглядеть так: docker build -t helloworld . (мы используем точку, чтобы указать Docker искать в нашем 
рабочем каталоге). Если мы правильно заполнили команду, мы увидим, как Docker начнет создавать образ: 

Терминал, показывающий процесс создания изображения «helloworld»
```commandline
cmnatic@thm:~$ docker build -t helloworld .
Sending build context to Docker daemon  4.778MB
Step 1/3 : FROM ubuntu:22.04
22.04: Pulling from library/ubuntu
2b55860d4c66: Pull complete
Digest: sha256:20fa2d7bb4de7723f542be5923b06c4d704370f0390e4ae9e1c833c8785644c1
Status: Downloaded newer image for ubuntu:22.04
 ---> 2dc39ba059dc
Step 2/3 : WORKDIR /
 ---> Running in 64d497097f8a
Removing intermediate container 64d497097f8a
 ---> d6bd1253fd4e
Step 3/3 : RUN touch helloworld.txt
 ---> Running in 54e94c9774be
Removing intermediate container 54e94c9774be
 ---> 4b11fc80fdd5
Successfully built 4b11fc80fdd5
Successfully tagged helloworld:latest
cmnatic@thm:~$
```
Отлично! Похоже, это успех. Давайте используем, docker image ls чтобы увидеть, было ли создано это изображение:

Использование команды «docker image ls» для подтверждения того, что наш образ был успешно собран
```commandline
cmnatic@thm:~$ docker image ls
REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
helloworld   latest    4b11fc80fdd5   2 minutes ago   77.8MB
ubuntu       22.04     2dc39ba059dc   10 days ago     77.8MB
cmnatic@thm:~$
```
Примечание: Любая базовая операционная система, которую вы перечислите в FROM инструкции в Dockerfile, также будет 
загружена. Вот почему мы видим два изображения:
helloworld (наш образ).
Ubuntu (базовая операционная система, используемая в нашем образе).
Теперь вы сможете использовать это изображение в контейнере. Обратитесь к задаче «Запуск вашего первого контейнера »,
чтобы напомнить вам, как запустить контейнер. 

Повышение уровня нашего Dockerfile

Давайте поднимем уровень нашего Dockerfile. Пока что наш контейнер создаст только файл — это не очень полезно! В следующем Dockerfile я собираюсь:
Используйте Ubuntu 22.04 в качестве базовой операционной системы для контейнера.
Установите веб-сервер «apache2».
Добавьте немного сети. Поскольку это веб-сервер, нам нужно будет как-то подключиться к контейнеру по сети. Я добьюсь этого, используя инструкцию EXPOSEи указав контейнеру открыть порт 80 .
Сообщите контейнеру, чтобы он запускал службу «apache2» при запуске. Контейнеры не имеют менеджеров служб, таких как systemd(это сделано намеренно — запускать несколько приложений в одном контейнере — плохая практика. Например, этот контейнер предназначен для веб-сервера apache2 — и только для веб-сервера apache2).
```commandline
# THIS IS A COMMENT
FROM ubuntu:22.04

# Update the APT repository to ensure we get the latest version of apache2
RUN apt-get update -y 

# Install apache2
RUN apt-get install apache2 -y

# Tell the container to expose port 80 to allow us to connect to the web server
EXPOSE 80 

# Tell the container to run the apache2 service
CMD ["apache2ctl", "-D","FOREGROUND"]

```
Для справки, команда для сборки этого будет такой docker build -t webserver .(предполагая, что Dockerfile находится 
в том же каталоге, откуда вы запускаете команду). После запуска контейнера с соответствующими параметрами ( docker 
run -d --name webserver -p 80:80  webserver), мы можем перейти на IP-адрес нашей локальной машины в нашем браузере!  

Целевая страница apache2 по умолчанию, которую можно использовать для подтверждения того, что служба запущена

Веб-сервер работает! В настоящее время Apache2 обслуживает файлы по умолчанию, поскольку мы не добавили свои 
собственные в контейнер. 

Оптимизация нашего Dockerfile

Docker — это, конечно, искусство, и оно не ограничивается Dockerfiles! Во-первых, нам нужно спросить себя, почему 
так важно оптимизировать Dockerfile? Раздутые Dockerfiles трудно читать и поддерживать, и они часто занимают много 
ненужного места! Например, вы можете уменьшить размер образа Docker (и сократить время сборки!) несколькими 
способами:   
- Устанавливаем только необходимые пакеты. Что хорошо в контейнерах, так это то, что они практически пусты с самого 
  начала — у нас есть полная свобода решать, что мы хотим. 
- Удаление кэшированных файлов (например, кэш APT или документация, установленная с инструментами). Код внутри 
  контейнера будет выполнен только один раз (при сборке!), поэтому нам не нужно ничего хранить для последующего использования.
- Использование минимальных базовых операционных систем в нашей FROM инструкции. Несмотря на то, что операционные 
  системы для контейнеров, такие как Ubuntu, уже довольно тонкие, рассмотрите возможность использования еще более 
  урезанной версии (например, ubuntu:22.04-minimal). Или, например, использование Alpine (которая может быть всего 5,
  59 МБ!).  


Минимизация количества слоев — я объясню это подробнее ниже.
Каждая инструкция (IE FROM, RUN, и т.д.) выполняется в своем собственном слое. Слои увеличивают время сборки! Цель 
состоит в том, чтобы иметь как можно меньше слоев. Например, попробуйте объединить команды из  RUNвместе следующим 
образом:  

До:
```commandline
FROM ubuntu:latest
RUN apt-get update -y
RUN apt-get upgrade -y
RUN apt-get install apache2 -y
RUN apt-get install net-tools -y

```
Терминал, на котором показано создание пяти слоев Dockerfile
```commandline
cmnatic@thm:~$ docker build -t before .
--omitted for brevity--
Step 2/5 : RUN apt-get update -y
 ---> Using cache
 ---> 446962612d20
Step 3/5 : RUN apt-get upgrade -y
 ---> Running in 8bed81c695f4
--omitted for brevity--
cmnatic@thm:~$
```
После:

```commandline
FROM ubuntu:latest
RUN apt-get update -y && apt-get upgrade -y && apt-get install apache2 -y && apt-get install net-tools
Терминал, показывающий два слоя Dockerfile, которые собираются
cmnatic@thm:~$ docker build -t after .
Sending build context to Docker daemon   4.78MB
Step 1/2 : FROM ubuntu
 ---> 2dc39ba059dc
Step 2/2 : RUN apt-get update -y && apt-get upgrade -y && apt-get install apache2 -y && apt-get install net-tools
 ---> Running in a4d4943bcf04
--omitted for brevity--
cmnatic@thm:~$
```
Иллюстрация, показывающая, что команды были сжаты в два слоя.

Обратите внимание, что теперь есть только два шага сборки (это будет два слоя, что значительно ускорит сборку). Это 
всего лишь небольшой пример Dockerfile, поэтому время сборки не будет столь значительным, но в гораздо больших 
Dockerfile сокращение количества слоев даст фантастический прирост производительности во время сборки.  

### Ответьте на вопросы ниже
Какую инструкцию нам следует использовать, чтобы указать, какой базовый образ должен использовать контейнер?
```commandline
FROM
```
Какую инструкцию мы бы использовали, чтобы сообщить контейнеру о необходимости выполнить команду?
```commandline
RUN
```
Какую команду Docker нам следует использовать для создания образа с использованием Dockerfile?
```commandline
build
```
Допустим, мы хотим дать имя этому изображению. Какой аргумент мы будем использовать?
```commandline
-t
```

## Задание 5
Давайте сначала разберемся, что такое Docker Compose и почему его стоит понимать. До сих пор мы взаимодействовали 
только с контейнерами по отдельности. Docker Compose, вкратце, позволяет нескольким контейнерам (или приложениям) 
взаимодействовать друг с другом при необходимости, работая при этом изолированно друг от друга.  

Вы, возможно, уже заметили проблему с Docker. Чаще всего приложениям требуются дополнительные сервисы для запуска, 
чего мы не можем сделать в одном контейнере. Например, современные — динамические — веб-сайты используют такие 
сервисы, как базы данных и веб-сервер. Ради этой задачи мы будем рассматривать каждое приложение как «микросервис».  

Хотя мы можем развернуть несколько контейнеров или «микросервисов» по отдельности и подключить их, делать это по 
одному — обременительно и неэффективно. Docker Compose позволяет нам создавать эти «микросервисы» как одну отдельную 
«службу».   

На этой иллюстрации показано, как контейнеры развертываются вместе с использованием Docker Compose и Docker:

Синий прямоугольник (представляющий компьютер) с надписью docker изолирован от другого набора синих прямоугольников 
(представляющих компьютер).

Прежде чем демонстрировать Docker Compose, давайте рассмотрим основы использования Docker Compose.
- Нам нужно установить Docker Compose (он не идет с Docker по умолчанию). Его установка выходит за рамки этой комнаты,
так как она меняется в зависимости от вашей операционной системы и других факторов. Вы можете ознакомиться с документацией по установке здесь .
- Нам нужен действительный файл docker-compose.yml — мы скоро к этому вернемся.
- Фундаментальное понимание использования Docker Compose для создания и управления контейнерами.


Я собрал некоторые основные команды Docker Compose в таблице ниже:
- up -	Эта команда (повторно)создаст/построит и запустит контейнеры, указанные в файле Compose. `docker-compose up`

- start -	Эта команда запустит (но для этого требуются уже созданные контейнеры) контейнеры, указанные в файле 
  Compose. `docker-compose start`

- down -	Эта команда остановит и удалит  контейнеры, указанные в файле Compose. `docker-compose down`

- stop -	Эта команда остановит ( а не удалит) контейнеры, указанные в файле Compose. `docker-compose stop`

- build -	Эта команда создаст (но не запустит) контейнеры, указанные в файле Compose. `docker-compose build`

Примечание : Это всего лишь несколько возможных команд. Ознакомьтесь с документацией по созданию сообщений для всех 
возможных опций. 

#### Демонстрация Docker Compose

С учетом сказанного, давайте посмотрим, как мы можем использовать Docker Compose самостоятельно. В этом сценарии я 
предполагаю следующие требования: 
- Сайт электронной коммерции, работающий на Apache
- Этот сайт электронной коммерции хранит информацию о клиентах в базе данных MySQL.

Теперь мы можем вручную запустить два контейнера следующим образом:
- Создание сети между двумя контейнерами: `docker network create ecommerce`
- Запуск контейнера веб-сервера Apache2: `docker run -p 80:80 --name webserver --net ecommerce webserver`
- Запуск сервера базы данных MySQL: `docker run --name database --net ecommerce webserver`
Иллюстрация, показывающая два контейнера, развернутых с помощью docker compose. Обратите внимание, что они не могут 
  общаться друг с другом 

На иллюстрации показаны два контейнера, работающих независимо друг от друга и не имеющих возможности 
взаимодействовать друг с другом. 

…но хотим ли мы делать это каждый раз? Или что, если мы решим масштабироваться и задействовать много веб-серверов? 
Хотим ли мы делать это для каждого контейнера, каждый раз? Я определенно не хочу. 

Вместо этого мы можем использовать Docker Compose docker-compose up для совместного запуска этих контейнеров, что 
дает нам следующие преимущества: 
- Одна простая команда для запуска обоих
- Эти два контейнера объединены в сеть, поэтому нам не нужно заниматься настройкой сети.
- Чрезвычайно портативный. Мы можем поделиться нашим файлом docker-compose.yml с кем-то еще, и они смогут настроить 
  работу точно так же, не понимая, как работают контейнеры по отдельности.
- Легко поддерживать и изменять. Нам не нужно беспокоиться о конкретных контейнерах, использующих (возможно, 
  устаревшие) образы.


Иллюстрация, показывающая два контейнера, развернутых как объединенная служба. Эти два контейнера могут общаться 
друг с другом. 

Файлы Docker-compose.yml 101

Один файл, чтобы управлять ими всеми. Форматирование файла docker-compose.yml отличается от форматирования 
Dockerfile. Важно отметить, что YAML требует отступов (хорошая практика — два пробела, которые должны быть 
согласованы!). Сначала я покажу некоторые новые инструкции, которые вам нужно будет изучить, чтобы иметь возможность 
написать файл docker-compose.yml, прежде чем мы приступим к созданию файла docker-compose.yml :   

С учетом сказанного, давайте рассмотрим наш первый файл docker-compose.yml. Этот файл docker-compose.yml предполагает следующее:
- Мы запустим один веб-сервер (с именем web) из ранее упомянутого сценария.
- Мы запустим сервер базы данных (назовем его базой данных) из ранее упомянутого сценария.
- Веб-сервер будет создан с использованием Dockerfile, но для сервера базы данных (MySQL) мы будем использовать уже 
  созданный образ.
- Контейнеры будут объединены в сеть для взаимодействия друг с другом (сеть называется электронной коммерцией).

Список наших каталогов выглядит следующим образом:
- docker-compose.yml
- веб/Dockerfile

Вот как будет выглядеть наш файл docker-compose.yml (напоминаем, что важно обращать внимание на отступы):

```commandline
version: '3.3'
services:
  web:
    build: ./web
    networks:
      - ecommerce
    ports:
      - '80:80'


  database:
    image: mysql:latest
    networks:
      - ecommerce
    environment:
      - MYSQL_DATABASE=ecommerce
      - MYSQL_USERNAME=root
      - MYSQL_ROOT_PASSWORD=helloword
    
networks:
  ecommerce:
```
### Ответьте на вопросы ниже
Я хочу использовать docker-compose для запуска серии контейнеров. Какой аргумент позволяет мне это сделать?
```commandline
up
```
Я хочу использовать docker-compose для удаления серии контейнеров. Какой аргумент позволяет мне это сделать?
```commandline
down
```
Как называется файл .yml, который docker-compose используется?
Примечание: для этого вопроса вам необходимо будет включить расширение файла .yml в свой ответ.
```commandline
docker-compose.yml
```

## Задание 6
Эта задача объяснит, как Docker взаимодействует между операционной системой и контейнером. Когда вы устанавливаете 
Docker, устанавливаются две программы: 
- Клиент Docker
- Докер-сервер


Docker работает в модели клиент/сервер. В частности, эти две программы взаимодействуют друг с другом, образуя Docker,
  который мы знаем и любим. Docker осуществляет эту связь с помощью так называемого сокета. Сокеты являются 
  неотъемлемой функцией операционной системы, которая позволяет передавать данные.   

Например, при использовании программы чата может быть два сокета:
- Сокет для хранения отправляемого вами сообщения.
- Сокет для хранения сообщения, которое вам кто-то отправляет.

Программа будет взаимодействовать с этими двумя сокетами для сохранения или извлечения данных из них! Сокет может 
быть либо сетевым соединением, либо тем, что представлено в виде файла. Важно знать о сокетах, что они допускают 
межпроцессное взаимодействие ( IPC ). Это просто означает, что процессы в операционной системе могут 
взаимодействовать друг с другом!   

В контексте Docker, Docker Server фактически является просто API . Docker Server использует этот API для 
прослушивания запросов, тогда как Docker Client использует API для отправки  запросов.  

Например, давайте возьмем эту команду: docker run helloworld. Docker Client запросит Docker-сервер запустить 
контейнер, используя образ "helloworld". Итак, хотя это объяснение довольно простое, оно является основной 
предпосылкой того, как работает Docker.  

Давайте рассмотрим следующую диаграмму, чтобы продемонстрировать этот процесс в действии:

иллюстрирующий поток взаимодействия Docker с использованием файла docker.sock в операционной системе

Интересно, что благодаря этому мы можем взаимодействовать с Docker Server с помощью таких команд, как curlили 
API-инструмент разработчика, например Postman. Использование этого выходит за рамки этой комнаты, но я 
продемонстрирую взаимодействие с Docker Server с помощью Postman для получения списка всех образов, которые хранятся 
в операционной системе:   

список образов Docker в операционной системе, полученный с помощью postman

Наконец, важно отметить, что из-за этого хост-машина, на которой запущен Docker, может быть настроена на обработку 
команд, отправленных с другого устройства. Это чрезвычайно опасная уязвимость, если она настроена неправильно, 
поскольку это означает, что кто-то может удаленно останавливать, запускать и получать доступ к контейнерам Docker. 
Несмотря на это, существуют случаи использования, когда эта функция Docker чрезвычайно полезна! Мы рассмотрим это 
более подробно в следующей комнате!    

### Ответьте на вопросы ниже
Что означает термин «МПК»?

```commandline
Interprocess Communication
```
С какой технологией можно сравнить Docker Server?
```commandline
API
```

## Задание 7
Разверните виртуальную машину, прикрепленную к этой задаче, нажав зеленую кнопку « Запустить машину ». После полной 
загрузки виртуальная машина появится в разделенном виде в вашем веб-браузере. Если вы не видите виртуальную машину,
нажмите синюю кнопку « Показать разделенный вид», расположенную в правом верхнем углу этой страницы.  

### Ответьте на вопросы ниже
Подключитесь к машине. Как называется контейнер, который сейчас запущен?
```commandline
CloudIsland
```
Используйте Docker для запуска веб-сервера с образом "webserver" (без кавычек). Вам нужно будет запустить контейнер 
с портом 80. 

После запуска контейнера попробуйте подключиться к https://LAB_WEB_URL.p.thmlabs.com/  в вашем браузере. Что такое флаг?
```commandline
THM{WEBSERVER_CONTAINER}
```
[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)