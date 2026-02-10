# ProfManual
## **Оглавление**
1. [Необходимые библиотеки](#Библиотеки)
2. [Сессия 1](#Сессия-1)
3. [Сессия 2](#Сессия-2)
4. [Сессия 3](#Сессия-3)
5. [Сессия 4](#Сессия-4)

## Библиотеки
### Что необходимо установить для Visual Studio.
В менеджере пакетов NuGet ищем и ставим:
1. EntityFramework
2. LiveCharts и LiveCharts.WPF
3. System.Data.SqlClient

### Что ставить в PyCharm
Создаем новый проект с локальным интерпритатором <sub>надеемся что его не снесут</sub>
В терминале ставим FastApi и прочее для работы с БД
```
pip install fastapi[all] sqlalchemy pyodbc
```
Так же можно воткнуть pandas и openpyxl  
Для автоматического создания моделей нужен `sqlacodegen`
### Для веба надо следующее
Чтобы верстать быстро, нужен бутстрап качаем его 
- [с этого репозитория](content/bootstrap-5.3.0-dist)
- [или с сайта](https://getbootstrap.ru/docs/5.3/getting-started/download/)

Для меню календаря нужен будет Full Calendar
- [с репозитория](content/dist)
- [с сайта](https://fullcalendar.io/docs/initialize-globals)

## **Сессия 1**
### Создание базы данных
Базу данных запомнить наизусть, со всеми ограничениями, но вот по братски [схема]()
### Импорт данных в БД
**Для импорта пользователей и продукто юзаем json** 
```
declare @json nvarchar(max);
select @json = BulkColumn
from openrowset (bulk 'путь к файлу', SINGLE_NCLOB, CODEPAGE='65001') as j
```
Если будут ошибки с кодировкой, то меняем ее в исходном файле на 16LE через VS Code
Хэштрованная строка пароля пользователя: 
> a665a45920422f9d417e4867efdc4fb8a04a1f3fff1fa07e998e86f7f7a27ae3
#### Дальше импорт из .csv
Тут будет 100% ошибка кодировок, поэтому чтобы ее исправить нужно создать Excel документ, импотировать в него нужный CSV через вкладку "данные", а затем сохранить в новый CSV с кодировкой UTF-8
## Сесия 2
**Подключение Live Charts в xaml**  
В верхних строчках пишем:
```
xmlns:local="clr-namespace:WPFSample"
xmlns:lvc="clr-namespace:LiveChartsCore.SkiaSharpView.WPF;assembly=LiveChartsCore.SkiaSharpView.WPF">
```
