## Задача 1

- Опишите своими словами основные преимущества применения на практике IaaC паттернов.

```
Сокращение затрат, скорость и уменьшение рисков.
Уменьшение расходов относится не только к финансовой составляющей, но и к количеству времени, затрачиваемого на рутинные операции. 

Принципы IaC позволяют не фокусироваться на рутине, а заниматься более важными задачами. 
Автоматизация инфраструктуры позволяет эффективнее использовать существующие ресурсы.
Также автоматизация позволяет минимизировать риск возникновения человеческой ошибки. 

Масштабируемость и стандартизация - IаaC предоставляет стабильные среды быстро и на должном уровне. 

Безопасность и документация - если за провизионирование всех вычислительных, сетевых и служб хранения отвечает код, они каждый раз будут развертываться одинаково.

IаaC также служит некой формой документации о правильном способе создания инфраструктуры и страховкой.

Поскольку код можно версионировать, IaаC позволяет документировать, регистрировать и отслеживать каждое изменение конфигурации вашего сервера.

Восстановление в аварийных ситуациях.
IaаC — чрезвычайно эффективный способ отслеживания вашей инфраструктуры и повторного развертывания последнего работоспособного состояния после сбоя или катастрофы любого рода. 
```
- Какой из принципов IaaC является основополагающим?

```
Идемпотентность - свойство объекта или операции при повторном применении операции к объекту давать тот же результат,
что и при первом.
```

## Задача 2

- Чем Ansible выгодно отличается от других систем управление конфигурациями?
```
тем что на сервера не нужно устанавливать агенты
```

- Какой, на ваш взгляд, метод работы систем конфигурации более надёжный push или pull?

## Задача 3

Установить на личный компьютер:

- VirtualBox
- Vagrant
- Ansible

```
vagrant version
Installed Version: 2.3.3.dev
```

```
VBoxManage --version
6.1.38_Ubuntur153438
```

```
 ansible --version
ansible [core 2.13.7]
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/home/monztro/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  ansible collection location = /home/monztro/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/bin/ansible
  python version = 3.10.6 (main, Nov 14 2022, 16:10:14) [GCC 11.3.0]
  jinja version = 3.0.3
  libyaml = True
```

