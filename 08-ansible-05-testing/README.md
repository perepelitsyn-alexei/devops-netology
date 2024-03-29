# Домашнее задание к занятию 5 «Тестирование roles»

## Основная часть

Ваша цель — настроить тестирование ваших ролей. 

Задача — сделать сценарии тестирования для vector. 

Ожидаемый результат — все сценарии успешно проходят тестирование ролей.

### Molecule

1. Запустите  `molecule test -s centos_7` внутри корневой директории clickhouse-role, посмотрите на вывод команды. Данная команда может отработать с ошибками, это нормально. Наша цель - посмотреть как другие в реальном мире используют молекулу.

![01](https://github.com/perepelitsyn-alexei/devops-netology/assets/105611781/041ec389-ea13-4c99-8b95-7f7550c978ef)


2. Перейдите в каталог с ролью vector-role и создайте сценарий тестирования по умолчанию при помощи `molecule init scenario --driver-name docker`.

![02](https://github.com/perepelitsyn-alexei/devops-netology/assets/105611781/66b275be-085c-4821-8db7-eeff7dc4797a)

3. Добавьте несколько разных дистрибутивов (centos:8, ubuntu:latest) для инстансов и протестируйте роль, исправьте найденные ошибки, если они есть.

![03](https://github.com/perepelitsyn-alexei/devops-netology/assets/105611781/820b85a8-5c4a-426d-a637-5d8209240616)

4. Добавьте несколько assert в verify.yml-файл для  проверки работоспособности vector-role (проверка, что конфиг валидный, проверка успешности запуска и др.). 
```
---
# This is an example playbook to execute Ansible tests.

- name: Verify
  hosts: all
  gather_facts: false
  tasks:
  - name: Example assertion
    assert:
      that: true
  - name: Get Vector version
  ansible.builtin.command: "vector --version"
  changed_when: false
  register: vector_version
  - name: Assert Vector instalation
    assert:
      that: "'{{ vector_version.rc }}' == '0'"
  - name: Validation Vector configuration
    ansible.builtin.command: "vector validate --no-environment --config-yaml {{ vector_config_path }}"
    changed_when: false
    register: vector_validate
  - name: Assert Vector validate config
    assert:
      that: "'{{ vector_validate.rc }}' == '0'"
  - name: Check Vector status
    shell: ps aux | grep [v]ector
```

5. Запустите тестирование роли повторно и проверьте, что оно прошло успешно.
6. Добавьте новый тег на коммит с рабочим сценарием в соответствии с семантическим версионированием.

[tag 0.0.2](https://github.com/perepelitsyn-alexei/devops-netology/tree/0.0.2/08-ansible-05-testing)

### Tox

1. Добавьте в директорию с vector-role файлы из [директории](./example).
2. Запустите `docker run --privileged=True -v <path_to_repo>:/opt/vector-role -w /opt/vector-role -it aragast/netology:latest /bin/bash`, где path_to_repo — путь до корня репозитория с vector-role на вашей файловой системе.
3. Внутри контейнера выполните команду `tox`, посмотрите на вывод.
5. Создайте облегчённый сценарий для `molecule` с драйвером `molecule_podman`. Проверьте его на исполнимость.
6. Пропишите правильную команду в `tox.ini`, чтобы запускался облегчённый сценарий.
8. Запустите команду `tox`. Убедитесь, что всё отработало успешно.

![tox](https://github.com/perepelitsyn-alexei/devops-netology/assets/105611781/8367a228-0f41-4c8e-9dd9-745a1745d4e2)

9. Добавьте новый тег на коммит с рабочим сценарием в соответствии с семантическим версионированием.

[tag 0.0.3](https://github.com/perepelitsyn-alexei/devops-netology/blob/0.0.3/08-ansible-05-testing/roles/vector-role/molecule/podman/molecule.yml)

После выполнения у вас должно получится два сценария molecule и один tox.ini файл в репозитории. Не забудьте указать в ответе теги решений Tox и Molecule заданий. В качестве решения пришлите ссылку на  ваш репозиторий и скриншоты этапов выполнения задания.

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.
