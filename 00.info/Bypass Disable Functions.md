[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)

# Комната [Bypass Disable Functions](https://tryhackme.com/r/room/bypassdisablefunctions) 

Всего 2 задания:
## Задание 1
#### Что такое уязвимость загрузки файлов?

Данная уязвимость возникает в веб-приложениях, где существует вероятность загрузки файла без проверки системой 
безопасности, которая предотвращает потенциальные опасности.  

Он позволяет злоумышленнику загружать файлы с кодом (скрипты, такие как .php, .aspx и другие) и запускать их на том 
же сервере, более подробная информация в этой комнате. 

#### Почему именно эта комната?

Среди обычно применяемых мер — отключение опасных функций, которые могут выполнять команды операционной системы или 
запускать процессы. Такие функции, как system() или shell_exec(), часто отключаются с помощью директив PHP , 
определенных в файле конфигурации php.ini. Другие функции, возможно, менее известные как dl() (которая позволяет 
динамически загружать расширение PHP), могут остаться незамеченными системным администратором и не быть 
отключенными. Обычно при тестировании на вторжение перечисляют, какие функции включены, на случай, если какие-то из 
них были забыты.     

Один из самых простых в реализации и не очень распространенных методов — это злоупотребление функциональными 
возможностями mail() и putenv(). Этот метод не нов, он уже был сообщен PHP в 2008 году gat3way, но он все еще 
работает по сей день. С помощью функции putenv() мы можем изменять переменные окружения, что позволяет нам 
присваивать нужное нам значение переменной LD_PRELOAD. Грубо говоря, LD_PRELOAD позволит нам предварительно 
загрузить библиотеку .so перед остальными библиотеками, так что если программа использует функцию библиотеки 
(например, libc.so), она выполнит функцию в нашей библиотеке вместо той, которую должна. Таким образом, мы можем 
перехватывать или «перехватывать» функции, изменяя их поведение по своему усмотрению.

Chankro: инструмент для обхода disable_functions и open_basedir

С помощью Chankro мы генерируем PHP- скрипт, который будет действовать как дроппер, создавая на сервере библиотеку.
so и двоичный файл (например, meterpreter) или скрипт bash (например, обратная оболочка), которые мы хотим свободно 
выполнять, и который позже будет вызывать putenv() и mail() для запуска процесса.

#### Установить инструмент:

git-клон https://github.com/TarlogicSecurity/Chankro.git
компакт-диск шанкр
python2 chankro.py --help

python chankro.py --arch 64 --input c.sh --output tryhackme.php --path /var/www/html

- --arch = Архитектура системы-жертвы 32 или 64.
- --input = файл с полезной нагрузкой для выполнения
- --output = Имя PHP- файла, который вы собираетесь создать; это файл, который вам нужно будет загрузить.
- --path = Необходимо указать абсолютный путь, где находится наш загруженный PHP- файл. Например, если наш файл 
  находится в папке uploads DOCUMENTROOT + uploads. 



Теперь при выполнении PHP- скрипта на веб-сервере будут созданы необходимые файлы для выполнения нашей полезной нагрузки.


Моя команда успешно выполнилась, и я создал файл в каталоге с выводом команды.

Кредиты .

Вся заслуга принадлежит Tarlogic за сценарий и объяснение метода обхода.
Ответить на вопросы ниже
Прочитайте вышеизложенное.

```commandline
Ответ не нужен
```

## Задание 2
Ответить на вопросы ниже
Взломайте машину и найдите файл flag.txt
```commandline
thm{bypass_d1sable_functions_1n_php}
```


[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)