# ZABBIX_CONFIG2
## Задание 1
Создайте свой шаблон, в котором будут элементы данных, мониторящие загрузку CPU и RAM хоста.

# Процесс выполнения
1. Выполняя ДЗ сверяйтесь с процессом отражённым в записи лекции.
2. В веб-интерфейсе Zabbix Servera в разделе Templates создайте новый шаблон
3. Создайте Item который будет собирать информацию об загрузке CPU в процентах
4. Создайте Item который будет собирать информацию об загрузке RAM в процентах
Требования к результату
 Прикрепите в файл README.md скриншот страницы шаблона с названием «Задание 1»

## Ответ 
1. Создаем новый шаблон
 ![New_template](img/New_Template.png)

 ![Zabbix_templ](img/Zabbix_new_template.png)
Добавим свой макрос
Укажем параметры обновления 5s и 50s
 ![alt text](img/macros_addpng.png)
 Создаем item
 ![alt text](img/createitems.png)
 СоздаетДанные
 ![cri](img/CreateIITEM2.png)

 Привязываем шаблон к хосту
 ![alt text](img/add_tmpl_to_host.png)

 --------------
 ### создаем шаблоны для CPU и RAM

 ![alt text](img/CPU_RAM.png)

 ![alt text](img/macro.png)

 ![alt text](img/CPU.png)

 ![alt text](img/RAM.png)

 прикручиваем шаблон к хосту
 ![alt text](img/add_tohost.png)
 ![alt text](img/add_tohost2.png)
 ![alt text](img/addtohost3.png)
 обновляем данные
 ![alt text](img/upd_itemspng.png)
 Идем смотреть что получилось
 так же можно потыкать в графики
 ![alt text](img/resultpng.png)
 ![alt text](img/gaphpng.png)


## Задание 2
Добавьте в Zabbix два хоста и задайте им имена <фамилия и инициалы-1> и <фамилия и инициалы-2>. Например: ivanovii-1 и ivanovii-2.

Процесс выполнения
Выполняя ДЗ сверяйтесь с процессом отражённым в записи лекции.
Установите Zabbix Agent на 2 виртмашины, одной из них может быть ваш Zabbix Server
Добавьте Zabbix Server в список разрешенных серверов ваших Zabbix Agentов
Добавьте Zabbix Agentов в раздел Configuration > Hosts вашего Zabbix Servera
Прикрепите за каждым хостом шаблон Linux by Zabbix Agent
Проверьте что в разделе Latest Data начали появляться данные с добавленных агентов
Требования к результату
 Результат данного задания сдавайте вместе с заданием 3
 ![alt text](img/hosts.png)