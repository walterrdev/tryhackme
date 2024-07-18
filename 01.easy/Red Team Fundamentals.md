[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)

# Комната [Red Team Fundamentals](https://tryhackme.com/r/room/redteamfundamentals) 

Всего 7 заданий:
## Задание 1
Кибербезопасность — это постоянная гонка между белыми и черными хакерами. По мере развития угроз в кибермире растет 
и потребность в более специализированных услугах, которые позволяют компаниям максимально подготовиться к реальным 
атакам.  

Хотя традиционные меры безопасности, такие как оценка уязвимости и тесты на проникновение, могут предоставить 
превосходный обзор состояния технической безопасности компании, они могут упустить из виду некоторые другие аспекты, 
которые может использовать настоящий злоумышленник. В этом смысле можно сказать, что традиционные тесты на 
проникновение хорошо показывают уязвимости, чтобы вы могли принять упреждающие меры, но они не могут научить вас, 
как реагировать на реальную продолжающуюся атаку мотивированного противника.    

Цели комнаты
- Узнайте об основах взаимодействия с красной командой
- Определите основные компоненты и заинтересованные стороны, участвующие в работе красной команды.
- Понять основные различия между Red Teaming и другими типами мероприятий по кибербезопасности.

Требования к помещению
Перед началом этой комнаты требуется знакомство с общими методами взлома. Хотя это не является строго обязательным, 
рекомендуется пройти обучающий курс Jr. Penetration Tester. 

### Ответить на вопросы ниже
Нажмите, чтобы перейти к следующей задаче

```commandline
Ответ не нужен
```

## Задание 2
Оценка уязвимости

Это самая простая форма оценки безопасности, и ее главная цель — выявить как можно больше уязвимостей в как можно 
большем количестве систем в сети. С этой целью могут быть сделаны уступки для эффективного достижения этой цели. 
Например, машина злоумышленника может быть внесена в список разрешенных доступных решений безопасности, чтобы не 
мешать процессу обнаружения уязвимостей. Это имеет смысл, поскольку цель — рассмотреть каждый хост в сети и оценить 
его состояние безопасности индивидуально, предоставляя при этом компании как можно больше информации о том, на чем 
следует сосредоточить усилия по исправлению.     

Подводя итог, можно сказать, что оценка уязвимости фокусируется на сканировании хостов на предмет уязвимостей как 
отдельных объектов, чтобы можно было выявить недостатки безопасности  и применить эффективные меры безопасности для 
защиты сети в приоритетном порядке. Большая часть работы может быть выполнена с помощью автоматизированных 
инструментов и выполняться операторами без необходимости в особых технических знаниях.   

Например, если бы вы проводили оценку уязвимости в сети, вы бы обычно попытались просканировать как можно больше 
хостов, но на самом деле не пытались бы эксплуатировать какие-либо уязвимости: 

### Тесты на проникновение
Помимо сканирования каждого отдельного хоста на предмет уязвимостей, нам часто нужно понимать, как они влияют на 
нашу сеть в целом. Тесты на проникновение дополняют оценку уязвимости, позволяя пентестеру исследовать влияние 
злоумышленника на всю сеть, выполняя дополнительные шаги, которые включают:  

Попытайтесь  использовать  уязвимости, обнаруженные в каждой системе. Это важно, поскольку иногда уязвимость может 
существовать в системе, но компенсаторные элементы управления эффективно предотвращают ее использование. Это также 
позволяет нам проверить, можем ли мы использовать обнаруженные уязвимости для компрометации данного хоста.  
Выполнение  задач по постэксплуатации  на любом скомпрометированном хосте, что позволяет нам выяснить, можем ли мы 
извлечь из них какую-либо полезную информацию или можем ли мы использовать их для перехода на другие хосты, которые 
ранее не были доступны с того места, где мы находимся.  
Тесты на проникновение могут начинаться со сканирования уязвимостей, как и обычная оценка уязвимости, но 
предоставлять дополнительную информацию о том, как злоумышленник может объединять уязвимости в цепочку для 
достижения определенных целей. Хотя его фокус остается на выявлении уязвимостей и установлении мер по защите сети, 
он также рассматривает сеть как целостную экосистему и то, как злоумышленник может получить выгоду от взаимодействия 
между ее компонентами.    

Если бы мы проводили тест на проникновение, используя тот же пример сети, что и раньше, то помимо сканирования всех 
хостов в сети на наличие уязвимостей мы бы попытались подтвердить, можно ли их использовать, чтобы 
продемонстрировать влияние, которое злоумышленник может оказать на сеть:


Анализируя, как злоумышленник может перемещаться по нашей сети, мы также получаем базовое представление о возможных 
обходах мер безопасности и о нашей способности обнаружить  реального  субъекта угрозы в определенной степени, 
ограниченной, поскольку область действия теста на проникновение обычно обширна, а тестировщики на проникновение не 
слишком заботятся о том, чтобы быть громкими или генерировать множество оповещений на устройствах безопасности, 
поскольку временные ограничения в таких проектах часто требуют от нас проверки сети в сжатые сроки.    



Расширенные постоянные угрозы и почему регулярного тестирования на проникновение недостаточно
Хотя упомянутые нами традиционные мероприятия по безопасности охватывают поиск большинства технических уязвимостей, 
существуют ограничения на такие процессы и на степень, в которой они могут эффективно подготовить компанию к 
реальному злоумышленнику. К таким ограничениям относятся:  



В результате некоторые аспекты тестов на проникновение могут существенно отличаться от реальной атаки, например:

Тесты на проникновение ГРОМКИ: Обычно пентестеры не прилагают много усилий, чтобы остаться незамеченными. В отличие 
от настоящих злоумышленников, они не против того, чтобы их было легко обнаружить, поскольку они были наняты, чтобы 
найти как можно больше уязвимостей на как можно большем количестве хостов.  
Нетехнические векторы атак могут быть упущены из виду: атаки, основанные на социальной инженерии или физических 
вторжениях, обычно не включаются в то, что тестируется. 
Ослабление механизмов безопасности:  при проведении обычного теста на проникновение некоторые механизмы безопасности 
могут быть временно отключены или ослаблены для команды пентестеров в пользу эффективности. Хотя это может 
показаться нелогичным, важно помнить, что у пентестеров ограниченное время для проверки сети. Поэтому обычно 
желательно не тратить время на поиск экзотических способов обхода IDS / IPS , WAF, обмана вторжения или других мер 
безопасности, а сосредоточиться на проверке критически важной технологической инфраструктуры на предмет уязвимостей.

С другой стороны, настоящие злоумышленники не будут следовать этическому кодексу и в основном не ограничены в своих 
действиях. В настоящее время наиболее известные субъекты угроз известны как  Advanced Persistent Threats (APT), 
которые представляют собой высококвалифицированные группы злоумышленников, обычно спонсируемые странами или 
организованными преступными группами. Они в первую очередь нацелены на критическую инфраструктуру, финансовые 
организации и государственные учреждения. Их называют постоянными, потому что операции этих групп могут оставаться 
незамеченными в скомпрометированных сетях в течение длительного времени.     


Если компания подверглась воздействию APT, будет ли она готова эффективно отреагировать? Смогут ли они обнаружить 
методы, используемые для получения и сохранения доступа к своим сетям, если злоумышленник находится там в течение 
нескольких месяцев? Что, если первоначальный доступ был получен, потому что Джон из бухгалтерии открыл 
подозрительное вложение к электронному письму? Что, если был задействован эксплойт нулевого дня? Готовят ли нас к 
этому предыдущие тесты на проникновение?

Для обеспечения более реалистичного подхода к безопасности была создана команда Red Team Engagements.

### Ответить на вопросы ниже
Подготовит ли нас оценка уязвимости к обнаружению реального злоумышленника в наших сетях? (Да/Нет)
```commandline
Nay
```
Во время теста на проникновение вы обеспокоены тем, что клиент вас обнаружит? (Да/Нет)
```commandline
Nay
```
Высокоорганизованные группы опытных нападающих в настоящее время называются ...
```commandline
Advanced Persistent Threats
```

## Задание 3
Чтобы идти в ногу с новыми угрозами, были разработаны мероприятия Red Team, чтобы сместить фокус с обычных тестов на 
проникновение на процесс, который позволяет нам четко видеть возможности нашей оборонительной команды по  
обнаружению и реагированию на реального субъекта угрозы. Они не заменяют традиционные тесты на проникновение, а 
дополняют их, фокусируясь на обнаружении и реагировании, а не на предотвращении.

Red teaming — термин, заимствованный из военных. В военных учениях группа берет на себя роль красной команды, чтобы 
имитировать методы атаки, чтобы проверить возможности реакции обороняющейся команды, обычно известной как синяя 
команда, против известных стратегий противника. В переводе на язык кибербезопасности, действия красной команды 
состоят из имитации тактики, методов и процедур (TTP) реального субъекта угрозы, чтобы мы могли измерить, 
насколько хорошо наша синяя команда реагирует на них, и в конечном итоге улучшить любые имеющиеся средства контроля 
безопасности.     



Каждое взаимодействие красной команды начинается с определения четких целей, часто называемых драгоценностями 
короны или флагами, начиная от компрометации определенного критического хоста до кражи некоторой конфиденциальной 
информации у цели. Обычно синяя команда не будет проинформирована о таких упражнениях, чтобы избежать внесения 
каких-либо предубеждений в свой анализ. Красная команда сделает все возможное, чтобы достичь целей, оставаясь 
незамеченной и обходя любые существующие механизмы безопасности, такие как брандмауэры, антивирусы, EDR, IPS и 
другие. Обратите внимание, что при взаимодействии красной команды не все хосты в сети будут проверены на уязвимости. 
Реальному злоумышленнику нужно будет найти только один путь к своей цели, и он не заинтересован в выполнении шумных 
сканирований, которые может обнаружить синяя команда.       



Взяв ту же сеть, что и раньше, в сражении красной команды, где цель состоит в том, чтобы скомпрометировать сервер 
интрасети, мы бы спланировали способ достижения нашей цели, взаимодействуя как можно меньше с другими хостами. Между 
тем, способность синей команды обнаруживать и соответствующим образом реагировать на атаку может быть оценена:   



Важно отметить, что конечной целью таких учений никогда не должно быть «победа» красной команды над синей командой, 
а скорее имитация достаточного количества TTP, чтобы синяя команда научилась адекватно реагировать на реальную 
текущую угрозу. При необходимости они могли бы подправить или добавить элементы управления безопасностью, которые 
помогут улучшить их возможности обнаружения.   

Бои Красной команды также улучшают результаты обычных тестов на проникновение, учитывая несколько поверхностей атаки:
 
Техническая инфраструктура: как и в обычном тесте на проникновение, красная команда попытается обнаружить 
технические уязвимости, уделяя гораздо больше внимания скрытности и уклонению. 
Социальная инженерия: воздействие на людей с помощью фишинговых кампаний, телефонных звонков или социальных сетей с 
целью заставить их раскрыть информацию, которая должна быть конфиденциальной. 
Физическое проникновение: использование таких методов, как взлом замков, клонирование RFID-меток, использование 
уязвимостей электронных устройств контроля доступа для доступа к закрытым зонам объектов. 
В зависимости от имеющихся ресурсов учения красной команды могут проводиться несколькими способами:

Полное взаимодействие: смоделируйте весь рабочий процесс злоумышленника, от первоначального взлома до достижения 
конечных целей. 
Предполагаемое нарушение: Начните с предположения, что злоумышленник уже получил контроль над некоторыми активами, и 
попытайтесь достичь целей оттуда. Например, красная команда может получить доступ к учетным данным некоторых 
пользователей или даже к рабочей станции во внутренней сети.  
Table-top Exercise: Моделирование за столом, где сценарии обсуждаются красной и синей командами, чтобы оценить, 
как они теоретически отреагируют на определенные угрозы. Идеально подходит для ситуаций, когда проведение реальных 
симуляций может быть сложным.  
### Ответить на вопросы ниже
Цели боя красной команды часто называют флагами или...

```commandline
crown jewels
```
Во время боя с красной командой общие методы, используемые атакующими, эмулируются против цели. Такие методы обычно 
называются TTP. Что означает TTP? 
```commandline
Tactics, techniques and procedures
```
Основная цель действий красной команды — обнаружить как можно больше уязвимостей на как можно большем количестве 
хостов (да/нет) 
```commandline
Nay
```

## Задание 4
В красной команде задействовано несколько факторов и людей. У каждого будет свой образ мышления и методология 
подхода к персоналу, участвующему в команде; однако, каждая команда может быть разбита на три команды или ячейки. 
Ниже приведена краткая таблица, иллюстрирующая каждую из команд, и краткое объяснение их обязанностей.

### Команда	Определение
- Красная клетка	Красная ячейка — это компонент, который составляет наступательную часть боя красной команды, 
имитирующую стратегические и тактические ответы заданной цели.
- Синяя ячейка	Синяя ячейка — это противоположность красной. Она включает все компоненты, защищающие целевую сеть. 
  Синяя ячейка обычно состоит из членов синей команды, защитников, внутреннего персонала и руководства организации.
- Белая клетка	Выступает в качестве арбитра между действиями эритроцитов и реакциями синих клеток во время 
  взаимодействия. Контролирует среду/сеть взаимодействия. Следит за соблюдением ROE. Координирует действия, 
  необходимые для достижения целей взаимодействия. Соотносит действия эритроцитов с оборонительными действиями. 
  Обеспечивает проведение взаимодействия без предвзятости в какую-либо сторону.  
>Определения взяты из redteam.guide.

Эти команды или ячейки можно далее разбить на части по иерархии взаимодействия.

Поскольку это комната, ориентированная на красную команду, мы сосредоточимся на обязанностях красной ячейки. Ниже 
приведена таблица, описывающая роли и обязанности членов красной команды.


Как и в случае с большинством функций красной команды, каждая команда и компания будут иметь свою собственную 
структуру и роли для каждого члена команды. Приведенная выше таблица служит только примером типичных обязанностей 
каждой роли.  

### Ответить на вопросы ниже
Какая ячейка отвечает за наступательные операции в бою?
```commandline
Red Cell
```
Частью какой ячейки является доверенный агент?
```commandline
White Cell
```

## Задание 5
Основная функция красной команды — эмуляция противника. Хотя это и не обязательно, но обычно используется для оценки 
того, что реальный противник будет делать в среде, используя свои инструменты и методологии. Красная команда может 
использовать различные цепочки киберубийств для обобщения и оценки шагов и процедур взаимодействия.   

Синяя команда обычно использует киберцепочки убийств для картирования поведения и разбивки движения противника. 
Красная команда может адаптировать эту идею для картирования TTP противника ( тактики ,  приемы и  процедуры ) к 
компонентам взаимодействия.  

Многие органы регулирования и стандартизации выпустили свои цепочки киберубийств. Каждая цепочка киллов следует 
примерно одной и той же структуре, некоторые из них углубляются или определяют цели по-другому. Ниже приведен 
небольшой список стандартных цепочек киберубийств.  

Lockheed Martin Cyber Kill Chain
Единая цепочка убийств
Varonis Cyber Kill Chain
Цикл атаки Active Directory
Фреймворк MITRE ATT&CK
В этой комнате мы будем часто ссылаться на «Lockheed Martin Cyber Kill Chain». Это более стандартизированная цепочка 
убийств, чем другие, и она очень часто используется среди красных и синих команд. 

Цепочка уничтожения Lockheed Martin фокусируется на периметре или внешнем нарушении. В отличие от других цепочек 
уничтожения, она не обеспечивает глубокого анализа внутреннего движения. Вы можете рассматривать эту цепочку 
уничтожения как сводку всех имеющихся поведений и операций.  

Компоненты цепочки уничтожения представлены в таблице ниже.

### Ответить на вопросы ниже
Если бы противник развернул Mimikatz на целевой машине, где бы он оказался в цепочке кибератак Lockheed Martin?
```commandline
Installation
```

Целью какой техники является использование целевой системы для выполнения кода?
```commandline
Exploitation
```
## Задание 6
Все, что мы обсудили, объединяется при выполнении взаимодействия красной команды. Чтобы лучше понять, как 
взаимодействуют компоненты и заинтересованные стороны, мы проанализируем упрощенный пример взаимодействия. Перейдите 
к зеленой кнопке «Просмотреть сайт», чтобы продолжить.  

Посмотреть сайт
Обратите внимание, как Cyber Kill Chain естественным образом соответствует упражнению: мы начинаем с фазы разведки 
, на которой собираем как можно больше информации о нашей цели, затем следуют этапы использования уязвимости и 
доставки путем отправки фишингового письма с вредоносным вложением, затем следуют этапы эксплуатации и установки , 
когда используются локальные эксплойты для повышения привилегий на BOB-PC, а затем устанавливаются инструменты на 
скомпрометированных хостах для сброса хэшей паролей и выполнения горизонтального перемещения, и заканчиваются 
действиями по целям , на которых наконец устанавливается соединение с нашей целью.     

### Ответить на вопросы ниже
Нажмите кнопку «Просмотреть сайт» и следуйте примеру взаимодействия, чтобы получить флаг.

```commandline
THM{RED_TEAM_ROCKS}
```

## Задание 7
В этой комнате представлен упрощенный обзор Red Team Engagements. Основные концепции, компоненты и заинтересованные 
стороны были представлены для получения первого понимания таких упражнений. В следующих комнатах вы узнаете все о 
планировании, стоящем за реальным взаимодействием, а также о множестве интересных приемов, которые настоящий 
злоумышленник будет использовать по ходу дела, включая то, как использовать разведданные об угрозах в своих 
интересах, обходить механизмы безопасности, присутствующие в любом современном хосте, выполнять боковое перемещение 
и пытаться избежать обнаружения любой ценой.

### Ответить на вопросы ниже
Прочитайте вышеизложенное и продолжайте обучение!

```commandline
Ответ не нужен
```
[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)