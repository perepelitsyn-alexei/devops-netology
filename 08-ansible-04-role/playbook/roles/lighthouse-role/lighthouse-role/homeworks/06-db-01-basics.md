# Домашнее задание к занятию "1. Типы и структура СУБД"

## Задача 1

Архитектор ПО решил проконсультироваться у вас, какой тип БД 
лучше выбрать для хранения определенных данных.

Он вам предоставил следующие типы сущностей, которые нужно будет хранить в БД:

- Электронные чеки в json виде

```
Документо-ориентированые БД, например, MongoDB, 
т.к. документы в ней хранятся в JSON 
или даже PostgreSQL в NoSQL режиме с JSONB

```

- Склады и автомобильные дороги для логистической компании
```
Здесь подходит графовый тип СУБД.
Адреса и названия складов представляют из себя узлы, а дороги, по которым происходит перемещение между этими складами,
представляют ребра графовой структуры.
один из популярных вариантов такой БД - Neo4j. 

Однако можно применять и реляционные решения,
например популярная программа "АвтоПеревозки АвтоСофт" использует Microsoft SQL, что и неудивительно, 
решения от Microsoft самые распространённые и популярные,
ведь можно использовать тот же Microsoft Access из офиссного пакета.
```
- Генеалогические деревья

```
Реляционные СУБД, т.к. хорошо структурируется в табличную форму с предопределенной схемой данных.
Для генеалогических данных используют специальный формат хранения данных GEDCOM.
Например популярный проект Webtrees - ваше семейное дерево в интернете использует MySQL. 
коммерческая российская программа для работы с генеалогической информацией использует SQLite.
```
- Кэш идентификаторов клиентов с ограниченным временем жизни для движка аутенфикации
```
БД вида ключ-значение, например Redis или Memcached
```

- Отношения клиент-покупка для интернет-магазина

```
В разработке сайтов интернет магазинов обычно используют реляционные решения, если попроще то SQLite,
если посерьёзней проект то тот же PostgreSQL будет хорошим выбором
```


## Задача 2

Вы создали распределенное высоконагруженное приложение и хотите классифицировать его согласно 
CAP-теореме. Какой классификации по CAP-теореме соответствует ваша система, если 
(каждый пункт - это отдельная реализация вашей системы и для каждого пункта надо привести классификацию):

- Данные записываются на все узлы с задержкой до часа (асинхронная запись)
```
AP (данные обновляются с задержкой, нет согласованности с последними изменениями)
PA/EL
```

- При сетевых сбоях, система может разделиться на 2 раздельных кластера
```
AP (вроде раз происходят сетевые сбои, то можно сказать что проблема с доступоностью, то есть CP,
но возможно имеется в виду что просто нет связи между двумя кластерами, тогда данные не согласованы, в этом случае AP)
PA/EC - при наличии сетевого разделения системы ставка делается на доступность, а при отсутствии распределения – на консистентность.
вариант PA/EL тоже может иметь здесь место при упоре на скорость ответа без разделения системы
```

- Система может не прислать корректный ответ или сбросить соединение

```
CP (здесь явно проблема с доступностью)
PC/EC или PC/EL
```

## Задача 3

Могут ли в одной системе сочетаться принципы BASE и ACID? Почему?
```
Не могут, потому что их основные принципы противоречат друг другу. BASE имеет приоритет высокой производительности
в ущерб согласованности данных.
Главное разногласие в требовании согласованности.
ACID требует немедленной согласованности, BASE согласованности в какой-то момент времени в будущем...
```

## Задача 4

Вам дали задачу написать системное решение, основой которого бы послужили:

- фиксация некоторых значений с временем жизни
- реакция на истечение таймаута

Вы слышали о key-value хранилище, которое имеет механизм Pub/Sub. 
Что это за система? Какие минусы выбора данной системы?

```
Под описание подходит Redis. Redis это key-value хранилище, имеет механизм
Pub/Sub и TTL с возможностью реакции на его истечение,
в Redis можно удалять ключи в автоматическом режиме устанавливая значение таймаута на ключи.
минусы Redis:
- Высокие требования к оперативной памяти сервера
- Консистентность данных - в случае отказа сервера данные из оперативной памяти будут утеряны
  и сохранятся только данные с последней синхронизации с диском
- Отсутствует разграничение прав доступа по пользователям.
- Отсутствует поддержка языка SQL
- Экземпляр БД не маштабируется
- Работает только на одном ядре процессора в однопоточном режиме
```