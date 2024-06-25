[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)

# Комната [Intro to IR and IM](https://tryhackme.com/r/room/introtoirandim)

## Задание 1 Введение
Киберинциденты на данный момент являются частью жизни. Вопрос больше не в том, произойдет ли в организации инцидент,
а в том, когда именно. К счастью, мы стали значительно лучше справляться с этими инцидентами с помощью хорошо 
отлаженных процессов и технологий, называемых «Реагирование на инциденты» и «Управление инцидентами». В этом зале 
мы познакомим вас с этими процессами. Несмотря на множество технологических достижений, люди по-прежнему необходимы 
для надлежащего управления и реагирования во время инцидента.

#### Предварительные условия
Введение в оборонную безопасность
Цели обучения

- Базовое понимание реагирования на инциденты и управления инцидентами.
- Понимание разницы между реагированием и управлением
- Понимание различных ролей во время инцидента
- Понять процесс управления инцидентами
- Понимание распространенных проблем, которые могут возникнуть во время инцидента, и способов предотвращения этих 
  ловушек.

#### Ответить на вопросы ниже
Я готов узнать о реагировании на инциденты и управлении инцидентами!
```
Ответ не нужен
```
## Задача 2 Что такое реагирование на инциденты и управление ими?
#### Что такое киберинцидент?
Прежде чем углубиться в реагирование на инциденты и управление ими, стоит сначала поговорить о том, что такое 
 киберинцидент. Обычно мы не начинаем с киберинцидента; прежде чем мы доберемся до этой точки, происходит наращивание.

#### Команда СОК 
Обычно все сначала начинается в SOC (Центре управления безопасностью). Здесь команда аналитиков следит 
 за безопасностью организации. По сути, эта команда следит за событиями в имуществе организации. Если событие 
является аномальным или неожиданным, генерируется предупреждение. Оповещения по-прежнему могут быть неверными, 
поэтому аналитики затем дополнительно изучают их. Однако, если предупреждение действительное, команда выполнит 
процедуру сортировки, чтобы определить серьезность. Если серьезность предупреждения достаточна, будет поднят инцидент.

Таким образом, SOC можно рассматривать как фильтр. Не все события доходят до инцидентов. Например, организации часто 
получают тысячи фишинговых писем каждый день. Большинство из них автоматически блокируются системами предотвращения 
вторжений, такими как спам-фильтр. Даже если пользователь будет взаимодействовать с большинством этих писем и 
запускать вредоносное ПО, например, антивирус или программное обеспечение Endpoint Detection and Response 
автоматически заблокирует это. В этих случаях будет сгенерировано оповещение, и команда SOC будет им заниматься, 
например, обновляя правила фильтрации почты или сигнатуры AV или EDR.

Инцидент, с другой стороны, — это когда на этапе сортировки мы обнаруживаем, что предупреждение может иметь 
дальнейшее влияние, и когда у нас нет всей Зараженная машина информации, необходимой для борьбы с ним. Например, 
предположим, что было сгенерировано оповещение о том, что на одном из наших серверов произошел аномальный вход в 
систему, у нас есть довольно много вопросов, на которые еще нужно ответить:

- Чей аккаунт использовался?
- Откуда произошел вход в систему?
- Где эта учетная запись использовалась до входа в систему?
- Была ли замечена какая-либо другая потенциально аномальная активность с этой учетной записью?
- Если уровень серьезности достаточен, предупреждение может быть поднято до инцидента. Позже мы обсудим различные 
  уровни реагирования на инциденты.

#### Реагирование на инциденты и управление ими

Когда серьезность оповещения достаточно высока, чтобы стать инцидентом, именно здесь обычно вступают в действие 
 функции «Реагирование на инциденты» и «Управление инцидентами». Часто эти два компонента объединяются и называются 
просто «Реагирование на инциденты». Однако у обоих из них есть отличительные особенности, которые стоит обсудить.

#### Реагирование на инциденты

Реагирование на инциденты охватывает технический аспект реагирования на инцидент. Это та часть, которая отвечает за 
 ответ на основной вопрос:

Что случилось?

Чтобы ответить на этот вопрос, группа реагирования на инциденты использует несколько методов и технологий. Эти 
расследования часто начинаются в SOC с проверки информации, предоставленной вместе с событием, вызвавшим 
предупреждение. Это может быть обеспечено одним из следующих инструментов:

EDR или AV Alert. Обычно эти инструменты создают оповещения об аномальной активности, произошедшей на определенном 
 хосте. Например, EDR может предупредить о попытках отслеживать нажатия клавиш пользователем.
Оповещение о перехвате сети. Перехваты сети предоставляют оповещения об аномальной сетевой активности. Например, 
может появиться предупреждение о том, что хост сканирует другие хосты в поместье.
Оповещение SIEM. Система управления информацией о безопасности и событиями (SIEM) может оповещать о настраиваемом 
правиле, созданном аналитиками. Например, правило невозможного путешествия, когда в учетную запись пользователя 
одновременно входят из двух разных стран.
При создании оповещения аналитику предоставляется большой объем информации. Первым шагом является изучение этой 
информации, чтобы лучше понять, что происходит. В этих системах при создании оповещения к оповещению также 
прикрепляются другие ключевые фрагменты информации. Например, в случае оповещения SIEM аналитик сможет просмотреть 
не только последние события входа в систему с учетной записью пользователя, но и историю его событий входа в 
систему за последние пару месяцев.

Однако иногда информации для оповещений недостаточно, и нам приходится собирать больше информации, чем 
предоставляется в настоящее время. Этот процесс обычно называют цифровой криминалистикой. Здесь мы проводим 
гораздо более практическое расследование, которое может включать следующее:

- Восстановление жесткого диска с зараженного хоста, чтобы выяснить, как вредоносное ПО попало туда.
- Восстановление данных из энергозависимой памяти (например, из оперативной памяти компьютера ) зараженного хоста для 
  изучения того, как работает вредоносное ПО.
- Восстановление системных и сетевых журналов с нескольких устройств, чтобы выяснить, как распространяется 
  вредоносное ПО.
 Общая цель реагирования на инциденты — попытаться понять масштаб инцидента. Если мы не совсем понимаем масштабы, 
процесс управления инцидентами не сможет предпринять адекватные шаги для закрытия инцидента. Обе крайности могут 
быть невероятно разрушительными. Если мы неправильно понимаем, что масштабы деятельности шире, чем они есть на 
самом деле, мы можем санкционировать более радикальные действия, чем требуется, что может подорвать бизнес. Если 
мы неправильно понимаем, что масштаб меньше, чем он есть, мы можем предпринять недостаточные действия против 
злоумышленника, а это означает, что инцидент не будет завершен.

#### Управление происшествиями
 Управление инцидентами охватывает процессуальный аспект работы с инцидентом. Это та часть, которая отвечает за 
 ответ на основной вопрос:

Как нам реагировать на то, что произошло?

Как только мы поймем масштаб инцидента, следующим вопросом будет то, как мы с ним справимся. Управление инцидентами 
 должно заботиться о нескольких вещах, таких как:

Оценка инцидента для точного обновления серьезности инцидента по мере поступления новой информации и привлечение 
 большего числа заинтересованных сторон для помощи в устранении инцидента, таких как профильные эксперты (SME).
Руководство действиями в случае инцидента с помощью учебных пособий.
Принятие решения о том, какие действия по сдерживанию, искоренению и восстановлению будут предприняты для 
устранения инцидента.
Принятие решения о том, какое сообщение будет отправлено внутри и снаружи, пока команда занимается инцидентом.
Документирование информации об инциденте, такой как предпринятые действия и их влияние на устранение инцидента.
Закрытие инцидента и использование информации для извлечения уроков из инцидента и улучшения будущих процессов и процедур.
 Для борьбы с инцидентом необходимы эффективное реагирование на инциденты и управление ими. Часто ошибочно полагают, 
 что для устранения инцидентов необходимы только технические навыки. Не менее важен и управленческий аспект. 
Подробнее об этом будет сказано в Задании 5.

#### Уровни реагирования и управления инцидентами
Как не все оповещения одинаковы, так и не все инциденты одинаковы. Таким образом, процесс реагирования на инциденты 
и управления ими будет различаться в зависимости от серьезности инцидента. Однако степень серьезности также не 
является статичной и может меняться, поскольку реагирование на инцидент помогает лучше понять масштаб инцидента. 
Таким образом, существуют разные уровни реагирования и управления инцидентами. Существует много разных способов 
классификации уровней, и в каждой организации они уникальны. Однако в первую очередь мы сосредоточимся на четырех 
разных уровнях этой комнаты. Мы говорим, что на каждом из этих уровней задействована другая команда, а это означает,
что в процесс вовлекаются более важные заинтересованные стороны. Более того, действия, доступные для устранения 
инцидента, становятся более мощными, но и более разрушительными. Описанные здесь уровни можно встретить в крупных 
организациях. На уровнях с первого по третий инцидентом занимается один и тот же SOC , а именно количество членов 
команды, вовлеченных в инцидент.

В данном случае мы будем использовать пример : Пользователь сообщил о фишинговом электронном письме.

#### Уровень 1: Инцидент SOC
На первом уровне они часто даже не классифицируются как инциденты. Обычно это требует чисто технического подхода. 
 На этом уровне, изучив наш пример, аналитик обнаруживает, что это изолированное событие, и поэтому просто 
обновляет правила фильтрации почты, чтобы заблокировать отправителя. Инциденты такого уровня могут происходить 
несколько раз в день, и обычно их быстро устраняют, а аналитик занимается этим самостоятельно.

 Однако в нашем примере инцидент группы компьютерной аварийной готовности (CERT) может быть вызван, если в ходе 
 расследования установлено, что электронное письмо получили несколько пользователей.

#### Уровень 2: Инцидент CERT

На втором уровне к расследованию могут быть привлечены несколько аналитиков SOC. Инцидент CERT — это тот случай, 
когда у нас еще недостаточно данных, чтобы поднять тревогу. Тем не менее, мы обеспокоены и поэтому проводим 
дополнительное расследование, чтобы определить масштаб инцидента. Обычно аналитик запрашивает помощь, и к ней 
привлекаются другие члены команды SOC . В нашем примере на этом этапе мы будем выяснять, взаимодействовал ли 
кто-либо из этих пользователей с электронным письмом. Нам также хотелось бы лучше понять, что делает электронная почта.

Если бы мы могли остановить инцидент до того, как кто-либо из пользователей взаимодействовал с электронным письмом, 
 мы бы обычно остановились на этом уровне. Однако, если мы обнаружим, что электронное письмо содержит вредоносное 
ПО и что некоторые пользователи действительно взаимодействовали с ним, мы вызовем группу реагирования на инциденты 
компьютерной безопасности (CSIRT).

#### Уровень 3: Инцидент CSIRT
На третьем уровне весь SOC находится в состоянии повышенной готовности и активно работает над устранением инцидента.
На этом этапе вся команда SOC сосредоточится на одном инциденте, чтобы справиться с ним. Аналитики и группа 
криминалистов работают над раскрытием всего масштаба инцидента, а команда управления принимает меры против 
злоумышленника, чтобы сдержать распространение вредоносного ПО, искоренить его на хостах, где оно обнаружено, и 
восстановить пострадавшие системы.

Если команде удастся остановить распространение атаки до того, как возникнут какие-либо сбои или злоумышленник 
сможет повысить свои привилегии в поместье, команда CSIRT закроет инцидент. Однако, если в результате 
расследования будет установлено, что объем инцидента шире, мы будем инициировать инцидент Группы кризисного 
управления (CMT).

#### Уровень 4: Инцидент CMT
На четвертом уровне все готово и официально начинается полномасштабный киберкризис. CMT обычно состоит из 
нескольких ключевых заинтересованных сторон бизнеса, таких как весь руководящий состав, члены юридических и 
коммуникационных групп, а также другие внешние стороны, такие как регулирующий орган или полиция. Более того, на 
этом уровне мы начинаем переходить на территорию так называемых «ядерных» действий. Вместо простых действий по 
сдерживанию, искоренению и восстановлению эта группа может санкционировать использование ядерных действий, например,
отключение всей организации, чтобы ограничить ущерб от инцидента.

#### Преимущества реагирования и управления инцидентами
Создание команды и всего необходимого для реагирования на инциденты и управления инцидентами стоит недешево. Также 
зачастую сложно доходчиво объяснить бизнесу, зачем это нужно. Однако цена инцидента может быть настолько серьезной,
что организация может полностью закрыть свои двери после одного из них. Это также не просто проблема «большой 
компании». Для сравнения: по данным Национального альянса кибербезопасности , примерно 60% небольших компаний, 
пострадавших от кибератаки, закрывают свой бизнес всего через шесть месяцев. Важность хорошего реагирования на 
инциденты и управления ими невозможно переоценить.

#### Ответить на вопросы ниже
На каком уровне (только номер) инцидента SOC будет переведен в режим повышенной готовности и отреагирует на инцидент?
3

Правильный ответ
На каком уровне (только номер) инцидент будет классифицирован как киберкризис?

4

Правильный ответ
Какой компонент (IR или IM) отвечает за ответ на вопрос: как нам реагировать на то, что произошло?

IM

Правильный ответ
Какой компонент (IR или IM) отвечает за ответ на вопрос: Что произошло?

IR

Правильный ответ
Задача 3
Различные роли во время инцидента
```commandline
Ответ не нужен
```

[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)