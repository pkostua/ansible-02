# Решение домашнего задания к занятию 2 «Работа с Playbook»
https://github.com/netology-code/mnt-homeworks/tree/MNT-video/08-ansible-02-playbook

### О репозитории
Репозиторий состоит из двух частей  
1. terraform -  Готовит окружение и формирует файл инвентаря, является вспомогательным иснтрументом и не рассматривается в рамках этой работы  
2. ansible - производит установку Clickhouse и Vector  

#### Описание playbook'a

Этот playbook предназначен для установки и настройки Clickhouse и Vector. Он включает в себя следующие задачи:

* Установка Clickhouse с помощью RPM-пакетов.
* Создание базы данных в Clickhouse.
* Установка и настройка Vector.
* Создание каталога конфигурации Vector.
* Создание файла конфигурации Vector из шаблона.
* Запуск Vector в фоне.

#### Требования

* Ansible 2.9 или выше.


#### Управление playbook'ом

Чтобы управлять playbook'ом, используйте следующие команды:

Используйте тэг vector для установки Vector
```
ansible-playbook site.yml -i inventory/prod.yml --tags="vector"
```

Используйте тэг clickhouse для установки Clickhouse
```
ansible-playbook site.yml -i inventory/prod.yml --tags="clickhouse"
```

Запуститте без тегов для установки Vector и Clickhouse
```
ansible-playbook site.yml -i inventory/prod.yml 
```

#### Примечания

*  playbook предполагает, что пакеты RPM Clickhouse доступны по умолчанию в репозиториях yum. Если это не так, может потребоваться добавить дополнительные репозитории или настроить менеджер пакетов вручную.
*  playbook создаёт базу данных под названием «logs» в Clickhouse. Вы можете изменить playbook, чтобы создать другую базу данных, если это необходимо.
*  playbook предполагает, что бинарный файл Vector будет установлен в директории, заданной в файле конфигурации `/group_vars/vector/vars.yml` . Если вам нужна другая директирия, вы можете изменить `/group_vars/vector/vars.yml`.
*  Версии ПО вы можете изменить в файлах `/group_vars/vector/vars.yml` `/group_vars/clickhouse/vars.yml`

### Права

Чтобы выполнить playbook, необходимы права на установку и удаление программ. Убедитесь, что используется пользователь с этими правами.


### Источники

* [Clickhouse documentation](https://clickhouse.com/docs/en/getting-started/install/)
* [Vector documentation](https://vector.dev/docs/)


## Скриншоты
### 5. ansible-lint ошибок нет
![image](https://github.com/user-attachments/assets/98b34900-7c60-475f-98c0-de73ffef3237)
### 6. --check ошибка выполнения изза запрета внесения изменений
![image](https://github.com/user-attachments/assets/3578868d-9776-4e09-ac34-161604f511d0)
### 7. --diff  Длинный лог получился. На скриншоте самй конец и summary по все задаче
![image](https://github.com/user-attachments/assets/cc06736b-e350-44b0-9664-027f56676687)
### 8. --diff Изменений нет
![image](https://github.com/user-attachments/assets/a432c36d-7621-4a06-be41-3164193aa648)





