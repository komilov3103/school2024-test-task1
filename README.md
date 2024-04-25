# Тестовое задание для отбора на Летнюю ИТ-школу КРОК по разработке

## Условие задания
Один развивающийся и перспективный маркетплейс активно растет в настоящее время. Текущая команда разработки вовсю занята тем, что развивает ядро системы. Помимо этого, перед CTO маркетплейса стоит задача — разработать подсистему аналитики, которая на основе накопленных данных формировала бы разнообразные отчеты и статистику.

Вы — компания подрядчик, с которой маркетплейс заключил рамочный договор на выполнение работ по разработке этой подсистемы. В рамках первого этапа вы условились провести работы по прототипированию и определению целевого технологического стека и общих подходов к разработке.

На одном из совещаний с Заказчиком вы определили задачу, на которой будете выполнять работы по прототипированию. В качестве такой задачи была выбрана разработка отчета о периодах наибольших трат со стороны пользователей.

Аналитики со стороны маркетплейса предоставили небольшой срез массива данных (файл format.json) о покупках пользователей, на примере которого вы смогли бы ознакомиться с форматом входных данных. Каждая запись данного среза содержит следующую информацию:
- Идентификатор пользователя;
- Дата и время оформления заказа;
- Статус заказа;
- Сумма заказа.

В пояснительной записке к массиву данных была уточняющая информация относительно статусов заказов:
- COMPLETED (Завершенный заказ);
- CANCELED (Отмененный заказ);
- CREATED (Созданный заказ, еще не оплаченный);
- DELIVERY (Созданный и оплаченный заказ, который доставляется).

Необходимо разработать отчет, вычисляющий по полученному массиву данных месяц, когда пользователи тратили больше всего. Если максимальная сумма пользовательских трат была в более, чем одном месяце, отчет должен показывать все такие месяцы. В отчете должны учитываться только завершенные заказы.

Требования к реализации:
1. Реализация должна содержать, как минимум, одну процедуру (функцию/метод), отвечающую за формирование отчета, и должна быть описана в readme.md в соответствии с чек-листом;
2. В качестве входных данных программа использует json-файл (input.json), соответствующий структуре, описанной в условиях задания;
3. Процедура (функция/метод) формирования отчета должна возвращать строку в формате json следующего формата:
   - {«months»: [«march»]} 
   - {«months»: [«march», «december»]}
4. Найденный в соответствии с условием задачи месяц должен выводиться на английском языке в нижнем регистре. Если месяцев несколько, то на вывод они все подаются на английском языке в нижнем регистре в порядке их следования в течение года.

## Автор решения
Комилов Комилджон Шарифович
## Описание реализации
Решение реализовано в функции formated_report. Принимает функция на вход путь с названием json файла. 
Сначала функция считывает этот json файл, переводит в объект List. Далее проходим в цикле по этому листу с данными, если статус заказа "COMPLETED", парсим необходимы данные такие как, месяц заказа и сумму. 
Далее в отдельном словаре total засовываем в качестве ключа месяц заказа, в качестве значения сумму. 
Если месяц есть то сумму прибавляем, если нет добавляем месяц с суммой. Затем определяем максимальную сумму из total и его индекс и добавляем в max_profit_list, который в результате будет выведен. 
Далее функция проверяет есть ли в total другие месяцы с такой же максимлаьной суммой заказов и добавляет его в max_orofit_list. И в конце выводится результат в виде json в консоль как указано в задании.
Также в main.py реализована функция сортировки месяцев по порядку.
## Инструкция по сборке и запуску решения
Cделайте git clone git clone https://github.com/komilov3103/school2024-test-task1.git
Нужно расположить input.json файл теста в директорию, где main.py находится. 
Запустить команду python3 main.py и через консоль передать имя файла либо его путь с названием. 
Функция возвращает строку в формате json.
Если нужно вывести в консоль результат, то нужно откомментировать строку с print в конце.
