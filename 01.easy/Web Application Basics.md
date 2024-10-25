[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)

# Комната [Web Application Basics](https://tryhackme.com/r/room/webapplicationbasics) 

Всего 11 заданий:
## Задание 1
Введение
Добро пожаловать на курс Web Application Basics! В этой комнате мы рассмотрим ключевые элементы веб-приложения, такие как URL-адреса, HTTP-запросы и ответы. Это идеально, если вы только начинаете и хотите разобраться с основами или хотите создавать веб-приложения или работать с ними.

Цели обучения
Завершив эту комнату, вы:

Понять, что такое веб-приложение и как оно работает в веб-браузере.
Разберите компоненты URL-адреса и посмотрите, как он помогает получать доступ к веб-ресурсам.
Узнайте, как работают HTTP- запросы и ответы.
Ознакомьтесь с различными типами методов HTTP- запросов.
Поймите, что означают различные коды ответов HTTP .
Узнайте, как работают заголовки HTTP и почему они важны для безопасности.
### Ответьте на вопросы ниже
Я готов изучать веб-приложения!
```commandline
Ответ не нужен
```

## Задание 2
Рассмотрим аналогию веб-приложения с планетой. Астронавты путешествуют на планету, чтобы исследовать ее поверхность, подобно тому, как кто-то использует веб-браузер для исследования или просмотра веб-приложения. Хотя мы видим только поверхность планеты, многое происходит под поверхностью. Вы можете представить себе всю планету как веб-сервер со многими вещами, происходящими под поверхностью веб-сервера, но все, что мы обычно видим, это поверхность веб-страниц или приложений. Теперь мы рассмотрим различные компоненты, из которых состоит веб-приложение.

Внешний интерфейс
Front End  можно рассматривать как аналог поверхности планеты, частей, которые астронавт может видеть и с которыми может взаимодействовать на основе законов природы. Веб-приложение будет иметь пользователя, взаимодействующего с ним, и использовать для этого ряд технологий, таких как HTML, CSS и JavaScript.

Иллюстрация планеты, символизирующей веб-страницу HTML: серая, голая и неподвижная, без CSS для дизайна и JavaScript для движения.
HTML (язык гипертекстовой разметки) — это основополагающий аспект веб-приложений. Это набор инструкций или код, который инструктирует веб-браузер о том, что отображать и как это отображать. Его можно сравнить с простыми организмами, живущими на планете; эти организмы имеют ДНК, которая является инструкциями о том, как простые организмы собираются вместе.


Иллюстрация яркой планеты, представляющая HTML-страницу, стилизованную с помощью CSS. Планета красочная и детализированная, демонстрирующая свою красоту через элементы дизайна, такие как текстуры, узоры и яркие цвета, символизирующие визуальные улучшения, предоставляемые CSS.
CSS  (каскадные таблицы стилей) в веб-приложениях описывают стандартный внешний вид, такой как определенные цвета, типы текста и макеты. Продолжая аналогию с ДНК, их можно сравнить с частями ДНК, которые описывают цвет, форму, размер и текстуру простого организма.


Иллюстрация планеты, символизирующей веб-страницу HTML: серая, голая и неподвижная, без CSS для дизайна и JavaScript для движения.
JS  (JavaScript) — это часть интерфейса веб-приложения, которая обеспечивает более сложную активность в веб-браузере. В то время как HTML можно считать простым набором инструкций о том, что отображать, JavaScript — это более продвинутый набор инструкций, который позволяет делать выбор и принимать решения о том, что отображать. В аналогии с планетой JavaScript можно считать мозгом развитого организма, который позволяет принимать решения на основе того, что и как с ним взаимодействует.



Бэк-Энд
Back End веб-приложения — это то, что вы не видите в веб-браузере, но что важно для работы веб-приложения. На планете это невизуальные вещи: структуры, которые удерживают здание, воздух и гравитация, которая удерживает ноги на земле.


Иллюстрация экосистемы планеты, представляющей базы данных. Поверхность планеты богата разнообразными ландшафтами, лесами, реками и ресурсами, символизирующими огромное хранилище данных. Эта процветающая экосистема подчеркивает, как базы данных хранят и предоставляют доступ к различным типам ресурсов, необходимых для функциональности планеты (веб-сайта).
База данных — это место, где информация может храниться, изменяться и извлекаться. Веб-приложение может захотеть хранить и извлекать информацию о предпочтениях посетителя относительно того, что показывать, а что нет; это будет храниться в базе данных. Планета может иметь более продвинутых обитателей, которые хранят информацию о местоположении на картах, пишут заметки в дневнике или кладут книги в библиотеку, а файлы в картотечный шкаф.


Иллюстрация инфраструктуры планеты, символизирующей веб-серверы, сети и системы, поддерживающие веб-приложение, в основе которого лежат взаимосвязанные сети и серверы.
Существует множество других компонентов инфраструктуры, лежащих в основе веб-приложений, таких как веб-серверы, серверы приложений, хранилища, различные сетевые устройства и другое программное обеспечение, поддерживающее веб-приложение. На планете это дороги, которые существуют, автомобили, которые ездят по этим дорогам, топливо, которое питает автомобили.


Иллюстрация озонового слоя планеты, представляющая собой брандмауэр веб-приложений (WAF). Защитный слой окружает планету, символизируя меры безопасности, которые защищают веб-приложение от внешних атак и угроз, обеспечивая его безопасность и целостность.
WAF  (Web Application Firewall) — это дополнительный компонент для веб-приложений. Он помогает отфильтровывать опасные запросы от веб-сервера и обеспечивает элемент защиты. Это можно сравнить с тем, как атмосфера планеты может защищать жителей от вредных ультрафиолетовых лучей.




Краткое содержание
В доставку веб-приложения вовлечено множество компонентов. Компоненты Front End, такие как HTML, CSS и JavaScript, фокусируются на опыте внутри браузера. Компоненты Back End, такие как веб-сервер, база данных или WAF, являются движком под поверхностью, который позволяет веб-приложению функционировать. Это простое введение будет дополняться в следующих задачах.

### Ответьте на вопросы ниже
Какой компонент компьютера отвечает за размещение и доставку контента для веб-приложений?
```commandline
web server
```
Какой инструмент используется для доступа к веб-приложениям и взаимодействия с ними?
```commandline
web browser
```
Какой компонент действует как защитный слой, фильтруя входящий трафик для блокировки вредоносных атак и обеспечивая безопасность веб-приложения?
```commandline
web application firewall
```

## Задание 3
Единый указатель ресурсов
Единый указатель ресурсов (URL) — это веб-адрес, который позволяет вам получать доступ ко всем видам онлайн-контента — будь то веб-страница, видео, фотография или другие медиа. Он направляет ваш браузер в нужное место в Интернете.

Анатомия URL-адреса
Иллюстрация, изображающая различные части URL, включая протокол, доменное имя, путь, параметры запроса и фрагмент. Каждый компонент помечен и визуально отличается, демонстрируя, как они работают вместе, образуя полный веб-адрес.

Думайте об URL как о чем-то, состоящем из нескольких частей, каждая из которых играет свою роль в поиске нужного ресурса. Понимание того, как эти части сочетаются друг с другом, важно для просмотра веб-страниц, разработки веб-приложений и даже устранения неполадок.

Вот разбивка ключевых компонентов:

Схема

Схема — это протокол, используемый для доступа к веб-сайту. Наиболее распространенными являются HTTP ( HyperText Transfer Protocol) и HTTPS (Hypertext Transfer Protocol Secure). HTTPS более безопасен, поскольку шифрует соединение, поэтому браузеры и эксперты по кибербезопасности рекомендуют его. Веб-сайты часто применяют HTTPS для дополнительной защиты.

Пользователь

Некоторые URL-адреса могут включать данные для входа пользователя (обычно имя пользователя) для сайтов, требующих аутентификации. Это происходит в основном в URL-адресах, которым требуются учетные данные для доступа к определенным ресурсам. Однако в настоящее время это встречается редко, поскольку размещение данных для входа в URL-адрес не очень безопасно — это может раскрыть конфиденциальную информацию, что представляет угрозу безопасности.

Хост/Домен

Хост или домен — самая важная часть URL, поскольку он сообщает вам, к какому веб-сайту вы обращаетесь. Каждое доменное имя должно быть уникальным и зарегистрировано через регистраторов доменов. С точки зрения безопасности ищите доменные имена, которые выглядят почти как настоящие, но имеют небольшие отличия (это называется тайпсквоттинг ). Такие поддельные домены часто используются в фишинговых атаках, чтобы обманом заставить людей предоставить конфиденциальную информацию.

Порт

Номер порта помогает направить ваш браузер к нужной службе на веб-сервере. Это как сказать серверу, какой дорвей использовать для связи. Номера портов варьируются от 1 до 65 535, но наиболее распространенными являются 80 для HTTP и 443 для HTTPS.

Путь

Путь указывает на конкретный файл или страницу на сервере, к которому вы пытаетесь получить доступ. Это как дорожная карта, которая показывает браузеру, куда идти. Веб-сайтам необходимо защищать эти пути, чтобы гарантировать, что только авторизованные пользователи могут получить доступ к конфиденциальным ресурсам.

Строка запроса

Строка запроса — это часть URL, которая начинается с вопросительного знака (?). Она часто используется для таких вещей, как поисковые термины или вводимые данные форм. Поскольку пользователи могут изменять эти строки запроса, важно обрабатывать их безопасно, чтобы предотвратить атаки, такие как инъекции , когда может быть добавлен вредоносный код.

Фрагмент

Фрагмент начинается с символа решетки (#) и помогает указать на определенный раздел веб-страницы — например, перейти непосредственно к определенному заголовку или таблице. Пользователи также могут изменять это, поэтому, как и в случае со строками запросов, важно проверить и очистить все данные здесь, чтобы избежать проблем, таких как атаки с инъекциями.

### Ответьте на вопросы ниже
Какой протокол обеспечивает зашифрованную связь для обеспечения безопасной передачи данных между веб-браузером и веб-сервером?


```commandline
HTTPS
```
Какой термин описывает практику регистрации доменных имен, которые представляют собой неправильно написанные варианты названий популярных веб-сайтов, с целью эксплуатации ошибок пользователей и потенциального участия в мошеннической деятельности?


```commandline
Typosquatting
```
Какая часть URL-адреса используется для передачи дополнительной информации, например поисковых запросов или данных формы, на веб-сервер?


```commandline
Query String
```

## Задание 4
HTTP-сообщения — это пакеты данных, которыми обмениваются пользователь (клиент) и веб-сервер. Эти сообщения очень важны для понимания того, как работают веб-приложения, поскольку они показывают, как передаются запросы пользователей и ответы сервера.

Представьте себе пример HTTP- запроса и HTTP- ответа, где вы можете увидеть ключевые части, такие как метод, URL, заголовки и коды состояния. Это то, что делает возможным взаимодействие клиент-сервер.

Существует два типа HTTP- сообщений:

HTTP- запросы : отправляются пользователем для запуска действий в веб-приложении.
HTTP- ответы : отправляются сервером в ответ на запрос пользователя.
Иллюстрация, показывающая запрос POST на вход и ответ об успешном входе.

Каждое сообщение имеет определенный формат, который помогает пользователю и серверу беспрепятственно общаться.

Стартовая линия

Стартовая строка — это как бы введение сообщения. Она сообщает, какой тип сообщения отправляется — запрос пользователя или ответ сервера. Эта строка также дает важные сведения о том, как следует обрабатывать сообщение.

Заголовки

Заголовки состоят из пар ключ-значение, которые предоставляют дополнительную информацию о сообщении HTTP . Они дают инструкции как клиенту, так и серверу, обрабатывающему запрос или ответ. Эти заголовки охватывают всевозможные вещи, такие как безопасность, типы контента и многое другое, гарантируя, что все пройдет гладко в коммуникации.

Пустая строка

Пустая строка — это небольшой разделитель, который отделяет заголовок от тела. Это важно, поскольку показывает, где заканчиваются заголовки и начинается фактическое содержимое сообщения. Без этой пустой строки сообщение может испортиться, и клиент или сервер могут неправильно его интерпретировать, что приведет к ошибкам.

Тело

Тело — это место, где хранятся фактические данные. В запросе тело может включать данные, которые пользователь хочет отправить на сервер (например, данные формы). В ответе это место, куда сервер помещает запрошенный пользователем контент (например, веб-страницу или данные API ).

Почему важно понимать HTTP- сообщения
Эти сообщения являются основой того, как общаются веб-приложения. Если они правильно структурированы, все работает гладко.
Знание того, как они работают, поможет вам диагностировать проблемы в веб-коммуникациях, что означает лучшую производительность и надежность вашего веб-приложения.
Это также важно для безопасности. Понимание HTTP- сообщений поможет вам реализовать надежные меры безопасности для защиты данных во время передачи.
### Ответьте на вопросы ниже
Какое HTTP-сообщение возвращает веб-сервер после обработки запроса клиента?
```commandline
HTTP response
```
Что следует за заголовками в HTTP-сообщении?
```commandline
Empty Line
```

## Задание 5
HTTP - запрос — это то, что пользователь отправляет на веб-сервер для взаимодействия с веб-приложением и выполнения чего-либо. Поскольку эти запросы часто являются первой точкой контакта между пользователем и веб-сервером, знание того, как они работают, крайне важно, особенно если вы занимаетесь кибербезопасностью.

Иллюстрация, показывающая запрос GET и все используемые заголовки.

Представьте себе HTTP- запрос, показывающий ключевые части, такие как метод (например, GET или POST), путь (например, /login) и версия (например, HTTP /1.1). Эти элементы составляют основы того, как клиент (пользователь) общается с сервером.

Запрос линии
Строка запроса (или стартовая строка) — это первая часть HTTP- запроса, которая сообщает серверу, с каким типом запроса он имеет дело. Она состоит из трех основных частей: HTTP- метод , URL-путь и HTTP- версия .

Пример: METHOD /path HTTP/version

HTTP- методы
Метод HTTP сообщает серверу , какое действие пользователь хочет выполнить на ресурсе, идентифицированном путем URL. Вот некоторые из наиболее распространенных методов и их возможные проблемы безопасности:

GET
Используется для извлечения данных с сервера без внесения каких-либо изменений. Напоминание! Убедитесь, что вы предоставляете только те данные, которые разрешено видеть пользователю. Избегайте помещения конфиденциальной информации, такой как токены или пароли, в запросы GET, поскольку они могут отображаться как открытый текст.

POST
Отправляет данные на сервер, обычно для создания или обновления чего-либо. Напоминание! Всегда проверяйте и очищайте входные данные, чтобы избежать атак типа SQL-инъекции или XSS .

PUT
Заменяет или обновляет что-либо на сервере. Напоминание! Убедитесь, что пользователь имеет право вносить изменения, прежде чем принимать запрос.

DELETE
Удаляет что-либо с сервера. Напоминание! Как и в случае с PUT, убедитесь, что только авторизованные пользователи могут удалять ресурсы.

Помимо этих распространенных методов, есть еще несколько, используемых в особых случаях:

PATCH
Обновляет часть ресурса. Это полезно для внесения небольших изменений без замены всего, но всегда проверяйте данные, чтобы избежать несоответствий.

HEAD
Работает как GET, но извлекает только заголовки, а не полное содержимое. Удобно для проверки метаданных без загрузки полного ответа.

ОПЦИИ
Сообщает, какие методы доступны для определенного ресурса, помогая клиентам понять, что они могут делать с сервером.

TRACE
Подобно OPTIONS, он показывает, какие методы разрешены, часто для отладки. Многие серверы отключают его по соображениям безопасности.

CONNECT
Используется для создания защищенного соединения, например, для HTTPS. Это не так распространено, но имеет решающее значение для зашифрованной связи.

Каждый из этих методов имеет свой собственный набор правил безопасности. Например, запросы PATCH должны быть проверены, чтобы избежать несоответствий, а OPTIONS и TRACE должны быть отключены, если они не нужны, чтобы избежать возможных рисков безопасности.

URL-путь
Путь URL сообщает серверу, где найти ресурс, который запрашивает пользователь. Например, в URL https://tryhackme.com/api/users/123путь /api/users/123идентифицирует конкретного пользователя.

Злоумышленники часто пытаются манипулировать URL-путем, чтобы воспользоваться уязвимостями, поэтому крайне важно:

Проверьте URL-путь, чтобы предотвратить несанкционированный доступ.
Продезинфицируйте путь, чтобы избежать инъекционных атак
Защитите конфиденциальные данные, проведя оценку конфиденциальности и рисков
Соблюдение этих правил поможет защитить ваше веб-приложение от распространенных атак.

HTTP- версия
Версия HTTP показывает версию протокола  ,  используемую для связи между клиентом и сервером. Вот краткий обзор наиболее распространенных:

HTTP /0.9 (1991)
Первая версия поддерживала только запросы GET.

HTTP /1.0 (1996)
Добавлены заголовки и улучшена поддержка различных типов контента, улучшено кэширование.

HTTP /1.1 (1997)
Принес постоянные соединения, кодирование передачи фрагментов и улучшенное кэширование. Он широко используется и сегодня.

HTTP /2 (2015)
Внедрены такие функции, как мультиплексирование, сжатие заголовков и приоритизация для повышения производительности.

HTTP /3 (2022)
Создан на основе HTTP /2, но использует новый протокол (QUIC) для более быстрых и безопасных соединений.

Хотя HTTP /2 и HTTP /3 предлагают лучшую скорость и безопасность, многие системы по-прежнему используют HTTP /1.1 , поскольку он хорошо поддерживается и работает с большинством существующих настроек. Однако обновление до HTTP /2 или HTTP /3 может обеспечить значительные улучшения производительности и безопасности, поскольку все больше систем принимают их.

### Ответьте на вопросы ниже
Какая версия  протокола HTTP  получила широкое распространение и остается наиболее часто используемой версией для веб-коммуникаций, известной такими функциями, как постоянные соединения и кодирование фрагментированной передачи?


```commandline
HTTP/1.1
```
Какой метод HTTP-запроса описывает параметры связи для целевого ресурса, позволяя клиентам определять, какие HTTP-методы поддерживаются веб-сервером?


```commandline
OPTIONS
```
Какой компонент в HTTP-запросе указывает конкретный ресурс или конечную точку на веб-сервере, запрашиваемую клиентом, обычно появляясь после доменного имени в URL-адресе?


```commandline
URL Path
```

## Задание 6
Заголовки запроса
Заголовки запроса позволяют передавать дополнительную информацию о запросе на веб-сервер. Некоторые общие заголовки следующие:

Общие заголовки запросов

Заголовок запроса	Пример	Описание
Хозяин	
Host: tryhackme.com

Указывает имя веб-сервера, к которому относится запрос.
Пользователь-агент	
User-Agent: Mozilla/5.0

Предоставляет информацию о веб-браузере, с которого поступил запрос.
Реферер	
Referer: https://www.google.com/

Указывает URL, с которого пришел запрос.
Печенье	
Cookie: user_type=student; room=introtowebapplication; room_status=in_progress

Информация, которую веб-сервер ранее запросил у веб-браузера, хранится в файлах cookie.
Тип контента	
Content-Type: application/json

Описывает тип или формат данных в запросе.


Текст запроса
В HTTP- запросах, таких как POST и PUT, где данные отправляются на веб-сервер, а не запрашиваются с веб-сервера, данные находятся внутри тела HTTP- запроса. Форматирование данных может принимать различные формы, но некоторые общие из них —  URL Encoded, Form Data, JSON, или XML.

URL Encoded (application/x-www-form-urlencoded)
Формат, в котором данные структурированы в пары ключ-значение, где ( key=value). Несколько пар разделяются символом ( &), например  key1=value1&key2=value2. Специальные символы кодируются процентами.

Пример
```commandline
POST /profile HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0
Content-Type: application/x-www-form-urlencoded
Content-Length: 33

name=Aleksandra&age=27&country=US
```
Форма данных (multipart/form-data)
Позволяет отправлять несколько блоков данных, где каждый блок отделен граничной строкой. Граничная строка — это определенный заголовок самого запроса. Этот тип форматирования может использоваться для отправки двоичных данных, например, при загрузке файлов или изображений на веб-сервер.

Пример
```commandline
POST /upload HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW

----WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="username"

aleksandra
----WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="profile_pic"; filename="aleksandra.jpg"
Content-Type: image/jpeg

[Binary Data Here representing the image]
----WebKitFormBoundary7MA4YWxkTrZu0gW--
JSON (application/json)
```
В этом формате данные могут быть отправлены с использованием структуры JSON (JavaScript Object Notation). Данные форматируются в парах имя : значение. Несколько пар разделяются запятыми, все заключены в фигурные скобки { }.

Пример
```commandline
POST /api/user HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0
Content-Type: application/json
Content-Length: 62

{
    "name": "Aleksandra",
    "age": 27,
    "country": "US"
}
XML (application/xml)
```
В  XML-  форматировании данные структурируются внутри меток, называемых тегами, которые имеют открытие и закрытие. Эти метки могут быть вложены друг в друга. В примере ниже вы можете увидеть открытие и закрытие тегов для отправки данных о пользователе по имени Александра.

Пример
```commandline
POST /api/user HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0
Content-Type: application/xml
Content-Length: 124

<user>
    <name>Aleksandra</name>
    <age>27</age>
    <country>US</country>
</user>
```
### Ответьте на вопросы ниже
Какой заголовок HTTP-запроса определяет доменное имя веб-сервера, на который отправляется запрос?


```commandline
Host
```
Какой тип содержимого используется по умолчанию для отправки форм в HTTP-запросе, где данные кодируются как пары 
ключ=значение в формате строки запроса? 


```commandline
application/x-www-form-urlencoded
```
Какая часть HTTP-запроса содержит дополнительную информацию, такую как хост, пользовательский агент и тип контента, 
определяющую, как веб-сервер должен обрабатывать запрос? 


```commandline
Request Headers
```

## Задание 7
Когда вы взаимодействуете с веб-приложением, сервер отправляет ответ HTTP , чтобы сообщить вам, был ли ваш запрос успешным или что-то пошло не так. Эти ответы включают код статуса и краткое объяснение (называемое Reason Phrase ), которое дает представление о том, как сервер обработал ваш запрос.

Строка статуса
Первая строка в каждом HTTP- ответе называется Status Line . Она предоставляет вам три ключевых фрагмента информации:

Версия HTTP : здесь указывается, какая версия HTTP используется.
Код статуса : трехзначное число, показывающее результат вашего запроса.
Фраза причины : короткое сообщение, поясняющее код состояния в понятных человеку терминах.
Поскольку мы уже рассмотрели версии HTTP в задании 5, давайте сосредоточимся на кодах состояния и фразах причин .

Коды состояния и фразы причин
Код статуса — это число, которое сообщает вам, был ли запрос успешным или нет, в то время как фраза причины объясняет, что произошло. Эти коды делятся на пять основных категорий:

Информационные ответы (100-199)
Эти коды означают, что сервер получил часть запроса и ждет остальную часть. Это сигнал «продолжайте».

Успешные ответы (200-299)
Эти коды означают, что все прошло как ожидалось. Сервер обработал запрос и отправил обратно запрошенные данные.

Сообщения о перенаправлении (300-399)
Эти коды сообщают вам, что запрошенный вами ресурс перемещен в другое место, обычно предоставляя новый URL-адрес.

Ответы об ошибках клиента (400-499)
Эти коды указывают на проблему с запросом. Возможно, URL неверен или у вас отсутствует какая-то необходимая информация, например, аутентификация.

Ответы об ошибках сервера (500-599)
Эти коды означают, что сервер столкнулся с ошибкой при попытке выполнить запрос. Обычно это проблемы на стороне сервера, а не вина клиента.

Общие коды статуса
Вот некоторые из наиболее часто встречающихся кодов статуса:

100 (Продолжить)
Сервер получил первую часть запроса и готов к остальной части.

200 (OK)
Запрос выполнен успешно, и сервер отправляет обратно запрошенный ресурс.

301 (Перемещен навсегда)
Запрашиваемый вами ресурс был перемещен навсегда на новый URL. С этого момента используйте новый URL.

404 (Не найдено)
Сервер не смог найти ресурс по указанному URL. Дважды проверьте, что вы указали правильный адрес.

500 (внутренняя ошибка сервера)
На стороне сервера произошла ошибка, и он не смог обработать ваш запрос.

### Ответьте на вопросы ниже
Какая часть HTTP-ответа содержит версию HTTP, код состояния и краткое объяснение результата ответа?


```commandline
Status Line
```
Какая категория кодов ответов HTTP указывает на то, что веб-сервер столкнулся с внутренней проблемой или не может выполнить запрос клиента?


```commandline
Server Error Responses
```
Какой код статуса HTTP указывает на то, что запрошенный ресурс не найден на веб-сервере?


```commandline
404
```

## Задание 8
Заголовки ответа
Когда веб-сервер отвечает на HTTP- запрос, он включает заголовки HTTP- ответа , которые в основном являются парами ключ-значение. Эти заголовки предоставляют важную информацию об ответе и сообщают клиенту (обычно браузеру), как его обрабатывать.

Представьте пример HTTP- ответа с выделенными заголовками. Ключевые заголовки, такие как Content-Type, Content-Length, и Dateдают нам важные сведения об ответе, который сервер отправляет обратно.

Изображение HTTP-ответа с выделением заголовков. Ключевые заголовки, такие как Content-Type, Content-Length и Date, выделены, иллюстрируя их роль в предоставлении важной информации об ответе сервера на запрос клиента.

Требуемые заголовки ответа
Некоторые заголовки ответа имеют решающее значение для обеспечения корректной работы HTTP- ответа. Они предоставляют важную информацию, которая нужна как клиенту, так и серверу для корректной обработки всего. Вот несколько важных:

Дата :
Пример: Date: Fri, 23 Aug 2024 10:43:21 GMT
этот заголовок показывает точную дату и время, когда сервер сгенерировал ответ.

Content-Type :
Пример: Content-Type: text/html; charset=utf-8
Он сообщает клиенту, какой тип контента он получает, например, HTML, JSON или что-то еще. Он также включает набор символов (например, UTF-8), чтобы помочь браузеру правильно его отобразить.

Server :
Пример: Server: nginx
Этот заголовок показывает, какое серверное программное обеспечение обрабатывает запрос. Он хорош для отладки, но также может раскрыть информацию о сервере, которая может быть полезна для злоумышленников, поэтому многие люди удаляют или скрывают его.

Другие распространенные заголовки ответов
Помимо основных, существуют и другие общие заголовки, которые предоставляют дополнительные инструкции клиенту или браузеру и помогают контролировать обработку ответа.

Set-Cookie :
Пример: Set-Cookie: sessionId=38af1337es7a8
Этот отправляет файлы cookie с сервера клиенту, которые клиент затем сохраняет и отправляет обратно с будущими запросами. Чтобы обеспечить безопасность, убедитесь, что файлы cookie установлены с флагом HttpOnly(чтобы к ним не мог получить доступ JavaScript) и Secureфлагом (чтобы они отправлялись только по HTTPS).

Cache-Control :
Пример: Cache-Control: max-age=600
Этот заголовок сообщает клиенту, как долго он может кэшировать ответ перед повторной проверкой на сервере. Он также может предотвратить кэширование конфиденциальной информации, если это необходимо (используя no-cache).

Местоположение :
Пример: Location: /index.html
Этот используется в ответах перенаправления (3xx). Он сообщает клиенту, куда идти дальше, если ресурс был перемещен. Если пользователи могут изменять этот заголовок во время запросов, будьте осторожны, проверяйте и очищайте его — в противном случае вы можете получить открытые уязвимости перенаправления, когда злоумышленники могут перенаправлять пользователей на вредоносные сайты.

Тело ответа
Тело ответа HTTP — это место, где находятся фактические данные — такие как HTML, JSON , изображения и т. д., которые сервер отправляет обратно клиенту. Чтобы предотвратить атаки с внедрением, такие как межсайтовый скриптинг ( XSS ), всегда очищайте и экранируйте любые данные (особенно пользовательский контент) перед включением их в ответ.

### Ответьте на вопросы ниже
Какой заголовок HTTP-ответа может раскрыть информацию о программном обеспечении и версии веб-сервера, потенциально подвергая его риску безопасности, если его не удалить?
```commandline
Server
```
Какой флаг следует добавить к файлам cookie в заголовке ответа HTTP Set-Cookie, чтобы гарантировать, что они передаются только по протоколу HTTPS, защищая их от раскрытия во время незашифрованных передач?
```commandline
Secure
```
Какой флаг следует добавить к файлам cookie в заголовке ответа HTTP Set-Cookie, чтобы предотвратить доступ к ним через JavaScript, тем самым повысив безопасность от атак XSS?
```commandline
HttpOnly
```

## Задание 9
Заголовки безопасности
Заголовки безопасности HTTP помогают повысить общую безопасность веб-приложения, обеспечивая смягчение таких атак, как межсайтовый скриптинг ( XSS ), кликджекинг и другие. Теперь мы более подробно рассмотрим следующие заголовки безопасности:

Политика безопасности контента ( CSP )
Строгая транспортная безопасность (HSTS)
X-Content-Type-Options
Реферер-Политика
Вы можете использовать сайт, например https://securityheaders.io/, для анализа заголовков безопасности любого веб-сайта. После обсуждения этой задачи вы, как мы надеемся, лучше поймете, о чем он сообщает.

Политика безопасности контента ( CSP )
Заголовок CSP — это дополнительный уровень безопасности, который может помочь смягчить такие распространенные атаки, как межсайтовый скриптинг ( XSS ). Вредоносный код может быть размещен на отдельном веб-сайте или домене и внедрен в уязвимый веб-сайт. CSP предоставляет администраторам возможность указать, какие домены или источники считаются безопасными, и обеспечивает уровень смягчения таких атак.

В самом заголовке вы можете увидеть такие свойства, как default-srcили script-srcdefined и многие другие. Каждое из них дает администратору возможность определять на разных уровнях детализации, какие домены разрешены для какого типа контента. Использование self является специальным ключевым словом, которое отражает тот же домен, на котором размещен веб-сайт.

Рассмотрим пример заголовка CSP :

Content-Security-Policy: default-src 'self'; script-src 'self' https://cdn.tryhackme.com; style-src 'self'

Мы видим использование:

default-src
— определяет политику по умолчанию self, что означает только текущий веб-сайт.

script-src
— определяет политику, из которой могут быть загружены скрипты, включая себя и скрипты, размещенные наhttps://cdn.tryhackme.com

style-src
— определяет политику, в которой таблицы стилей CSS могут быть загружены с текущего веб-сайта (self)

Строгая транспортная безопасность (HSTS)
Заголовок HSTS гарантирует, что веб-браузеры всегда будут подключаться по HTTPS. Давайте рассмотрим пример HSTS:

Strict-Transport-Security: max-age=63072000; includeSubDomains; preload

Вот разбивка примера заголовка HSTS по директивам:

max-age
— это время истечения срока действия этого параметра в секундах.

includeSubDomains
— необязательный параметр, который указывает браузеру применять этот параметр ко всем поддоменам.

preload
- Эта необязательная настройка позволяет включить веб-сайт в списки предварительной загрузки. Браузеры могут использовать списки предварительной загрузки для принудительного применения HSTS еще до первого посещения веб-сайта.
X-Content-Type-Options
Заголовок X-Content-Type-Options может использоваться для указания браузерам не угадывать MIME- время ресурса, а использовать только заголовок Content-Type. Вот пример:

X-Content-Type-Options: nosniff

Вот разбивка заголовка X-Content-Type-Options по директивам:

nosniff
— эта директива предписывает браузеру не анализировать и не угадывать тип MIME .
Реферер-Политика
Этот заголовок контролирует объем информации, отправляемой на целевой веб-сервер, когда пользователь перенаправляется с исходного веб-сервера, например, когда он нажимает гиперссылку. Заголовок доступен для того, чтобы позволить веб-администратору контролировать, какая информация передается. Вот несколько примеров Referrer-Policy:

Referrer-Policy: no-referrer
Referrer-Policy: same-origin
Referrer-Policy: strict-origin
Referrer-Policy: strict-origin-when-cross-origin
Вот разбивка заголовка Referrer-Policy по директивам:

no-referrer
— полностью отключает отправку любой информации о реферере.

same-origin
- Эта политика будет отправлять информацию о реферере только тогда, когда пункт назначения является частью того же источника. Это полезно, когда вы хотите, чтобы информация о реферере передавалась, когда гиперссылки находятся в пределах одного и того же веб-сайта, но не за его пределами на внешних веб-сайтах.

strict-origin
- Эта политика отправляет реферер как источник только тогда, когда протокол остается прежним. Таким образом, реферер отправляется, когда соединение HTTPS переходит в другое соединение HTTPS.

strict-origin-when-cross-origin
— аналогично strict-origin, за исключением запросов на один и тот же источник, когда в заголовке источника отправляется полный путь URL.
### Ответьте на вопросы ниже
Какое свойство можно задать в конфигурации политики безопасности контента (CSP), чтобы определить, откуда можно загружать скрипты?
```commandline
script-src
```
Какую директиву следует включить при настройке заголовка Strict-Transport-Security (HSTS) для обеспечения использования HTTPS всеми поддоменами сайта, чтобы применить политику безопасности как к основному домену, так и к его поддоменам?
```commandline
includeSubDomains
```
Какая директива заголовка HTTP используется для предотвращения интерпретации браузерами файлов как файлов с типом MIME, отличным от указанного сервером, тем самым предотвращая атаки с перехватом типа контента?
```commandline
nosniff
```

## Задание 10
Нажмите кнопку «Просмотр сайта» справа, чтобы запустить статический сайт в режиме разделенного просмотра.


Это эмулятор для создания демонстрационных HTTP-запросов. Используя то, что вы узнали из заданий выше, ответьте на вопросы ниже.


Если статический сайт не отображается, нажмите синюю кнопку «Показать разделенный вид» в верхней части страницы.

### Ответьте на вопросы ниже
Сделайте запрос GET к /api/users. Какой флаг?
```commandline
THM{YOU_HAVE_JUST_FOUND_THE_USER_LIST}
```
Сделайте запрос  POST/api/user/2  и обновите страну Боба с UK на US . Какой флаг?

Примечание: для всех требуемых параметров используйте только строчные буквы.
```commandline
THM{YOU_HAVE_MODIFIED_THE_USER_DATA}
```
Сделайте запрос  DELETE/api/user/1 для  удаления пользователя. Что такое флаг?
```commandline
THM{YOU_HAVE_JUST_DELETED_A_USER}
```

## Задание 11
Вот и все! Вы выполнили все задания! Надеемся, вам понравилось изучать элементы, из которых состоят веб-приложения. Надеемся, вы узнали немного больше о:

Какие компоненты задействованы в веб-приложениях
Структура унифицированного указателя ресурсов (URL)
Что такое HTTP- сообщения, запросы, заголовки и ответы?
Важность заголовков безопасности
Наслаждайтесь вашим следующим познавательным приключением.

### Ответьте на вопросы ниже
Я готов двигаться вперед и узнать больше о безопасности веб-приложений.
```commandline
Ответ не нужен
```

[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)