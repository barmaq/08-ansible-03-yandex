**Домашнее задание к занятию 3 «yandex»**

переписал на работу с менеджером пакетов apt ( в привычных мне системах проще выполнять отладку. при необходимости передалаю под yum\centOS )

Плейбук устанавливает и подготавливает приложения Clickhouse и Vector и LightHouse 
Playbook разделен на три части : 

**Требования :** 
OS c менеджером пакетов **apt** ( Debian / Ubuntu )

**Install Clickhouse**  - Установка Clickhouse  
**Install and configure Vector** - Установка и настройка Vector  
**Install and configure LightHouse** - Установка и настройка  LightHouse  

------------------

**Установка:**

ansible-playbook site.yml -i inventory/prod.yml

По умолчани. хосты указываются раздельно для каждого блока Clickhouse, Vector и LightHouse в  
**inventory/prod.yml**

------------------

**Clickhouse:**
 

**Переменные:**  
параметры версии и названия необходимых пакетов указываются в **/group_vars/clickhouse/vars.yml**  

**особенности плейбука**  
По умолчанию плейбук пытается скачать дистрибутив **all.deb**, но в случае ошибки скачает **amd64.deb**

Для установки использует менеджер пакетов **apt**

------------------

**Vector**

**Переменные:**  
параметры версии указываются в **/group_vars/vector/vars.yml**  
шаблоны конфига указываются в **/templates/vector.j2**  
шаблоны файла сервиса указыаются в **/templates/vector.service.j2**  

Для установки использует менеджер пакетов **apt**

------------------

**LightHouse**

**Переменные:**  

ссылка на репозиторий и директория для установки указывается в **/group_vars/LightHouse/vars.yml**
Для установки использует модуль **git**  
устанавливает в качестве веб сервера **Nginx**


