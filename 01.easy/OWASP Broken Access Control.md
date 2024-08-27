[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)

# Комната [OWASP Broken Access Control](https://tryhackme.com/r/room/owaspbrokenaccesscontrol) 

Всего 7 заданий:
## Задание 1
Неисправный контроль доступа — это тип уязвимости безопасности, которая возникает, когда приложение или система не может должным образом ограничить доступ к конфиденциальным данным или функциям. Эта уязвимость позволяет злоумышленникам получить несанкционированный доступ к ресурсам, которые должны быть ограничены, таким как учетные записи пользователей, файлы, базы данных или административные функции. Неисправный контроль доступа может возникнуть из-за различных факторов, включая плохой дизайн, ошибки конфигурации или ошибки кодирования.

Цели, которые изучит студент:
- Узнайте, что такое нарушение контроля доступа и каковы его последствия.
- Выявите уязвимости взломанного контроля доступа в веб-приложениях.
- Используйте эти уязвимости в контролируемой среде.
- Понимать и применять меры по смягчению и предотвращению этих уязвимостей.

Предварительные условия:
- Базовые знания JSON, веб-приложений и протоколов HTTP.
- Знакомство с языками сценариев, такими как PHP и JavaScript.
- Знание стандартов и фреймворков безопасности веб-приложений, таких как OWASP Top 10.
- Базовое понимание и использование прокси-инструмента, такого как Burp Suite.

### Ответьте на вопросы ниже
Нажмите на меня, чтобы перейти к следующему заданию.
```commandline
Ответ не нужен
```

## Задание 2
Что такое контроль доступа?
Контроль доступа — это механизм безопасности, используемый для контроля того, каким пользователям или системам разрешен доступ к определенному ресурсу или системе. Контроль доступа реализован в компьютерных системах, чтобы гарантировать, что только авторизованные пользователи имеют доступ к ресурсам, таким как файлы, каталоги, базы данных и веб-страницы. Основная цель контроля доступа — защитить конфиденциальные данные и гарантировать, что они доступны только тем, кто имеет на это разрешение.

Пример контроля доступа

Контроль доступа может быть реализован различными способами в зависимости от типа защищаемого ресурса и требований безопасности системы. Некоторые общие механизмы контроля доступа включают:

Дискреционный контроль доступа (DAC) : в этом типе контроля доступа владелец ресурса или администратор определяет, кому разрешен доступ к ресурсу и какие действия им разрешено выполнять. DAC обычно используется в операционных системах и файловых системах. Проще говоря, представьте себе замок, где король может давать ключи своим советникам, позволяя им открывать любые двери, которые им нравятся, когда они захотят. Это DAC для вас. Это свобода контролировать доступ к собственным ресурсам. Тот, кто у власти, как король замка, может выдавать разрешения кому угодно, диктуя, кто может входить и выходить.

Пример дискреционного контроля доступа

Обязательный контроль доступа (MAC) : в этом типе контроля доступа доступ к ресурсам определяется набором предопределенных правил или политик, которые применяются системой. MAC обычно используется в высокозащищенных средах, таких как правительственные и военные системы. Проще говоря, представьте себе форт с железным протоколом безопасности. Только определенные лица с определенными допусками могут получить доступ к определенным зонам, и это не подлежит обсуждению. Верховный командующий устанавливает правила, и они неукоснительно соблюдаются. Вот как работает MAC. Это как строгий офицер безопасности, который не допускает никаких исключений из правил.

Пример обязательного контроля доступа

Управление доступом на основе ролей ( RBAC ) : в этом типе управления доступом пользователям назначаются роли, которые определяют их уровень доступа к ресурсам. RBAC обычно используется в корпоративных системах, где пользователи имеют разные уровни полномочий в зависимости от их должностных обязанностей. Проще говоря, представьте себе современную корпорацию. У вас есть менеджеры, руководители, торговые представители и т. д. У каждого из них разный доступ к зданию. Некоторые могут войти в зал заседаний, другие могут получить доступ в торговый зал и т. д. В этом суть RBAC — назначение доступа на основе роли человека в организации.

Пример ролевого контроля доступа

Управление доступом на основе атрибутов (ABAC) : в этом типе управления доступом доступ к ресурсам определяется набором атрибутов, таких как роль пользователя, время суток, местоположение и устройство. ABAC обычно используется в облачных средах и веб-приложениях. Проще говоря, представьте себе высокотехнологичную систему безопасности из научной фантастики, которая сканирует людей на наличие определенных атрибутов. Возможно, она проверяет, с какой планеты они прибыли, носят ли они определенное устройство или пытаются ли получить доступ к ресурсу в определенное время. Это ABAC. Это как интеллектуальная, гибкая безопасность будущего.

Пример контроля доступа на основе атрибутов

Реализация контроля доступа может помочь предотвратить нарушения безопасности и несанкционированный доступ к конфиденциальным данным. Однако контроль доступа не является абсолютно надежным и может быть уязвимым для различных типов атак, таких как повышение привилегий и уязвимости контроля доступа. Поэтому важно регулярно проверять и тестировать механизмы контроля доступа, чтобы убедиться, что они работают так, как задумано.

Нарушенный контроль доступа:
Уязвимости сломанного контроля доступа относятся к ситуациям, когда механизмы контроля доступа не обеспечивают надлежащие ограничения доступа пользователя к ресурсам или данным. Вот некоторые распространенные эксплойты для сломанного контроля доступа и примеры:

Горизонтальное повышение привилегий  происходит, когда злоумышленник может получить доступ к ресурсам или данным, принадлежащим другим пользователям с тем же уровнем доступа. Например, пользователь может получить доступ к учетной записи другого пользователя, изменив идентификатор пользователя в URL.

Вертикальное повышение привилегий происходит, когда злоумышленник может получить доступ к ресурсам или данным, принадлежащим пользователям с более высокими уровнями доступа. Например, обычный пользователь может получить доступ к административным функциям, манипулируя скрытым полем формы или параметром URL.



Недостаточные проверки контроля доступа происходят, когда проверки контроля доступа не выполняются правильно или последовательно, что позволяет злоумышленнику обойти их. Например, приложение может позволить пользователям просматривать конфиденциальные данные без проверки их соответствующих разрешений.

Небезопасные прямые ссылки на объекты возникают, когда злоумышленник может получить доступ к ресурсу или данным, используя уязвимость в механизмах контроля доступа приложения. Например, приложение может использовать предсказуемые или легко угадываемые идентификаторы для конфиденциальных данных, что упрощает злоумышленнику доступ. Вы можете обратиться к этой комнате  в Задании № 4,  чтобы узнать больше об этом.

Пример небезопасных прямых ссылок на объекты

Эти атаки можно предотвратить, внедрив надежные механизмы контроля доступа и регулярно проверяя и тестируя их, чтобы убедиться, что они функционируют должным образом.

### Ответьте на вопросы ниже
Что такое ИДОР?
```commandline
Insecure direct object reference
```
Что происходит, когда злоумышленник получает доступ к ресурсам или данным, принадлежащим другим пользователям с таким же уровнем доступа?
```commandline
Horizontal privilege escalation
```
Что происходит, когда злоумышленник получает доступ к ресурсам или данным пользователей с более высокими уровнями доступа?
```commandline
Vertical privilege escalation
```
Что такое АБАК?
```commandline
Attribute-Based Access Control
```
Что такое RBAC?
```commandline
Role-Based Access Control
```

## Задание 3
Чтобы сосредоточиться на изучении неисправных средств контроля доступа, нажмите  Start Machine кнопку, расположенную в правом верхнем углу этой задачи, чтобы развернуть виртуальную машину для этой комнаты.

После получения сгенерированного IP-адреса машины вы можете либо использовать наш AttackBox, либо использовать собственную виртуальную машину , подключенную к VPN TryHackMe, чтобы начать атаку. Если вы предпочитаете использовать AttackBox, вы можете просто нажать на  Start AttackBox кнопку, расположенную над названием комнаты.

После запуска AttackBox или подключения вашей атакующей  виртуальной машины к VPN  TryHackMe вы можете начать получать доступ к целевому веб-сайту, введя http://MACHINE_IP/ в браузере.

Предварительный просмотр уязвимого приложения

Имейте в виду, что запуск машины может занять до 5 минут .

### Ответьте на вопросы ниже
Я задействовал машину, прикрепленную к заданию.
```commandline
Ответ не нужен
```

## Задание 4
Цель обучения:
В этой задаче наша цель — получить полное представление о функциональности веб-приложения. Это позволит нам максимально использовать возможности приложения и достичь желаемых результатов.

Оценка заявки:
Когда вы просматриваете веб-приложение в качестве тестера на проникновение, представьте, как выглядит базовый код и какие уязвимости приходят вам на ум для каждой функции, запроса и ответа.

Веб-приложение для этой комнаты включает в себя панель инструментов, форму входа и регистрации, которая позволяет пользователям получать доступ к панели инструментов веб-сайта. С точки зрения пентестера веб-приложений пентестер обычно регистрирует учетную запись. После регистрации пентестер затем попытается проверить функцию входа на наличие уязвимостей контроля доступа.

Ниже приведены скриншоты каждой веб-страницы:

Регистрация:

Страница регистрации

Авторизоваться:

Страница входа

Панель инструментов:

Страница панели инструментов

Чтобы перехватывать HTTP-запросы, отправляемые на сервер, мы можем использовать OWASP ZAP  или Burp Suite Community Edition.

Более подробную информацию об использовании Burp Suite и его функциональных возможностях можно найти в модуле Burp Suite .

Захват HTTP- трафика
Для того, чтобы мы могли дополнительно проанализировать запросы и ответы, отправляемые и получаемые с сервера, мы будем использовать модуль « Proxy » Burp Suite для захвата HTTP- трафика, отправляемого на сервер. Захваченный HTTP- трафик может использоваться с другими модулями Burp Suite .

Затем их можно обработать или отправить на другие инструменты, например, «Повторитель» , для дальнейшей обработки, прежде чем им будет разрешено продолжить путь к месту назначения. 

Ниже представлен захваченный HTTP- трафик, отправляемый functions.phpпосле входа в систему.

Захваченный HTTP-трафик

На основе представленного выше снимка экрана мы можем заметить, что после завершения процесса входа в систему веб-приложение выдаст нам ответ JSON , содержащий статус, сообщение, first_name, last_name, is_admin и redirect_link, которые сервер использует для перенаправления пользователя на страницу dashboard.phpс параметром «isadmin» в URL-адресе.

Понимание содержания  HTTP-  запроса и ответа:
- В целевом веб-приложении не реализованы заголовки безопасности, что свидетельствует об отсутствии превентивных мер 
(например, первой линии обороны) для защиты веб-приложения от определенных типов атак.
- Целевое веб-приложение работает на  операционной системе Linux  ( Debian) и использует  веб-сервер Apache  ( 
  Apache/2.4.38). Эта информация может быть полезна для выявления потенциальных уязвимостей безопасности, которые могут существовать в целевом веб-приложении.
- Целевое веб-приложение использует  PHP/8.0.19 в качестве своего языка программирования бэкэнда. Эта информация 
  важна для понимания технологического стека приложения и выявления потенциальных уязвимостей безопасности или проблем совместимости, которые могут возникнуть с другими компонентами программного обеспечения.
- Целевое веб-приложение перенаправляет пользователя на панель управления с параметром, который мы можем проверить на 
  предмет уязвимостей повышения привилегий.
### Ответьте на вопросы ниже
Какой тип сервера размещает веб-приложение? Это можно узнать в ответе на запрос в Burp Suite.
```commandline
Apache
```
Как называется параметр в ответе JSON на запрос на вход, содержащий ссылку перенаправления?
```commandline
redirect_link
```
Какой модуль Burp Suite позволяет нам  захватывать запросы и ответы между нами и нашей целью?
```commandline
Proxy
```
Какой адрес электронной почты администратора можно найти в таблице онлайн-пользователей?
```commandline
admin@admin.com
```

## Задание 5
В предыдущей задаче мы узнали, что файл functions.phpвозвращает ответ JSON при входе в систему. Ответ содержит redirect_link с параметром, который мы можем протестировать на предмет уязвимостей контроля доступа.

Чтобы начать тестирование на эту уязвимость, мы можем перехватить HTTP- ответ и скопировать значение параметра redirect_link  в нашу адресную строку.

Перенаправить ссылку в адресной строке

Поскольку приложение перенаправляет пользователя на dashboard.php, а ответ JSON можно увидеть только путем перехвата с помощью прокси-инструмента, мы можем попробовать изменить значение параметра с  «false» на «true» или наоборот.

Измененное значение параметра в адресной строке

При изменении значения с false на true приложение перенаправляет нас на admin.php, который по умолчанию скрыт для обычного пользователя. Ниже представлен HTTP-запрос, который захватывается с помощью Burp Suite Proxy .

Захваченный HTTP-запрос с использованием Burp Suite Proxy

Предварительный просмотр страницы администратора

Поскольку у нас есть доступ к admin.php с использованием учетной записи с низкими привилегиями, мы могли бы также проверить наличие атаки с вертикальным повышением привилегий.

Отметив галочкой поле в столбце «Доступ администратора» зарегистрированной вами учетной записи и нажав кнопку «Сохранить изменения», вы предоставите нам права администратора. Что в свою очередь позволит нам отозвать доступ других пользователей-администраторов.

Предварительный просмотр страницы администратора с измененным доступом администратора

### Ответьте на вопросы ниже
Какое повышение привилегий произошло после доступа к admin.php?
```commandline
Vertical
```
Какой параметр позволяет злоумышленнику получить доступ к странице администратора?
```commandline
isadmin
```
Что означает флаг на странице администратора?
```commandline
THM{I_C4n_3xpl01t_B4c}
```
## Задание 6
Существует несколько шагов, которые можно предпринять для снижения риска нарушения контроля доступа в приложениях PHP :

Реализуйте управление доступом на основе ролей ( RBAC ) : управление доступом на основе ролей ( RBAC ) — это метод регулирования доступа к компьютерным или сетевым ресурсам на основе ролей отдельных пользователей в рамках предприятия. Определяя роли в организации и назначая права доступа этим ролям, вы можете контролировать, какие действия пользователь может выполнять в системе. Приведенный фрагмент кода иллюстрирует, как можно определять роли (например, «администратор», «редактор» или «пользователь») и связанные с ними разрешения. Функция hasPermissionпроверяет, имеет ли пользователь определенной роли указанное разрешение.

Образец кода
```commandline
// Define roles and permissions
 $roles = [
     'admin' => ['create', 'read', 'update', 'delete'],
     'editor' => ['create', 'read', 'update'],
     'user' => ['read'],
 ];

 // Check user permissions
 function hasPermission($userRole, $requiredPermission) {
     global $roles;
     return in_array($requiredPermission, $roles[$userRole]);
 }

 // Example usage
 if (hasPermission('admin', 'delete')) {
     // Allow delete operation
 } else {
     // Deny delete operation
 }
```
 
Используйте параметризованные запросы : параметризованные запросы — это способ защиты PHP- приложений от атак SQL- инъекций, при которых злоумышленники могут получить несанкционированный доступ к вашей базе данных. Используя заполнители вместо прямого включения пользовательского ввода в SQL- запрос, вы можете значительно снизить риск атак SQL- инъекций. Приведенный пример демонстрирует, как можно сделать запрос безопасным с помощью подготовленных операторов, которые отделяют синтаксис SQL от данных и безопасно обрабатывают пользовательский ввод.

Образец кода
```commandline
// Example of vulnerable query
 $username = $_POST['username'];
 $password = $_POST['password'];
 $query = "SELECT * FROM users WHERE username='$username' AND password='$password'";

 // Example of secure query using prepared statements
 $username = $_POST['username'];
 $password = $_POST['password'];
 $stmt = $pdo->prepare("SELECT * FROM users WHERE username=? AND password=?");
 $stmt->execute([$username, $password]);
 $user = $stmt->fetch();

``` 
Правильное управление сеансами : Правильное управление сеансами гарантирует, что аутентифицированные пользователи имеют своевременный и соответствующий доступ к ресурсам, тем самым снижая риск несанкционированного доступа к конфиденциальной информации. Управление сеансами включает использование защищенных файлов cookie, установку тайм-аутов сеансов и ограничение количества активных сеансов, которые может иметь пользователь. Фрагмент кода показывает, как инициализировать сеанс, задать переменные сеанса и проверить действительность сеанса, просматривая время последней активности.

Образец кода

```commandline
// Start session
 session_start();

 // Set session variables
 $_SESSION['user_id'] = $user_id;
 $_SESSION['last_activity'] = time();

 // Check if session is still valid
 if (isset($_SESSION['last_activity']) && (time() - $_SESSION['last_activity'] > 1800)) {
     // Session has expired
     session_unset();
     session_destroy();
 }
``` 
Используйте безопасные методы кодирования : безопасные методы кодирования включают методы предотвращения внедрения уязвимостей безопасности. Разработчики должны дезинфицировать и проверять пользовательский ввод, чтобы предотвратить вредоносные данные от нанесения вреда и избегать использования небезопасных функций или библиотек. Приведенный пример показывает, как дезинфицировать пользовательский ввод с помощью функции PHP иfilter_input демонстрирует, как безопасно хэшировать пароль, используя password_hashвместо небезопасной функции, такой как md5.

Образец кода
```commandline

// Validate user input
 $username = filter_input(INPUT_POST, 'username', FILTER_SANITIZE_STRING);
 $password = filter_input(INPUT_POST, 'password', FILTER_SANITIZE_STRING);

 // Avoid insecure functions
 // Example of vulnerable code using md5
 $password = md5($password);
 // Example of secure code using password_hash
 $password = password_hash($password, PASSWORD_DEFAULT);
``` 
### Ответьте на вопросы ниже
Нажмите на меня, чтобы перейти к следующему заданию.

```commandline
Ответ не нужен
```

## Задание 7
Нарушение контроля доступа — это уязвимость системы безопасности, которая возникает, когда система не обеспечивает должным образом контроль доступа, что может привести к получению неавторизованными пользователями доступа к конфиденциальной информации или выполнению действий, на которые у них нет полномочий.

Горизонтальное повышение привилегий происходит, когда пользователь может получить доступ к данным или выполнить действия, которые ему не разрешены в рамках его собственного уровня привилегий. Это может быть опасно, поскольку это может позволить злоумышленнику, который уже получил доступ к системе, перемещаться по сети и получать доступ к дополнительным ресурсам или конфиденциальным данным.

Вертикальное повышение привилегий происходит, когда пользователь может получить доступ к данным или выполнить действия, зарезервированные для пользователей с более высокими уровнями привилегий, например, системных администраторов. Это может быть еще более опасно, поскольку может позволить злоумышленнику получить полный контроль над системой и потенциально захватить всю сеть.

Влияние этих типов повышения привилегий может различаться в зависимости от конкретной системы и уровня полученного доступа. Однако в целом последствия могут включать несанкционированный доступ к конфиденциальной информации, потерю или кражу данных, нарушение работы критических систем или служб и даже полную компрометацию сети. Поэтому важно внедрить строгий контроль доступа и регулярно отслеживать любые признаки несанкционированного доступа или активности.

Вот несколько ссылок, которые вы можете дать разработчикам PHP , чтобы помочь им реализовать эти стратегии смягчения:

Памятка по настройке PHP OWASP
 Правильный путь в PHP : безопасность
Безопасное кодирование на  PHP
### Ответьте на вопросы ниже
Нажмите на меня, чтобы закончить эту комнату.
```commandline
Ответ не нужен
```

[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)