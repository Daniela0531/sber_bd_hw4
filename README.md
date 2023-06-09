# Изученине SenseiDB

## 1. История развития СУБД

Первоначально SenseiDB был разработан и использован командой LinkedIn в 2009 году.
Над проектом работали инженеры LinkedIn и Xiaomi.
Затем он стал проектом с открытым исходным кодом, в который внесли свой вклад многие люди.
После трех выпусков SenseiDB больше не обновлялась и не использовалась с 2013 года.

## 2. Инструменты для взаимодействия с СУБД
из того, что нашла:
Sensei Console: веб-консоль, которая позволяет пользователям взаимодействовать с базой данных Sensei и управлять индексами, документами и запросами.
Sensei REST API: RESTful API, который позволяет разработчикам программно взаимодействовать с базой данных Sensei, позволяя им создавать собственные приложения и интеграции.
Sensei Python Client: клиентская библиотека Python, предоставляющая простой в использовании интерфейс для взаимодействия с базой данных Sensei.
Sensei Java Client: клиентская библиотека Java, предоставляющая простой в использовании интерфейс для взаимодействия с базой данных Sensei.
Sensei CLI: интерфейс командной строки, который позволяет пользователям взаимодействовать с базой данных Sensei с терминала.
Sensei Admin: веб-инструмент администрирования, который позволяет пользователям управлять и контролировать свои кластеры Sensei.
Sensei Data Loader: инструмент, который позволяет пользователям загружать данные в базу данных Sensei из различных источников, включая CSV-файлы и базы данных.
Sensei Query Builder: графический пользовательский интерфейс, который позволяет пользователям создавать сложные запросы для базы данных Sensei без написания кода.

## 3. Какой database engine используется в вашей СУБД?
не нашла

## 4. Как устроен язык запросов в вашей СУБД?
Используется язык запросов BQL.
Язык запросов для просмотра (BQL) поддерживается SenseiDB, который имеет синтаксис, похожий на SQL.
Помимо существующих предложений в SQL, BQL вводит предложение "BROWSE BY" для поддержки граненого поиска и навигации.
Это самая большая особенность BQL.

## 5. Возможно ли распределение файлов БД по разным носителям?
Исходя из информации с официальных сайтов, какое-либо распараллеливание не поддерживается:

SenseiDB не поддерживает параллельные операции. 
Только один поток может работать одновременно.
Кроме того, транзакции также не поддерживаются.

## 6. На каком языке/ах программирования написана СУБД?
Java

## 7. Какие типы индексов поддерживаются в БД?
SenseiDB применяет менеджер индексации под названием Zoie,
который представляет собой независимый механизм поиска и индексации,
построенный на Apache Lucene, который использует инвертированный индекс для эффективного извлечения данных.
Самая большая особенность Zoie — поддержка поиска и обновлений в реальном времени.

встроенное задание индексации Map-reduce

## 8. Как строится процесс выполнения запросов в вашей СУБД?
Выполнение запроса выполняется механизмом запросов под названием Bobo, который использует модель кортежа за раз.

## 9. Есть ли для вашей СУБД понятие «план запросов»? Если да, объясните, как работает данный этап.
нет

## 10. Поддерживаются ли транзакции в вашей СУБД?
Нет, не поддерживаются.
см п 5

## 11. Какие методы восстановления поддерживаются в вашей СУБД.
Не нашла, что такие есть.
Контрольно-пропускных пунктов нет, ведение журнала нет, кажется что методов восстановления нет.

Вся база данных разделена на несколько осколков.
Каждый шард реплицируется между N узлами, так что в одном узле может быть более одного осколка.
В системе нет главного узла, и каждый узел независим.
Предстоящие запросы проходят через отдельный балансировщик нагрузки, чтобы решить, какие узлы запрашивать.


## 12. Расскажите про шардинг в вашей конкретной СУБД.
данная субд легко маштабируется

## 13. Возможно ли применить термины Data Mining, Data Warehousing и OLAP в вашей СУБД?
да, OLAP

## 14. Какие методы защиты поддерживаются вашей СУБД? Шифрование трафика, модели авторизации и т.п.
шифрование AES-256, шифрование SSL/TLS и безопасное хранение данных с несколькими уровнями защиты.

## 15. Какие сообщества развивают данную СУБД? Кто в проекте имеет права на коммит и создание дистрибутива версий?
база данных Sensei представляет собой проект с открытым исходным кодом, который активно поддерживается и
развивается командой разработчиков и участников со всего мира.

## 16. Создайте свои собственные данные для демонстрации работы СУБД

- 
## 17. Как продолжить самостоятельное изучение языка запросов с помощью демобазы. Если демобазы нет, то создайте ее.
нет

## 18. Где найти документацию и пройти обучение
http://senseidb.github.io/sensei/

## 19. Как быть в курсе происходящего
твитер: @sensei_db
http://senseidb.github.io/sensei/
http://senseidb.github.io/sensei/overview.html


Экземпляр SenseiDB - это таблица данных, организованная в столбцы.
Атрибуты таблицы хранятся в виде метаданных, и каждый столбец может принадлежать к одному из поддерживаемых типов:
string, int, long, short, float, double, char, date, text.