# Домашнее задание к занятию «Введение в микросервисы»

## Задача

Руководство крупного интернет-магазина, у которого постоянно растёт пользовательская база и количество заказов, рассматривает возможность переделки своей внутренней   ИТ-системы на основе микросервисов. 

Вас пригласили в качестве консультанта для оценки целесообразности перехода на микросервисную архитектуру. 

Опишите, какие выгоды может получить компания от перехода на микросервисную архитектуру и какие проблемы нужно решить в первую очередь.

---

Основной плюс микросервисов это повышение отказоустойчивости сервиса, потому что у микросервисной архитектуры нет единой точки отказа. При монолите, если он падает, то сервис полностью недоступен. Если же монолит разделить на несколько сервисов, при падении какого то одного микросервиса остальные могут не пострадать и продолжат работу в штатном режиме. К тому же современные микросервисы обычно выполнены в режиме кластера, когда упавшие поды и ноды, переподнимаются автоматически, что опять же идёт на пользу отказоустойвости и надёжности сервиса.

Так же надёжность сервиса повышается тем что при выявлении каких то проблем в работе отдельного микросервиса, например, после очередного обновления выявили какую то ошибку в програмном обеспечении, то отдельный участок сервиса проще откатить на предыдущую версию ПО, чем перезапускать весь монолит целиком.

При использовании микросервисов, когда за каждый участок отвечает отдельная команда, соответственно возникает понимание разделения ответственности, кто конкретно и за что отвечает. Повышается качество менеджмента продукта. 

Применение микросервисной архитектуры позволяет децентрализовать организацию команд разработчиков.

При разделении на микросервисы скорость доставки новых фич в ПО увеличивается, командам проще обновлять и тестировать(а также эксперементировать) отдельный микросервис чем весь монолит в целом. Процесс разработки ускоряется, становится более гибким и управляемым. 

Использование микросервисов облегчает масштабирование, поскольку можно масштабировать только необходимые компоненты.
В микросервисах удобно балансировать возможности инфраструктуры в пользу более требовательных сервисов и предоставить оставшимся минимально необходимое количество для работы. Это не только поможет системе лучше справляться с нагрузкой, но и оптимизирует использование ресурсов, сократив затраты.

___

Решение о переходе на микросервисы должно быть принято с учетом специфики бизнеса и технического задания. Переход может потребовать значительных затрат времени и ресурсов на обучение персонала и для разработки и поддержки новых процессов и инструментов. 

При переходе с монолита на микросервисную архитектуру, сначала надо спроектировать на сколько частей будет делится сервис, за каждым сервисом нужно закрепить свою команду, назначить отвественных. Организовать коммуникацию между комендами. Нужно продумать как именно процесс распила монолита будет происходить, обычно монолит "пилят" по частям постепенно, стараются чтобы процесс перехода не отражался на работе сервиса и был незаметен для пользователей. 

При переходе на микросервисы усложняется система мониторинга, поэтому нужно правильно спланировать и организовать мониторинг всей инфраструктуры.

Так же придётся увеличить работу по безопасности. В монолите все данные передются через один процес, у каждого микросервиса же свой процесс и им нужно обмениваться между собой данными, что повышает риски утечки данных при передаче. Потребуется принять дополнительные меры для обеспечения безопасности, чтобы предотвратить утечки и несанкционированный доступ к данным.

Придётся решать проблемы идемпотентности данных. В распределенных системах, где разные процессы управляют состоянием в разных базах данных, возникают потенциальные проблемы с согласованностью данных.

Структура микросервисного приложения намного сложнее, чем монолитного, его обслуживание требует больше ресурсов и знаний в сфере DevOps.