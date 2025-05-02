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
 -----------------
 ![alt text](img/Zadanie1.png)
 -----------------
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

## Задание 3
Привяжите созданный шаблон к двум хостам. Также привяжите к обоим хостам шаблон Linux by Zabbix Agent.

Процесс выполнения
Выполняя ДЗ сверяйтесь с процессом отражённым в записи лекции.
Зайдите в настройки каждого хоста и в разделе Templates прикрепите к этому хосту ваш шаблон
Так же к каждому хосту привяжите шаблон Linux by Zabbix Agent
Проверьте что в раздел Latest Data начали поступать необходимые данные из вашего шаблона
Требования к результату
 Прикрепите в файл README.md скриншот страницы хостов, где будут видны привязки шаблонов с названиями «Задание 2-3». Хосты должны иметь зелёный статус подключения
![alt text](img/add_templ.png)


## Задание 4
Создайте свой кастомный дашборд.

Процесс выполнения
Выполняя ДЗ сверяйтесь с процессом отражённым в записи лекции.
В разделе Dashboards создайте новый дашборд
Разместите на нём несколько графиков на ваше усмотрение.
Требования к результату
 Прикрепите в файл README.md скриншот дашборда с названием «Задание 4»
![alt text](img/test_DASHBOARD.png)

## Задание 5* со звёздочкой
Создайте карту и расположите на ней два своих хоста.

Процесс выполнения
Настройте между хостами линк.
Привяжите к линку триггер, связанный с agent.ping одного из хостов, и установите индикатором сработавшего триггера красную пунктирную линию.
Выключите хост, чей триггер добавлен в линк. Дождитесь срабатывания триггера.
Требования к результату
 Прикрепите в файл README.md скриншот карты, где видно, что триггер сработал, с названием «Задание 5»
 ![alt text](img/map.png)
 
 чтобы настроить связь нужно CTRL+выбрать 2 хоста
 и настроить триггер
 ![alt text](img/line.png)
 Если хотим чтобы хост назавался как он называется в хостах то используем переменную
  ![alt text](img/Hostname.png)


 ## Задание 6* со звёздочкой
Создайте UserParameter на bash и прикрепите его к созданному вами ранее шаблону. Он должен вызывать скрипт, который:

при получении 1 будет возвращать ваши ФИО,
при получении 2 будет возвращать текущую дату.
Требования к результату
 Прикрепите в файл README.md код скрипта, а также скриншот Latest data с результатом работы скрипта на bash, чтобы был виден результат работы скрипта при отправке в него 1 и 2

 ### Создадим простой UserParameter

![alt text](img/add_zabbix_custom_echo.png)

Создадим файл test_up.conf в директории /etc/zabbix/zabbix_agentd.d
```
sudo nano /etc/zabbix/zabbix_agentd.d/test_user_parameter.conf
```

Добавим туда строку:

```
UserParameter=my_script[*], python3 /etc/zabbix/test_python_script.py $1 $2
```

создаем скрипт
``nano /etc/zabbix/test_python_script.py``
```
import sys
import os
import re
if (sys.argv[1] == '-ping'): # Если -ping
 result=os.popen("ping -c 1 " + sys.argv[2]).read() # Делаем пинг по заданному адресу
 result=re.findall(r"time=(.*) ms", result) # Выдёргиваем из результата время
 print(result[0]) # Выводим результат в консоль
elif (sys.argv[1] == '-simple_print'): # Если simple_print
 print(sys.argv[2]) # Выводим в консоль содержимое sys.arvg[2]
else: # Во всех остальных случаях
 print(f"unknown input: {sys.argv[1]}") # Выводим непонятый запрос в консоль
```
![alt text](img/user_parameters.png)
![alt text](img/script_use.png)
![alt text](img/script2.png)


# Доработанный скрипт Zabbix

Этот скрипт расширяет функции из лекции и обрабатывает различные запросы:

- При вызове с аргументом `1` возвращает ФИО.
- При вызове с аргументом `2` возвращает текущую дату.
- При вызове с аргументом `-ping <адрес>` выполняет ping по заданному адресу.
- При вызове с аргументом `-simple_print <текст>` выводит текст.

## Установка

1. Убедитесь, что Zabbix Agent установлен на сервере.
2. Скопируйте скрипт в `/etc/zabbix/test_python_script.py`.
3. Обновите конфигурацию Zabbix Agent с помощью добавления параметров в файл `/etc/zabbix/zabbix_agentd.d/test_up.conf`.
4. Перезапустите Zabbix Agent:
```
   sudo systemctl restart zabbix-agent
```

```
import sys
import os
import re
from datetime import datetime

# Проверка на количество передаваемых аргументов
if len(sys.argv) < 2:
    print("Error: Not enough arguments")
    sys.exit(1)

# Определение поведения в зависимости от переданных параметров

if sys.argv[1] == '-ping':  # Если -ping
    result = os.popen("ping -c 1 " + sys.argv[2]).read()  # Делаем пинг по заданному адресу
    result = re.findall(r"time=(.*) ms", result)  # Выдёргиваем из результата время
    if result:
        print(result[0])  # Выводим результат в консоль
    else:
        print("Ping failed or no response.")
elif sys.argv[1] == '1':  # Запрос на ФИО
    print("Ваши ФИО")  # Замените на свои ФИО
elif sys.argv[1] == '2':  # Запрос на текущую дату
    print(datetime.now().strftime("%Y-%m-%d %H:%M:%S"))  # Вывод текущей даты
elif sys.argv[1] == '-simple_print':  # Если simple_print
    print(sys.argv[2])  # Выводим в консоль содержимое sys.argv[2]
else:  # Во всех остальных случаях
    print(f"unknown input: {sys.argv[1]}")  # Выводим непонятый запрос в консоль

```

![alt text](img/zabbiconfig.png)

- Для получения ФИО:
    - Запрос:
    `` zabbix_get -s 192.168.31.125 -p 10050 -k my_fio``
- Для получения текущей даты:
    - Запрос:`` zabbix_get -s 192.168.31.12 -p 10050 -k my_date``
- Для проверки Ping:
    - Запрос: ``zabbix_get -s 192.168.31.12 -p 10050 -k "my_ping[8.8.8.8]"``
- Для простого вывода текста:
    - Запрос: ``zabbix_get -s 192.168.31.12 -p 10050 -k "my_simple_print[текст]"``


![alt text](img/zabbixget.png)


Задание 8* со звёздочкой
Настройте автообнаружение и прикрепление к хостам созданного вами ранее шаблона.

![alt text](img/autodecdoveryrule.png)
![auto2](img/auto2.png)
![alt text](img/auto3.png)

