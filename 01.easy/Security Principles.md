[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)

# Комната [Security Principles](https://tryhackme.com/r/room/securityprinciples) 

Всего 9 заданий:
## Задание 1
Безопасность стала модным словом; каждая компания хочет заявить, что ее продукт или услуга безопасны. Но так ли это?

Прежде чем мы начнем обсуждать различные принципы безопасности, крайне важно знать противника, от которого мы 
защищаем наши активы. Вы пытаетесь помешать малышу получить доступ к вашему ноутбуку? Или вы пытаетесь защитить 
ноутбук, содержащий технические разработки стоимостью в миллионы долларов? Использование точных механизмов защиты от 
малышей и субъектов промышленного шпионажа было бы нелепо. Следовательно, знание нашего противника является 
обязательным, чтобы мы могли узнать об их атаках и начать внедрять соответствующие меры безопасности.    

Ноутбук за массивной железной дверью (как дверь сейфа), а по другую сторону — малыш. (Как будто ноутбук кладут в 
сейф размером с комнату, чтобы защитить его от милого, любознательного малыша.)  

Невозможно достичь идеальной безопасности; ни одно решение не является безопасным на 100%. Поэтому мы стараемся 
улучшить нашу позицию безопасности, чтобы нашим противникам было сложнее получить доступ. 

Целью этой комнаты является:
- Объясните функции безопасности: конфиденциальность, целостность и доступность ( ЦРУ ).
- Представить противоположность триаде безопасности ЦРУ : Раскрытие, Изменение и Уничтожение/Отрицание ( DAD ).
- Познакомить с основными концепциями моделей безопасности, такими как модель Белла-ЛаПадулы.
- Объясните принципы безопасности, такие как «глубокая защита», «нулевое доверие» и «доверяй, но проверяй».
- Внедрение стандарта ISO/IEC 19249.
- Объясните разницу между уязвимостью, угрозой и риском.
### Ответьте на вопросы ниже
Подумайте, как бы вы описали что-то как безопасное.
```commandline
Ответ не нужен
```

## Задание 2
Прежде чем мы сможем описать что-то как безопасное, нам нужно лучше рассмотреть, что составляет безопасность. Когда 
вы хотите оценить безопасность системы, вам нужно думать в терминах триады безопасности: конфиденциальность, 
целостность и доступность ( CIA ).

`Конфиденциальность` гарантирует, что доступ к данным смогут получить только те лица или получатели, которым они предназначены.
Целью `целостности` является обеспечение невозможности изменения данных; более того, мы можем обнаружить любое изменение, если оно произойдет.
`Доступность` направлена на обеспечение доступности системы или услуги при необходимости.
Продавец с чеком, добавляющий ноль к цене товара после того, как покупатель его выбрал, тем самым умножая цену на десять.

Рассмотрим триаду безопасности CIA в случае оформления заказа в интернет-магазине:
- `Конфиденциальность :` Во время онлайн-покупок вы ожидаете, что номер вашей кредитной карты будет раскрыт только 
субъекту, который обрабатывает платеж. Если вы сомневаетесь, что данные вашей кредитной карты будут раскрыты 
  ненадежной стороне, вы, скорее всего, воздержитесь от продолжения транзакции. Более того, если утечка данных 
  приведет к раскрытию персонально идентифицируемой информации, включая данные кредитных карт, компания понесет 
  огромные убытки на нескольких уровнях.   
- `Целостность :` Если после оформления заказа злоумышленник сможет изменить указанный вами адрес доставки, посылка 
  будет отправлена кому-то другому. Без целостности данных вы можете быть очень неохотно размещать заказ у этого продавца.
- `Доступность :` Чтобы разместить онлайн-заказ, вам нужно будет либо просмотреть веб-сайт магазина, либо использовать 
  его официальное приложение. Если сервис недоступен, вы не сможете просматривать продукты или размещать заказ. Если 
  вы продолжите сталкиваться с такими техническими проблемами, вы в конечном итоге можете сдаться и начать искать 
  другой интернет-магазин.  


Давайте рассмотрим ЦРУ с точки зрения его связи с записями пациентов и связанными с ними системами:
- Конфиденциальность : Согласно различным законам современных стран, поставщики медицинских услуг должны обеспечивать и поддерживать конфиденциальность медицинских записей. Следовательно, поставщики медицинских услуг могут быть привлечены к юридической ответственности, если они незаконно раскрывают медицинские записи своих пациентов.
- Целостность : Если запись пациента случайно или злонамеренно изменена, это может привести к назначению 
  неправильного лечения, что, в свою очередь, может привести к ситуации, угрожающей жизни. Следовательно, система будет бесполезной и потенциально вредной без обеспечения целостности медицинских записей.
- Доступность : когда пациент посещает клинику для наблюдения за своим состоянием здоровья, система должна быть 
  доступна. Недоступная система будет означать, что врач не сможет получить доступ к записям пациента и, следовательно, не будет знать, связаны ли какие-либо текущие симптомы с историей болезни пациента. Такая ситуация может сделать медицинскую диагностику более сложной и подверженной ошибкам.
Не обязательно делать одинаковый акцент на всех трех функциях безопасности. Примером может служить университетское объявление; хотя оно обычно не является конфиденциальным, целостность документа имеет решающее значение.

### За пределами CIA
Курьер с нелепо большим количеством коробок с пиццей и мужчина у двери, говорящий: «Я этого не заказывал».

Делая еще один шаг за пределы триады безопасности ЦРУ, мы можем подумать о:
- Подлинность : Подлинный означает не мошеннический и не поддельный. Подлинность заключается в обеспечении того, что документ/файл/данные получены из заявленного источника.
- Неотказуемость : Отказ означает отказ признавать действительность чего-либо. Неотказуемость гарантирует, что 
  первоисточник не может отрицать, что он является источником определенного документа/файла/данных. Эта характеристика незаменима для различных областей, таких как шопинг, диагностика пациентов и банковское дело.
Эти два требования тесно связаны. Необходимость отличать подлинные файлы или заказы от поддельных является обязательной. Более того, обеспечение того, чтобы другая сторона не могла отрицать, что является источником, жизненно важно для того, чтобы многие системы были пригодны для использования.

В интернет-магазинах, в зависимости от вашего бизнеса, вы можете допустить попытку доставить футболку с оплатой наличными при доставке и узнать позже, что получатель никогда не размещал такой заказ. Однако ни одна компания не может допустить отправку 1000 автомобилей, чтобы обнаружить, что заказ поддельный. В примере с заказом в магазине вы хотите подтвердить, что указанный клиент действительно разместил этот заказ; это подлинность. Более того, вы хотите убедиться, что он не сможет отрицать размещение этого заказа; это неотказуемость.

Как компания, если вы получаете заказ на поставку 1000 автомобилей, вам необходимо гарантировать подлинность этого заказа; более того, источник не должен иметь возможности отрицать размещение такого заказа. Без подлинности и неотказуемости бизнес не может вестись.

#### Паркеровская гексада
В 1998 году Донн Паркер предложил Паркеровскую гексаду — набор из шести элементов безопасности. Они следующие:
- Доступность
- Утилита
- Честность
- Подлинность
- Конфиденциальность
- Владение
Мы уже рассмотрели четыре из шести вышеперечисленных элементов. Давайте обсудим оставшиеся два элемента:

`Utility` : Utility фокусируется на полезности информации. Например, пользователь мог потерять ключ дешифрования для доступа к ноутбуку с зашифрованным хранилищем. Хотя у пользователя все еще есть ноутбук с его диском(ами), он не может получить к ним доступ. Другими словами, хотя информация все еще доступна, она находится в форме, которая бесполезна, т. е. бесполезна.
`Владение` : этот элемент безопасности требует, чтобы мы защищали информацию от несанкционированного изъятия, копирования или контроля. Например, злоумышленник может забрать резервный диск, что означает, что мы потеряем владение информацией, пока у него есть диск. В качестве альтернативы злоумышленник может успешно зашифровать наши данные с помощью программы-вымогателя; это также приведет к потере владения данными.
### Ответьте на вопросы ниже
Нажмите «Просмотр сайта» и ответьте на пять вопросов. Какой флаг вы получили в итоге?

```commandline
THM{CIA_TRIAD}
```

## Задание 3
Безопасность системы подвергается атаке одним из нескольких способов. Это может быть раскрытие секретных данных, 
изменение данных или уничтожение данных. 

- Раскрытие информации является противоположностью конфиденциальности. Другими словами, раскрытие конфиденциальных 
данных было бы атакой на конфиденциальность. 
- Изменение противоположно Целостности. Например, целостность чека необходима.
- Разрушение/Отрицание — это противоположность Доступности.


Противоположностью триады ЦРУ является триада DAD : Раскрытие, Изменение и Уничтожение.

Рассмотрим предыдущий пример историй болезни пациентов и связанных с ними систем:

- Раскрытие: Как и в большинстве современных стран, поставщики медицинских услуг должны сохранять конфиденциальность 
медицинских записей. В результате, если злоумышленнику удастся украсть некоторые из этих медицинских записей и выложить их в сеть для публичного просмотра, поставщик медицинских услуг понесет убытки из-за этой атаки по раскрытию данных.
- Изменение: Подумайте о серьезности ситуации, если злоумышленнику удастся изменить медицинские записи пациента. Эта 
  атака с изменением может привести к назначению неправильного лечения, и, следовательно, эта атака с изменением может быть опасной для жизни.
- Уничтожение/Отрицание: Рассмотрим случай, когда медицинское учреждение полностью перешло на безбумажный 
  документооборот. Если злоумышленнику удастся сделать системы баз данных недоступными, учреждение не сможет нормально функционировать. Они могут временно вернуться к бумажным документам; однако записи пациентов будут недоступны. Эта атака отрицания остановит все учреждение.

Защита от раскрытия, изменения и уничтожения/отрицания имеет первостепенное значение. Эта защита эквивалентна работе по поддержанию конфиденциальности, целостности и доступности.

Защита конфиденциальности и целостности до крайности может ограничить доступность, а увеличение доступности до крайности может привести к потере конфиденциальности и целостности. Хорошая реализация принципов безопасности требует баланса между тремя.

### Ответьте на вопросы ниже
Злоумышленнику удалось получить доступ к записям клиентов и выложить их в сеть. Что это за атака?
```commandline
Disclosure
```
Группа злоумышленников смогла обнаружить как основную, так и резервную систему электроснабжения и отключить их. В результате вся сеть была отключена. Что это за атака?
```commandline
Destruction/Denial
```

## Задание 4
Мы узнали, что триада безопасности представлена Конфиденциальностью, Целостностью и Доступностью ( CIA ). Можно 
спросить, как мы можем создать систему, которая обеспечивает одну или несколько функций безопасности? Ответ будет в 
использовании моделей безопасности. В этой задаче мы представим три основополагающие модели безопасности:   
- Модель Белла-ЛаПадулы
- Модель целостности Biba
- Модель Кларка-Уилсона
#### Модель Белла-ЛаПадулы
Модель Белла-ЛаПадулы направлена на достижение конфиденциальности путем указания трех правил:

- Простое свойство безопасности : это свойство называется «не читать»; оно гласит, что субъект на более низком уровне 
безопасности не может читать объект на более высоком уровне безопасности. Это правило предотвращает доступ к конфиденциальной информации выше авторизованного уровня.
- Свойство Star Security : Это свойство называется «no write down»; оно гласит, что субъект с более высоким уровнем 
  безопасности не может записывать в объект с более низким уровнем безопасности. Это правило предотвращает раскрытие конфиденциальной информации субъекту с более низким уровнем безопасности.
- Свойство Discretionary-Security : Это свойство использует матрицу доступа для разрешения операций чтения и записи. 
  Пример матрицы доступа показан в таблице ниже и используется в сочетании с первыми двумя свойствами.
 
Первые два свойства можно обобщить как «записать, прочитать». Вы можете делиться конфиденциальной информацией с людьми с более высоким уровнем допуска к секретной информации (записать), и вы можете получать конфиденциальную информацию от людей с более низким уровнем допуска к секретной информации (прочитать).

Модель Белла-ЛаПадулы имеет определенные ограничения. Например, она не была разработана для обработки обмена файлами.

#### Модель Биба
Модель Биба направлена на достижение целостности путем указания двух основных правил:

- Свойство простой целостности : это свойство называется «невозможность чтения»; субъект с более высокой степенью 
целостности не должен считывать данные с объекта с более низкой степенью целостности.
- Свойство целостности звезды : это свойство называется «без записи»; субъект с более низкой степенью целостности не 
  должен записывать данные в объект с более высокой степенью целостности.
Эти два свойства можно обобщить как «прочитай, запиши». Это правило противоречит модели Белла-ЛаПадулы, и это не должно удивлять, поскольку одно касается конфиденциальности, а другое — целостности.

Модель Biba страдает от различных ограничений. Одним из примеров является то, что она не обрабатывает внутренние угрозы (инсайдерскую угрозу).

#### Модель Кларка-Уилсона
Модель Кларка-Уилсона также направлена на достижение целостности с помощью следующих концепций:

- Ограниченный элемент данных (CDI) : это тип данных, целостность которого мы хотим сохранить.
- Неограниченный элемент данных (UDI) : относится ко всем типам данных за пределами CDI, таким как пользовательский и 
  системный ввод.
- Процедуры преобразования (TP) : эти процедуры представляют собой запрограммированные операции, такие как чтение и 
  запись, и должны поддерживать целостность CDI.
- Процедуры проверки целостности (IVP) : эти процедуры проверяют и гарантируют действительность CDI.
Мы рассмотрели только три модели безопасности. Читатель может изучить множество дополнительных моделей безопасности. 


Вот некоторые примеры: 
- Модель Брюэра и Нэша
- Модель Гогена-Месегера
- модель Сазерленда
- Модель Грэхема-Деннинга
- Модель Харрисона-Руццо-Ульмана
### Ответьте на вопросы ниже
Нажмите «Просмотр сайта» и ответьте на четыре вопроса. Какой флаг вы получили в конце?

```commandline
THM{SECURITY_MODELS}
```

## Задание 5
Глубокоэшелонированная защита подразумевает создание системы безопасности, состоящей из нескольких уровней; поэтому ее также называют многоуровневой безопасностью.

Рассмотрим следующую аналогию: у вас есть запертый ящик, в котором вы храните важные документы и дорогие вещи. Ящик заперт; однако, хотите ли вы, чтобы этот замок был единственным, что стоит между вором и вашими дорогими вещами? Если мы думаем о многоуровневой безопасности, мы бы предпочли, чтобы ящик был заперт, соответствующая комната была заперта, главная дверь квартиры была заперта, ворота здания были заперты, и вы, возможно, даже захотите добавить несколько камер видеонаблюдения по пути. Хотя эти несколько уровней безопасности не могут остановить каждого вора, они заблокируют большинство из них и замедлят остальных.

### Ответьте на вопросы ниже
Обязательно прочтите вышеизложенное.
```commandline
Ответ не нужен
```
## Задание 6
Международная организация по стандартизации (ISO) и Международная электротехническая комиссия (IEC) создали ISO/IEC 19249. В этой задаче мы кратко рассмотрим ISO/IEC 19249:2017 Информационные технологии. Методы обеспечения безопасности. Каталог принципов архитектуры и проектирования для защищенных продуктов, систем и приложений . Цель состоит в том, чтобы лучше понять, чему будут обучать международные организации в отношении принципов обеспечения безопасности.

#### В стандарте ISO/IEC 19249 перечислены пять архитектурных принципов:

- Разделение доменов : каждый набор связанных компонентов группируется как единое целое; компонентами могут быть 
приложения, данные или другие ресурсы. У каждого субъекта будет свой собственный домен и ему будет назначен общий набор атрибутов безопасности. Например, рассмотрим уровни привилегий процессора x86: ядро ​​операционной системы может работать в кольце 0 (наиболее привилегированный уровень). Напротив, приложения пользовательского режима могут работать в кольце 3 (наименее привилегированный уровень). Разделение доменов включено в модель Гогена-Месегера.
- Слои : Когда система структурирована на многих абстрактных уровнях или слоях, становится возможным навязывать 
  политики безопасности на разных уровнях; более того, было бы возможно проверять работу. Давайте рассмотрим модель OSI (взаимодействие открытых систем) с ее семью уровнями в сети. Каждый уровень в модели OSI предоставляет определенные услуги уровню, расположенному выше. Такое наложение слоев позволяет навязывать политики безопасности и легко проверять, что система работает так, как задумано. Еще один пример из мира программирования — дисковые операции; программист обычно использует функции чтения и записи на диск, предоставляемые выбранным высокоуровневым языком программирования. Язык программирования скрывает низкоуровневые системные вызовы и представляет их как более удобные для пользователя методы. Слои относятся к глубокоэшелонированной защите.
- Инкапсуляция : в объектно-ориентированном программировании (ООП) мы скрываем низкоуровневые реализации и 
  предотвращаем прямое манипулирование данными в объекте, предоставляя специальные методы для этой цели. Например, если у вас есть объект часов, вы предоставляете метод increment()вместо того, чтобы предоставлять пользователю прямой доступ к secondsпеременной. Цель состоит в том, чтобы предотвратить недопустимые значения для ваших переменных. Аналогично, в более крупных системах вы используете (или даже проектируете) надлежащий интерфейс прикладного программирования ( API ), который ваше приложение будет использовать для доступа к базе данных.
- Избыточность : этот принцип обеспечивает доступность и целостность. Существует множество примеров, связанных с 
  избыточностью. Рассмотрим случай аппаратного сервера с двумя встроенными блоками питания: если один блок питания выходит из строя, система продолжает функционировать. Рассмотрим конфигурацию RAID 5 с тремя дисками: если один диск выходит из строя, данные остаются доступными с использованием оставшихся двух дисков. Более того, если данные неправильно изменены на одном из дисков, это будет обнаружено с помощью четности, что гарантирует целостность данных.
- Виртуализация : С появлением облачных сервисов виртуализация стала более распространенной и популярной. Концепция 
  виртуализации заключается в совместном использовании одного набора оборудования несколькими операционными системами. Виртуализация обеспечивает возможности песочницы, которые улучшают границы безопасности, обеспечивают безопасную детонацию и наблюдение за вредоносными программами.
#### Стандарт ISO/IEC 19249 устанавливает пять принципов проектирования :

- Наименьшие привилегии : Вы также можете неформально сформулировать это как «основание необходимости» или «основание 
необходимости знать», отвечая на вопрос «кто может получить доступ к чему?» Принцип наименьших привилегий учит, что вы должны предоставить наименьшее количество разрешений для кого-либо, чтобы выполнить его задачу, и ничего более. Например, если пользователю необходимо иметь возможность просматривать документ, вы должны предоставить ему права на чтение без прав на запись.
- Минимизация поверхности атаки : у каждой системы есть уязвимости, которые злоумышленник может использовать для 
  компрометации системы. Некоторые уязвимости известны, а другие еще не обнаружены. Эти уязвимости представляют собой риски, которые мы должны стремиться минимизировать. Например, на одном из шагов по укреплению системы Linux мы отключим любую службу, которая нам не нужна.
- Централизованная проверка параметров : многие угрозы возникают из-за того, что система получает входные данные, 
  особенно от пользователей. Недействительные входные данные могут использоваться для эксплуатации уязвимостей системы, таких как отказ в обслуживании и удаленное выполнение кода. Поэтому проверка параметров является необходимым шагом для обеспечения правильного состояния системы. Учитывая количество параметров, обрабатываемых системой, проверка параметров должна быть централизована в пределах одной библиотеки или системы.
- Централизованные службы общей безопасности : как принцип безопасности, мы должны стремиться централизовать все 
  службы безопасности. Например, мы бы создали централизованный сервер для аутентификации. Конечно, вы могли бы принять надлежащие меры для обеспечения доступности и предотвращения создания единой точки отказа.
- Подготовка к обработке ошибок и исключений : всякий раз, когда мы создаем систему, мы должны учитывать, что ошибки 
  и исключения происходят и будут происходить. Например, в приложении для покупок клиент может попытаться разместить заказ на отсутствующий товар. База данных может перегрузиться и перестать отвечать на веб-приложение. Этот принцип учит, что системы должны быть спроектированы так, чтобы быть отказоустойчивыми; например, если брандмауэр выходит из строя, он должен блокировать весь трафик вместо того, чтобы разрешать его. Более того, мы должны быть осторожны, чтобы сообщения об ошибках не приводили к утечке информации, которую мы считаем конфиденциальной, например, к сбросу содержимого памяти, содержащего информацию, связанную с другими клиентами.
В следующих вопросах ссылайтесь на пять принципов проектирования, изложенных выше в стандарте ISO/IEC 19249. В 
  качестве ответа укажите число от 1 до 5 в зависимости от номера принципа проектирования. 

### Ответьте на вопросы ниже
Какой принцип вы применяете при отключении незащищенного сервера, не имеющего решающего значения для бизнеса?
```commandline
2
```
Ваша компания наняла нового торгового представителя. Какой принцип они применяют, когда говорят вам предоставить им 
доступ только к продуктам и ценам компании? 
```commandline
1
```
Читая код банкомата, вы заметили большой кусок кода для обработки непредвиденных ситуаций, таких как отключение сети 
и отключение питания. Какой принцип они применяют? 
```commandline
5
```

## Задание 7
Доверие — очень сложная тема; в действительности мы не можем функционировать без доверия. Если кто-то подумает, что поставщик ноутбука установил шпионское ПО на ноутбук, он, скорее всего, в конечном итоге перестроит систему. Если кто-то не доверяет поставщику оборудования, он полностью прекратит его использовать. Если мы думаем о доверии на уровне бизнеса, все становится только сложнее; однако нам нужны некоторые руководящие принципы безопасности. Два принципа безопасности, которые представляют для нас интерес в отношении доверия:

- Доверяй, но проверяй
- Нулевое доверие


`Доверяй, но проверяй :` этот принцип учит, что мы всегда должны проверять, даже если доверяем сущности и ее поведению. Сущность может быть пользователем или системой. Проверка обычно требует настройки надлежащих механизмов регистрации; проверка означает просмотр журналов, чтобы убедиться, что все нормально. В действительности невозможно проверить все; просто подумайте о работе, которая требуется для проверки всех действий, предпринимаемых одной сущностью, например, интернет-страниц, просматриваемых одним пользователем. Для этого требуются автоматизированные механизмы безопасности, такие как прокси-сервер, системы обнаружения и предотвращения вторжений.

`Zero Trust :` этот принцип рассматривает доверие как уязвимость и, следовательно, он обслуживает угрозы, связанные с инсайдерами. Рассмотрев доверие как уязвимость, нулевое доверие пытается устранить ее. Он косвенно учит: «никогда не доверяй, всегда проверяй». Другими словами, каждая сущность считается враждебной, пока не доказано обратное. Zero Trust не предоставляет доверия устройству на основе его местоположения или владельца. Этот подход контрастирует со старыми моделями, которые доверяли внутренним сетям или корпоративным устройствам. Перед доступом к любому ресурсу требуется аутентификация и авторизация. В результате, если произойдет какое-либо нарушение, ущерб будет более ограниченным, если будет реализована архитектура нулевого доверия.

Микросегментация — одна из реализаций Zero Trust. Она относится к проектированию, в котором сегмент сети может быть размером с один хост. Более того, для связи между сегментами требуется аутентификация, проверки списков контроля доступа и другие требования безопасности.

Существует предел тому, насколько широко мы можем применять модель нулевого доверия без негативного влияния на бизнес; однако это не означает, что мы не должны ее применять, пока это возможно.

### Ответьте на вопросы ниже
Обязательно прочтите вышеизложенное.

```commandline
Ответ не нужен
```

## Задание 8
Есть три термина, которые нам следует принять во внимание, чтобы избежать путаницы.

- Уязвимость : Уязвимый означает подверженный атаке или повреждению. В информационной безопасности уязвимость — это 
слабость.
- Угроза : Угроза — это потенциальная опасность, связанная с данной слабостью или уязвимостью.
- Риск : Риск связан с вероятностью того, что злоумышленник воспользуется уязвимостью и последующее влияние на бизнес.


Вдали от информационных систем, выставочный зал с дверями и окнами из стандартного стекла страдает от слабости или уязвимости из-за природы стекла. Следовательно, существует угроза того, что стеклянные двери и окна могут быть разбиты. Владельцы выставочного зала должны учитывать риск , т. е. вероятность того, что стеклянная дверь или окно будут разбиты, и вытекающее из этого влияние на бизнес.

Рассмотрим еще один пример, напрямую связанный с информационными системами. Вы работаете в больнице, которая использует определенную систему базы данных для хранения всех медицинских записей. Однажды вы следите за последними новостями по безопасности и узнаете, что используемая система базы данных не только уязвима, но и был выпущен рабочий код эксплойта для проверки концепции; выпущенный код эксплойта указывает на реальность угрозы. Зная это, вы должны оценить возникающий риск и решить, что делать дальше.

Мы подробно рассмотрим угрозы и риски в отдельном зале.

### Ответьте на вопросы ниже
Обязательно прочтите вышеизложенное.
```commandline
Ответ не нужен
```

## Задание 9
В этой комнате были рассмотрены различные принципы и концепции, связанные с безопасностью. К настоящему моменту вы должны быть хорошо знакомы с CIA и DAD и другими терминами, такими как подлинность, отказ, уязвимость, угроза и риск. Мы рассмотрели три модели безопасности и ISO/IEC 19249. Мы рассмотрели различные принципы безопасности, такие как глубокая защита, доверие, но проверка и нулевое доверие.

Наконец, стоит упомянуть модель общей ответственности, особенно с учетом возросшей зависимости от облачных сервисов. Для обеспечения надлежащей безопасности требуются различные аспекты. Они включают в себя оборудование, сетевую инфраструктуру, операционные системы, приложения и т. д. Однако клиенты, использующие облачные сервисы, имеют разные уровни доступа в зависимости от используемых ими облачных сервисов. Например, пользователь инфраструктуры как услуги (IaaS) имеет полный контроль (и ответственность) над операционной системой.

С другой стороны, пользователь программного обеспечения как услуги ( SaaS ) не имеет прямого доступа к базовой операционной системе. Следовательно, обеспечение безопасности в облачной среде требует, чтобы и поставщик облачных услуг, и пользователь выполняли свои части. Модель общей ответственности — это фреймворк безопасности облака, гарантирующий, что каждая сторона осознает свою ответственность.

Закончив изучение раздела «Принципы безопасности», вы можете перейти в раздел «Введение в криптографию».

### Ответьте на вопросы ниже
Обязательно запишите все ключевые термины и сокращения, которые мы рассмотрели в этой комнате.
```commandline
Ответ не нужен
```
[>> вернуться на главную страницу](https://github.com/BEPb/tryhackme/blob/master/README.md)