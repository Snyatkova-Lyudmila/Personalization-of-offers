# Разработка решения для персонализации предложения постоянным клиентам интернет-магазина «В один клик»

Интернет-магазин «В один клик» продаёт разные товары: для детей, для дома, мелкую бытовую технику, косметику и даже продукты. Отчёт магазина за прошлый период показал, что активность покупателей начала снижаться. Привлекать новых клиентов уже не так эффективно: о магазине и так знает большая часть целевой аудитории. Возможный выход - удерживать активность постоянных клиентов. Сделать это можно с помощью персонализированных предложений.

«В один клик» - современная компания, поэтому её руководство не хочет принимать решения просто так - только на основе анализа данных и бизнес-моделирования. Отделу цифровых технологий необходимо разработать решение, которое позволит персонализировать предложения постоянным клиентам с целью увеличения их покупательской активности.

## Задачи исследования

* провести предобработку и анализ данных
* промаркировать уровень финансовой активности постоянных покупателей: «снизилась» / «прежний уровень»
* cобрать данные по клиентам по следующим группам:

1)признаки, которые описывают коммуникацию сотрудников компании с клиентом  
2)признаки, которые описывают продуктовое поведение покупателя (например, какие товары покупает и как часто)
3)признаки, которые описывают покупательское поведение клиента (например, сколько тратил в магазине)
4)признаки, которые описывают поведение покупателя на сайте (например, как много страниц просматривает и сколько времени проводит на сайте)

* построить модель, которая предскажет вероятность снижения покупательской активности клиента в следующие три месяца
(в исследование нужно включить дополнительные данные финансового департамента о прибыльности клиента: какой доход каждый покупатель приносил компании за последние три месяца)
* используя данные модели и данные о прибыльности клиентов, выделить сегменты покупателей 
* разработать персонализированные предложения для каждого сегмента покупателей
* сделать выводы, дать рекомендации

## Цель исследования
разработать решение, которое позволит персонализировать предложения постоянным клиентамс целью увеличения их покупательской активности.

## Данные для анализа

*market_file.csv* - таблица, которая содержит данные о поведении покупателя на сайте, о коммуникациях с покупателем и его продуктовом поведении

*market_money.csv* - таблица с данными о выручке, которую получает магазин с покупателя / сколько покупатель всего потратил за период взаимодействия с сайтом

*market_time.csv* - таблица с данными о времени (в минутах), которое покупатель провёл на сайте в течение периода

*money.csv* - таблица с данными о среднемесячной прибыли покупателя за последние 3 месяца / какую прибыль получает магазин от продаж каждому покупателю

## Описание данных

Датасет market_file.csv:

* *id* — номер покупателя в корпоративной базе данных
* *Покупательская активность* — рассчитанный класс покупательской активности (целевой признак): «снизилась» или «прежний уровень»
* *Тип сервиса* — уровень сервиса, например «премиум» и «стандарт»
* *Разрешить сообщать* — информация о том, можно ли присылать покупателю дополнительные предложения о товаре  
(согласие на это даёт покупатель)
* *Маркет_актив_6_мес* — среднемесячное значение маркетинговых коммуникаций компании, которое приходилось на покупателя за последние 6 месяцев / это значение показывает, какое число рассылок, звонков, показов рекламы и прочего приходилось на клиента
* *Маркет_актив_тек_мес* — количество маркетинговых коммуникаций в текущем месяце
* *Длительность* — значение, которое показывает, сколько дней прошло с момента регистрации покупателя на сайте
* *Акционные_покупки* — среднемесячная доля покупок по акции от общего числа покупок за последние 6 месяцев
* *Популярная_категория* — самая популярная категория товаров у покупателя за последние 6 месяцев
* *Средний_просмотр_категорий_за_визит* — показывает, сколько в среднем категорий покупатель просмотрел за визит в течение последнего месяца
* *Неоплаченные_продукты_штук_квартал* — общее число неоплаченных товаров в корзине за последние 3 месяца
* *Ошибка_сервиса* — число сбоев, которые коснулись покупателя во время посещения сайта
* *Страниц_за_визит* — среднее количество страниц, которые просмотрел покупатель за один визит на сайт за последние 3 месяца

Датасет market_money.csv:

* *id* — номер покупателя в корпоративной базе данных
* *Период* — название периода, во время которого зафиксирована выручка (например, 'текущий_месяц' или 'предыдущий_месяц')
* *Выручка* — сумма выручки за период

Датасет market_time.csv:

* *id* — номер покупателя в корпоративной базе данных
* *Период* — название периода, во время которого зафиксировано общее время
* *минут* — значение времени, проведённого на сайте, в минутах

Датасет money.csv:

* *id* — номер покупателя в корпоративной базе данных
* *Прибыль* — значение прибыли

## Этапы работы над проектом

*Шаг 1.* Загрузка данных

*Шаг 2.* Предобработка данных

*Шаг 3.* Исследовательский анализ данных:  
* исследовательский анализ данных из каждой таблицы  
* отбор клиентов с покупательской активностью не менее трёх месяцев, то есть таких, которые что-либо покупали в этот период  
выводы по результатам шага

*Шаг 4.* Объединение таблиц (market_file.csv, market_money.csv, market_time.csv)

*Шаг 5.* Корреляционный анализ
* корреляционный анализ признаков в количественной шкале в итоговой таблице для моделирования
* выводы о мультиколлинеарности 

*Шаг 6.* Использование пайплайнов
* подготовка данных с использованием ColumnTransformer
* обучение четырех моделей: KNeighborsClassifier(), DecisionTreeClassifier(), LogisticRegression() и  SVC()
* выбор подходящей метрики
* выбор лучшей модели с помощью выбранной метрики (при использовании одного общего пайплайна для всех моделей)

*Шаг 7.* Анализ важности признаков
* оценка важности признаков для лучшей модели, построение графика важности с помощью метода SHAP
* выводы о значимости признаков:  

*Шаг 8.* Сегментация покупателей  
* сегментация покупателей с использованием результатов моделирования и данных о прибыльности покупателей
* выбор группы покупателей, предложения по увеличению её покупательскую активности
* выводы о сегментах (какой сегмент был исследован, какие предложения были сформулированы)

*Шаг 9.* Общий вывод
