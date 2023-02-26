# Домашнее задание к занятию "1. Типы и структура СУБД"

## Задача 1

Архитектор ПО решил проконсультироваться у вас, какой тип БД 
лучше выбрать для хранения определенных данных.

Он вам предоставил следующие типы сущностей, которые нужно будет хранить в БД:

- Электронные чеки в json виде
```
Документо-ориентированые БД, например, MongoDB, т.к. документы в ней хранятся в JSON или даже PostgreSQL в NoSQL режиме с 
JSONB
```

- Склады и автомобильные дороги для логистической компании
```
Здесь подходит графовый тип СУБД. Адреса и названия складов представляют из себя узлы, а дороги, по которым происходит перемещение между этими складами, представляют ребра графовой структуры.
один из популярных вариантов такой БД - Neo4j. 
Однако можно применять и реляционные решения, например популярная программа "АвтоПеревозки АвтоСофт" использует Microsoft SQL, что и неудивительно, решения от Microsoft самые распространённые и популярные,
ведь можно использовать тот же Microsoft Access из офиссного пакета.
```
- Генеалогические деревья
- Кэш идентификаторов клиентов с ограниченным временем жизни для движка аутенфикации
- Отношения клиент-покупка для интернет-магазина

Выберите подходящие типы СУБД для каждой сущности и объясните свой выбор.

## Задача 2

Вы создали распределенное высоконагруженное приложение и хотите классифицировать его согласно 
CAP-теореме. Какой классификации по CAP-теореме соответствует ваша система, если 
(каждый пункт - это отдельная реализация вашей системы и для каждого пункта надо привести классификацию):

- Данные записываются на все узлы с задержкой до часа (асинхронная запись)
- При сетевых сбоях, система может разделиться на 2 раздельных кластера
- Система может не прислать корректный ответ или сбросить соединение

А согласно PACELC-теореме, как бы вы классифицировали данные реализации?

## Задача 3

Могут ли в одной системе сочетаться принципы BASE и ACID? Почему?

## Задача 4

Вам дали задачу написать системное решение, основой которого бы послужили:

- фиксация некоторых значений с временем жизни
- реакция на истечение таймаута

Вы слышали о key-value хранилище, которое имеет механизм Pub/Sub. 
Что это за система? Какие минусы выбора данной системы?

---