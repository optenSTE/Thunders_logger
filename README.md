# Thunders_logger
Софт для получения времени и координат молний в выбранном районе

# Цель 
Получить время и координаты каждой отдельной молнии. Фиксация молний основана на распределенных электромагнитных детекторах проекта https://www.blitzortung.org/
На текущий момент (13.08.2021) blitzortung.org не предоставляет доступ к архивам молний, приходится действовать обходными путями.

# Обходной путь1
Необходимо открыть онлайн-карту молний, запустить запись скриншотов.
На полученных снимках найти маркеры молний, определить их координаты - вручную или с помощью python
```
Настроить отображение онлайн-карты на сайте map.blitzortung.org. Открыть нужный район + запас по сторонам. Тип подложки - по вкусу

Запустить запись скриншотов с помощью программы AutomaticScreenshotter
Capture Options
  Capture rate = 1
  Specific region - указать неизменную часть карты (где нет счетчиков, рекламы), например 14х199, 1899х850
Capture Rules
  Ignore changes... = 1
App Rules
  Only ever capture... = chrome.exe
```

# Обходной путь2
На сайт приходят JSON'ы с описанием молний
https://map.blitzortung.org/GEOjson/getjson.php?f=s&n=01
Всего приходят 24 файла, в каждом описание молний за 5 минут
Содержимое:
```
[
  [
    16.286692,
    64.486795,
    "2021-08-14 09:45:09.261672192",
    1,
    11965,
    87,
    331
  ],
  [
    16.246337,
    64.499321,
    "2021-08-14 09:45:09.261675520",
    1,
    5272,
    204,
    360
  ],
  ...
]

Значение полей
[
  Широта, °
  Долгота, °
  Время молнии (UTC)
  Container:	1	(Europe)
  max deviation,	nsec
  min cycle gap, °
  detectors involved
]
```
