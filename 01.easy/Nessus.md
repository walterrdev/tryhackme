[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)

# Комната [Nessus](https://tryhackme.com/r/room/rpnessusredux) 

Всего 5 заданий:
## Задание 1
Сканер уязвимостей Nessus — это именно то, о чем вы подумали! Сканер уязвимостей!
Он использует методы, похожие на Nmap, для поиска и сообщения об уязвимостях, которые затем представляются в удобном 
графическом интерфейсе для просмотра. 
Nessus отличается от других сканеров тем, что не делает предположений при сканировании,
например, предположим, что веб-приложение работает на порту 80.

Nessus предлагает бесплатный и платный сервис, в котором некоторые функции отсутствуют в бесплатной версии, чтобы 
сделать вас более склонными к покупке платного сервиса.  
Их цена аналогична цене Burp Suite , поэтому, если у вас нет лишних денег, мы будем использовать их бесплатную версию.

Вы можете ознакомиться с их ценовыми вариантами здесь:  https://www.tenable.com/products/nessus

### Ответить на вопросы ниже
Я прочитал описание!
```commandline
Ответ не нужен
```

## Задание 2
Мы установим Nessus на локальную виртуальную машину Kali.

Предупреждение : Не устанавливайте Nessus на THM AttackBox. Он не будет работать, так как там недостаточно места!

Другие ОС в этом пошаговом руководстве рассматриваться не будут, в таком случае официальное руководство по 
установке можно найти ниже.  

 https://docs.tenable.com/nessus/Content/GettingStarted.htm

### Ответить на вопросы ниже
Шаг 1
Перейдите по ссылке  https://www.tenable.com/products/nessus/nessus-essentials и зарегистрируйте учетную запись.

Это вам нужно будет сделать для получения кода активации.
```commandline
Ответ не нужен
```
Шаг 2
Затем мы загрузим файл Nessus-#.##.#-debian6_ amd64.deb
Сохраните его в папке /Загрузки/
```commandline
Ответ не нужен
```
Шаг 3
В терминале перейдем в эту папку и выполним следующую команду:
`sudo dpkg -i  файл_пакета.deb`
Не забудьте заменить  package_file.deb на имя загруженного вами файла.
```commandline
Ответ не нужен
```
Шаг №4
Теперь запустим службу Nessus с помощью команды:
`sudo /bin/systemctl запустить nessusd.service`
```commandline
Ответ не нужен
```
Шаг №5
Откройте Firefox и перейдите по следующему URL-адресу:
https://localhost:8834/ 
Вам может быть выдано предупреждение об угрозе безопасности.
Нажмите «Дополнительно...» -> «Принять риск и продолжить».
```commandline
Ответ не нужен
```
Шаг №6
Далее настроим сканер.
Выберите опцию Nessus Essentials
Нажатие кнопки «Пропустить» перенесет нас на страницу, на которой нам нужно будет ввести код, полученный в 
электронном письме от Nessus.  
```commandline
Ответ не нужен
```
Шаг №7
Заполните поля Имя пользователя и Пароль . Обязательно используйте надежный пароль!
```commandline
Ответ не нужен
```
Шаг №8
Теперь Nessus установит плагины, необходимые для его работы.
Это займет некоторое время, которое будет зависеть от вашего интернет-соединения и оборудования, подключенного к 
вашей виртуальной машине. 
Если полоса прогресса не движется, это означает, что на виртуальной машине недостаточно места для установки.
```commandline
Ответ не нужен
```
Шаг №9
Войдите в систему, используя учетные данные, которые вы создали ранее. 
```commandline
Ответ не нужен
```
Шаг  №10
Вы успешно установили Nessus !
```commandline
Ответ не нужен
```

## Задание 3
Типы навигации и сканирования!﻿

### Ответить на вопросы ниже
Как называется кнопка, которая используется для запуска сканирования?
```commandline
New Scan
```
Какая опция бокового меню позволяет нам создавать пользовательские шаблоны ?
```commandline
Policies
```
Какое меню позволяет нам изменять свойства плагина , например, скрывать их или изменять их серьезность?
```commandline
Plugin Rules
```
Какое сканирование позволяет нам просто увидеть, какие хосты активны, в разделе « Шаблоны сканирования » после 
нажатия кнопки « Новое сканирование »? 
```commandline
Host Discovery
```
Один из самых полезных типов сканирования, который считается « подходящим для любого хоста »?
```commandline
Basic Network Scan
```
Какое сканирование позволяет «Аутентифицироваться на хостах и перечислять отсутствующие обновления »?
```commandline
Credentialed Patch Audit
```
Какой метод сканирования используется специально для сканирования веб-приложений ? 
```commandline
Web Application Tests
```

## Задание 4
Запустите сканирование сети!

### Ответить на вопросы ниже
Создайте новое « Базовое сетевое сканирование », нацеленное на развернутую виртуальную машину. Какую опцию мы можем 
установить в разделе « Базовое » (слева), чтобы задать время для запуска этого сканирования? Это может быть очень 
полезно, когда перегрузка сети является проблемой.  
```commandline
Schedule
```
В разделе « ОБНАРУЖЕНИЕ » (слева) установите «Тип сканирования» для охвата портов 1-65535. Как называется этот тип?
```commandline
Port scan (all ports)
```
Какой « Тип сканирования» можно изменить в разделе «РАСШИРЕННОЕ» для соединения с меньшей пропускной способностью?
```commandline
Scan low bandwidth links
```
Установив эти параметры, запустите сканирование. 
```commandline
Ответ не нужен
```
После завершения сканирования, о какой «Уязвимости» в семействе «Сканеров портов» мы можем просмотреть сведения, 
чтобы увидеть открытые порты на этом хосте? 
```commandline
Nessus SYN scanner
```
Какую версию сервера Apache HTTP сообщает Nessus?
```commandline
2.4.99
```

## Задание 5
Запустите сканирование веб-приложений на виртуальной машине !
(Выполнение этого сканирования займет некоторое время, пожалуйста, проявите терпение)

### Ответить на вопросы ниже
Каков идентификатор плагина, определяющего тип и версию HTTP-сервера?
```commandline
10107
```
Какую страницу аутентификации обнаруживает сканер, передающий учетные данные в открытом виде?
```commandline
login.php
```
Какое расширение имеет файл резервной копии конфигурации?
```commandline
.bak
```
В каком каталоге содержатся примеры документов? (Это будет каталог php)
```commandline
/external/phpids/0.6/docs/examples/
```
Какой уязвимости подвержено это приложение, связанной с X-Frame-Options?
```commandline
Clickjacking
```

[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)