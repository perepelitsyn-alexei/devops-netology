# Домашнее задание к занятию 3. «MySQL»


## Задача 1

Используя Docker, поднимите инстанс MySQL (версию 8). Данные БД сохраните в volume.

Изучите [бэкап БД](https://github.com/netology-code/virt-homeworks/tree/virt-11/06-db-03-mysql/test_data) и 
восстановитесь из него.

Перейдите в управляющую консоль `mysql` внутри контейнера.

Используя команду `\h`, получите список управляющих команд.

Найдите команду для выдачи статуса БД и **приведите в ответе** из её вывода версию сервера БД.

Подключитесь к восстановленной БД и получите список таблиц из этой БД.

**Приведите в ответе** количество записей с `price` > 300.

В следующих заданиях мы будем продолжать работу с этим контейнером.

![01](https://github.com/perepelitsyn-alexei/devops-netology/assets/105611781/e81aed5e-d93e-4417-9cfd-770a3a3a3906)

## Задача 2

Создайте пользователя test в БД c паролем test-pass, используя:

- плагин авторизации mysql_native_password
- срок истечения пароля — 180 дней 
- количество попыток авторизации — 3 
- максимальное количество запросов в час — 100
- аттрибуты пользователя:
    - Фамилия "Pretty"
    - Имя "James".

Предоставьте привелегии пользователю `test` на операции SELECT базы `test_db`.
    
Используя таблицу INFORMATION_SCHEMA.USER_ATTRIBUTES, получите данные по пользователю `test` и 
**приведите в ответе к задаче**.

![02](https://github.com/perepelitsyn-alexei/devops-netology/assets/105611781/6cbbb287-88dd-4e22-89fe-be4f9128a0e6)

## Задача 3

Установите профилирование `SET profiling = 1`.
Изучите вывод профилирования команд `SHOW PROFILES;`.

Исследуйте, какой `engine` используется в таблице БД `test_db` и **приведите в ответе**.

Измените `engine` и **приведите время выполнения и запрос на изменения из профайлера в ответе**:
- на `MyISAM`,
- на `InnoDB`.

![03](https://github.com/perepelitsyn-alexei/devops-netology/assets/105611781/f5fbac0b-f7c4-4516-b975-8862620447c3)


## Задача 4 

Изучите файл `my.cnf` в директории /etc/mysql.

![04](https://github.com/perepelitsyn-alexei/devops-netology/assets/105611781/78e946f7-ed13-461a-a717-83c58e76e8b9)


Измените его согласно ТЗ (движок InnoDB):

- скорость IO важнее сохранности данных;
- нужна компрессия таблиц для экономии места на диске;
- размер буффера с незакомиченными транзакциями 1 Мб;
- буффер кеширования 30% от ОЗУ;
- размер файла логов операций 100 Мб.

Приведите в ответе изменённый файл `my.cnf`.

![05](https://github.com/perepelitsyn-alexei/devops-netology/assets/105611781/ec2a55ac-b11c-4c8d-89ca-5d605103a081)

---

