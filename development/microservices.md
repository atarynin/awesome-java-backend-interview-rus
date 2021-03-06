[Оглавление](../README.md)

# Microservices

- [Чем сервисная архитектура отличается от микросервисной?](#чем-сервисная-архитектура-отличается-от-микросервисной)
- [Какие есть ограничения у микросервисов? Назовите достоинства и недостатки микросервисной архитектуры.](#какие-есть-ограничения-у-микросервисов-назовите-достоинства-и-недостатки-микросервисной-архитектуры)
- [Какие вы знаете паттерны микросервисов?](#какие-вы-знаете-паттерны-микросервисов)

## Чем сервисная архитектура отличается от микросервисной?

[Сервис-ориентированная архитектура](https://en.wikipedia.org/wiki/Service-oriented_architecture) (SOA) - независимый от технологий, компаний и программных продуктов подход к разработке программного обеспечения на основе распределённых, слабосвязанных заменяемых компонентов с чётко определёнными интерфейсами и протоколами взаимодействия. Область охвата SOA — это всё предприятие, где происходит взаимодействие между приложениями. SOA делает ставку на доступ к бизнес-функциям предприятия через повторно используемые интерфейсы.

[Сервис](https://web.archive.org/web/20160819141303/http://opengroup.org/soa/source-book/soa/soa.htm) в данной архитектуре:
- представляет бизнес-логику с определённым результатом (много ответственностей, связанных единой бизнес-областью, целью, смыслом и т.п.);
- может состоять из других сервисов или зависеть от них;
- является "чёрным ящиком" для своих клиентов.
Как и все серьёзные подходы к чему-либо имеет свой [манифест](http://www.soa-manifesto.org/default_russian.html)

[Микросервисная архитектура](https://en.wikipedia.org/wiki/Microservices) (MSA) - частный случай SOA, побуждающий строить взаимодействие насколько это возможно и необходимо небольших, слабосвязанных, легко изменяемых и взаимозаменяемых компонентов (микросервисов). MSA ориентирована, в первую очередь, на структуру и компоненты отдельного приложения.

Микросервис:
- выполняет только одну достаточно элементарную и определённую функцию (Unix way - единственная ответственность);
- деплоится и разрабатывается независимо от других микросервисов;
- является независимым от других микросервисов (в том числе максимальная минимизация общего кода);
- является "чёрным ящиком" для своих клиентов.

Можно найти несколько источников, где MSA представляется как нечто новое и хорошее, а SOA - старое и умирающее. Часто это ещё и подаётся под соусом технологий. ИМХО - это больше маркетинговая туфта, чем хорошее сравнение. MSA и SOA не завязаны на технологии и не ограничивают в их использовании. Более того, оба подхода можно совмещать с пользой для бизнеса.

Подробнее:
- [Стандарты SOA](https://publications.opengroup.org/standards/soa)
- [Микросервисы, SOA и API](https://www.ibm.com/developerworks/ru/library/1601_clark-trs/index.html) на ibm с отличными картинками о различиях SOA и MSA
- [Monolith vs SOA vs MSA](https://medium.com/@leprosus/monolith-vs-soa-vs-msa-8767bfebe00) на medium
- [Microservices vs SOA](https://dzone.com/articles/microservices-vs-soa-whats-the-difference) на DZone
- [Колонка сравнения MSA и SOA](https://martinfowler.com/articles/microservices.html#MicroservicesAndSoa) на сайте Мартина Фаулера
- [SOA и MSA](https://www.opengroup.org/soa/source-book/msawp/p3.htm)

[к содержанию](#microservices)

## Какие есть ограничения у микросервисов? Назовите достоинства и недостатки микросервисной архитектуры.

Достоинства:
- Меньше кода на программный компонент (микросервис) -> проще и быстрее разрабатывать, поддерживать, тестировать, понимать, выбросить и переписать, реализовывать с помощью наиболее подходящих технологий и инструментов (в том числе на новье)
- Меньше команда -> меньше проблем и конфликтов при мёрже и совместной разработке
- Проще горизонтально масштабировать
- Быстрее и проще как внедрять, так и откатывать

Недостатки:
- Увеличение накладных расходов на взаимодействие между программными компонентами (микросервисами) - обмен между ними выполняется по сети со всем вытекающим (сериализация/десериализация, задержки и т.д.)
- Возможно появление необходимости распределённых транзакций
- Увеличение объёмов логирования и мониторинга
- Дублирование кода
- Сложнее дебажить и отлавливать ошибки
- Нужно быть готовым и способным продолжить работать, когда любой из микросервисов отвалится
- Общая сложность растёт с количеством микросервисов

Подробнее:
- На Хабре есть целый [хаб](https://habr.com/ru/hub/microservices/) на тему микросервисов. Отмечу несколько статей по вопросу: [раз](https://habr.com/ru/post/416819/), [два](https://habr.com/ru/post/427215/), [три](https://habr.com/ru/post/311208/), [четыре](https://habr.com/ru/post/303778/), [пять](https://habr.com/ru/company/raiffeisenbank/blog/427953/), [шесть](https://habr.com/ru/post/489912/) и [Смерть микросервисного безумия в 2018 году](https://habr.com/ru/company/flant/blog/347518/)
- Записка программиста [Преимущества и недостатки микросервисной архитектуры](https://eax.me/micro-service-architecture/)
- [Статья](https://en.wikipedia.org/wiki/Microservices) на Wikipedia
- [Microservices - Not A Free Lunch!](http://highscalability.com/blog/2014/4/8/microservices-not-a-free-lunch.html)
- [Микросервисы — за и против](http://devopsru.com/news/2016-05-10-microservice-trade-offs.html)
- [What are microservices?](https://raygun.com/blog/what-are-microservices/)
- [To go or not to go micro: the pros and cons of microservices](https://medium.com/@goodrebels/to-go-or-not-to-go-micro-the-pros-and-cons-of-microservices-7967418ff06)
- [Microservices in a Nutshell. Pros and Cons](https://phauer.com/2015/microservices-nutshell-pros-cons/)

Посмотреть:
- [Преимущества и недостатки микросервисной архитектуры в HeadHunter](https://www.youtube.com/watch?v=7WT_Rl6m2DU)
- [Микросервисная Архитектура: проблемы и решения](https://www.youtube.com/watch?v=GIslwdE2DWY)
- [Микросервисная архитектура](https://www.youtube.com/watch?v=wXaoKroEnp4)
- [Микросервисная архитектура, подходы и технологии](https://www.youtube.com/watch?v=FF-GZ7iipwc)

[к содержанию](#microservices)

## Какие вы знаете паттерны микросервисов?

Как и в случае с ООП-паттернами, есть [книжка](https://microservices.io/book) с одноимённым названием. Есть на русском. На Хабре есть [статья-затравочка](https://habr.com/ru/company/piter/blog/462519/) от ИД "Питер".

И есть другая книжка - [Microservice Patterns and Best Practices](https://www.packtpub.com/application-development/microservice-patterns-and-best-practices). На Medium имеется на неё [обзор](https://medium.com/@alexanderpolomodov/%D0%BE%D0%B1%D0%B7%D0%BE%D1%80-%D0%BA%D0%BD%D0%B8%D0%B3%D0%B8-microservice-patterns-and-best-practices-dce7785b9c45).

На microservices.io можно найти наглядные и интерактивные схемы паттернов микросервисной архитектуры: [тут](https://microservices.io/patterns/microservices.html) или [здесь](https://microservices.io/patterns/). Каждый блок на схемах - это ссылка на статью по данному паттерну. Строго рекомендую.

Также на Хабре есть [статья](https://habr.com/ru/company/piter/blog/275633/) по теме. Первым же комментарием к ней советуют тоже интересную книжку - [Enterprise Integration Patterns](https://www.enterpriseintegrationpatterns.com/index.html) и [список](https://www.enterpriseintegrationpatterns.com/patterns/messaging/toc.html) паттернов из неё.

[к содержанию](#microservices)