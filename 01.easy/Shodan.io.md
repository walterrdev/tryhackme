[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)

# Комната [Shodan.io](https://tryhackme.com/r/room/shodan) 

Всего 7 заданий:
## Задание 1
Прочитайте запись в блоге для более подробного  объяснения. 

https://skerritt.blog/shodan/

Комната создана  https://twitter.com/bee_sec_san  на основе  этой записи в блоге.

Shodan.io — поисковая система для Интернета вещей.

Вы когда-нибудь задумывались, как найти общедоступные камеры видеонаблюдения? А как насчет того, чтобы узнать, 
сколько Pi-Holes находятся в открытом доступе? Или подключена ли ваша офисная кофемашина к Интернету?
#### Shodan.io — вот ответ!
Shodan сканирует весь Интернет и индексирует службы, запущенные на каждом IP-адресе.
Примечание: если вы следуете нашим инструкциям, вам понадобится премиум-аккаунт Shodan.

#### Поиск услуг
Допустим, мы проводим пентест компании и хотим выяснить, какие службы работают на одном из ее серверов.
Нам нужно захватить их IP-адрес. Мы можем сделать это с помощью  ping.
Мы можем выполнить ping-запрос на tryhackme.com, и ответ на ping сообщит нам его IP-адрес.
Затем, как только мы это сделаем, мы вводим IP-адрес в Shodan и получаем:
Мы видим, что TryHackMe работает на Cloudflare в США, и у них открыто много портов.
Cloudflare выступает в качестве прокси-сервера между TryHackMe и их реальными серверами. Если бы мы проводили 
пентестинг крупной компании, это было бы бесполезно. Нам нужен какой-то способ получить их IP-адреса.
Мы можем сделать это, используя номера автономных систем.

Номера автономных систем
Номер автономной системы (ASN) — это глобальный идентификатор диапазона IP-адресов. Если вы огромная компания, как 
Google, у вас, скорее всего, будет свой собственный ASN для всех IP-адресов, которыми вы владеете.
Мы можем ввести IP-адрес в инструмент поиска ASN, например https://asnlookup.com/ ,
Что говорит нам о том, что у них ASN AS14061.

Tryhackme не является мега-большой корпорацией, поэтому у них нет собственного ASN. Когда мы гуглим AS14061, мы 
видим, что это номер DigitalOcean ASN. 
На Shodan.io мы можем искать с помощью фильтра ASN. Фильтр,  ASN:[number] где number — это номер, который мы 
получили ранее, AS14061. 

Сделав это, мы можем увидеть целый ряд (фактически 6,2 миллиона веб-сайтов), которые находятся в этой единственной ASN!
https://www.shodan.io/search?query=asn%3AAS14061
Знание ASN полезно, поскольку мы можем искать в Shodan такие вещи, как кофеварки или уязвимые компьютеры в пределах 
нашего ASN, о которых мы знаем (если мы крупная компания), что они находятся в нашей сети. 

Начиная
Пора приступить к работе! Если вы застряли, посмотрите предыдущее задание, оно вам поможет! :)

Баннеры
Чтобы максимально эффективно использовать Shodan, важно понимать синтаксис поисковых запросов.

Устройства запускают службы, а Shodan хранит информацию о них. Информация хранится в  баннере . Это самая 
фундаментальная часть Shodan. 

Пример баннера выглядит так:
```commandline
{
		"data": "Moxa Nport Device",
		"Status": "Authentication disabled",
		"Name": "NP5232I_4728",
		"MAC": "00:90:e8:47:10:2d",
		"ip_str": "46.252.132.235",
		"port": 4800,
		"org": "Starhub Mobile",
		"location": {
				"country_code": "SG"
		}
 }
```

Мы рассматриваем выходные данные одного порта, которые включают информацию об IP-адресе и сведения об аутентификации.

За пределами API вы этого не увидите , поэтому мы не будем в это углубляться.

### Ответьте на вопросы ниже
Перейти на Shodan.io
```commandline
Ответ не нужен
```

## Задание 2
Фильтры
На домашней странице Shodan.io мы можем нажать «исследовать», чтобы просмотреть наиболее популярные поисковые 
запросы. Самый популярный из них — веб-камеры. 
https://www.shodan.io/explore
Примечание: это серая зона. Законно просматривать общедоступную веб-камеру, незаконно пытаться взломать защищенную 
паролем. Используйте мозг и изучите законы вашей страны! 
Одним из наиболее популярных поисковых запросов является поиск баз данных MYSQL.
https://www.shodan.io/search?query=product%3AMySQL
Если мы посмотрим на поиск, то увидим, что это еще один фильтр.
продукт:MySQL
Зная это, мы фактически можем объединить 2 поиска в 1.
Давайте попробуем найти несколько серверов MYSQL на ASN TryHackMe.
Мы используем этот поисковый запрос

asn:AS14061 продукт:MySQL

И та-дам! У нас есть серверы MYSQL на TryHackMe ASN (который на самом деле является DigitalOcean ASN).
https://www.shodan.io/search?query=asn%3AAS14061+product%3AMySQL
Shodan имеет много мощных фильтров. Мой любимый — фильтр vuln, который позволяет нам искать IP-адреса, уязвимые для эксплойта.
Допустим, мы хотим найти IP-адреса, уязвимые для Eternal Blue:
уязвимость:ms17-010
Однако эта функция доступна только для академических и бизнес-пользователей, чтобы предотвратить злоумышленников от 
ее использования! 

Город Страна Гео (координаты) Имя хоста сеть (на основе IP / CIDR) ОС (найти операционные системы) порт до/после 
(временные рамки) 

API
У Shodan.io есть API ! Для него требуется учетная запись, поэтому я не буду говорить об этом здесь.
Если вы хотите изучить API Shodan , я написал пост в блоге о поиске Pi-Holes с его помощью:
https://github.com/beesecurity/How-I-Hacked-Your-Pi-Hole/blob/master/README.md
API позволяет нам программно искать Shodan и получать в ответ список IP-адресов. Если мы компания, мы можем написать 
скрипт для проверки наших IP-адресов на предмет уязвимости каких-либо из них. 
PS: Вы можете автоматически фильтровать по Shodan, нажимая на элементы в левой боковой панели!

### Ответьте на вопросы ниже
Как найти эксплойты Eternal Blue на Shodan?
```commandline
vuln:ms17-010
```

## Задание 3
Учимся фильтровать с помощью Google. Полезный совет: внимательно следите за тем, о чем вас спрашивают в вопросе!

### Ответьте на вопросы ниже
Какая операционная система является лучшей для серверов MYSQL в ASN Google?    
```commandline
5.6.40-84.0-log
```
Какая страна занимает второе место по популярности среди серверов MYSQL в ASN Google?
```commandline
Netherlands
```
Какой протокол nginx более популярен в ASN от Google: Hypertext Transfer Protocol или Hypertext Transfer Protocol с SSL?
```commandline
Hypertext Transfer Protocol
```
Какой город является самым популярным согласно ASN Google?
```commandline
Kansas City
```
Какая операционная система является самой популярной в ASN Google в Лос-Анджелесе по версии Shodan?
```commandline
Debian
```
Используя верхний поиск веб-камер на странице обзора, найдите ли в ASN Google какие-либо веб-камеры? Да / нет.
```commandline
Nay
```

## Задание 4
Shodan Monitor — это приложение для мониторинга ваших устройств в вашей собственной сети. По их словам:
Отслеживайте устройства, которые вы подключили к Интернету. Настройте уведомления, запустите сканирование и получите 
полную видимость того, что вы подключили.
Раньше нам приходилось делать это с помощью их API , но теперь у нас есть это модное приложение.
Доступ к панели управления осуществляется по этой ссылке:
https://monitor.shodan.io/dashboard
Вы увидите, что он запрашивает диапазон IP-адресов.
После добавления сети мы увидим ее на панели управления.
Если нажать на шестеренку настроек, то можно увидеть ряд «сканирований», которые Shodan выполняет в отношении нашей сети.
Каждый раз, когда Shodan обнаруживает уязвимость безопасности в одной из этих категорий, он отправляет нам электронное письмо.
Если мы снова обратимся к панели управления, то увидим, что она отображает для нас некоторые данные.

В частности:
- Лучшие открытые порты (наиболее распространенные)
- Основные уязвимости (то, с чем нам нужно разобраться немедленно)
- Известные порты (необычные открытые порты)
- Потенциальные уязвимости
- Известные IP-адреса (то, что нам следует изучить более подробно).
Интересно то, что вы можете фактически контролировать сети других людей, используя это. Для bug bounties вы можете 
  сохранить список IP-адресов, и Shodan отправит вам письмо, если обнаружит какие-либо проблемы. 

Примечание: это премиум-продукт, но вы часто можете получить аккаунты Shodan за 1 доллар по специальным предложениям в Черную пятницу.

### Ответьте на вопросы ниже
Какой URL ведет на Shodan Monitor?
```commandline
https://monitor.shodan.io/dashboard
```

## Задание 5
Shodan имеет несколько прекрасных веб-страниц с Dorks, которые позволяют нам находить вещи. Их веб-страницы с 
примерами поиска содержат некоторые из них. 

Вот некоторые забавные из них:
has_screenshot:true encrypted attention
Который использует оптическое распознавание символов и удаленный рабочий стол для поиска машин, зараженных вирусом-вымогателем в Интернете. 
screenshot.label:ics
vuln:CVE-2014-0160 Подключенные к Интернету машины уязвимы для heartbleed. Примечание: поиск CVE разрешен только для академических или бизнес-подписчиков.

Атака на цепочку поставок Solar Winds с использованием Favicons:

http.favicon.hash:-1776962843

Больше Shodan Dorks вы можете найти на GitHub .

### Ответьте на вопросы ниже
Какой придурок позволяет нам находить ПК, зараженные вирусами-вымогателями?
```commandline
has_screenshot:true encrypted attention
```
## Задание 6
Расширение Shodan
У Shodan также есть расширение.
https://chrome.google.com/webstore/detail/shodan/jjalcfnidlmpjhdfepjhjbhnhkbgleap

После установки вы можете нажать на него, и он сообщит вам IP-адрес работающего веб-сервера, какие порты открыты, 
где он находится и есть ли у него какие-либо проблемы безопасности. 

Я полагаю, что это хорошее расширение для тех, кто интересуется вознаграждениями за обнаружение ошибок, поскольку 
оно позволяет быстро определить, уязвима ли система или нет, основываясь на выводе Shodan. 

PS: Это официальное изображение расширения. Извините, что оно такое размытое!

### Ответьте на вопросы ниже
Это будет полезно для вознаграждений за обнаружение ошибок!
```commandline
Ответ не нужен
```

## Задание 7
У Shodan.io есть API! Для него требуется учетная запись, поэтому я не буду говорить об этом здесь.
Если вы хотите изучить API Shodan, я написал пост в блоге о поиске Pi-Holes с его помощью:
https://github.com/beesecurity/How-I-Hacked-Your-Pi-Hole/blob/master/README.md

API позволяет нам программно искать Shodan и получать в ответ список IP-адресов. Если мы компания, мы можем написать 
скрипт для проверки наших IP-адресов на предмет уязвимости каких-либо из них. 
PS: Вы можете автоматически фильтровать по Shodan, нажимая на элементы в левой боковой панели!

### Ответьте на вопросы ниже
Прочитайте сообщение в блоге выше!
```commandline
Ответ не нужен
```
[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)