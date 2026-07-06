\# Dashboard Requirements — Product \& Financial Metrics



\## Цель дашборда



Дашборд должен показывать ключевые продуктовые и финансовые метрики маркетплейса Olist на основе доставленных заказов.



Основная задача — дать быстрый обзор:



\- масштаба бизнеса;

\- динамики GMV и заказов;

\- структуры категорий;

\- качества клиентского опыта;

\- платёжного поведения.



\## Основные KPI



В верхней части дашборда должны быть карточки:



\- Delivered orders

\- Unique customers

\- GMV

\- Freight revenue

\- AOV

\- Average review score

\- Repeat customers share

\- Canceled orders share



\## Динамика по месяцам



Нужны графики:



1\. Orders by month

2\. GMV by month

3\. AOV by month

4\. Average review score by month



Период для основной динамики:



\- January 2017 — August 2018



Важно: август 2018 является неполным месяцем, поэтому его нужно интерпретировать осторожно.



\## Категории



Нужны визуализации:



1\. Top 10 categories by GMV

2\. Top 10 categories by orders

3\. Categories by average review score

4\. Categories by freight-to-GMV ratio

5\. ABC segments by GMV share



\## ABC-анализ



Дашборд должен показывать:



\- количество категорий в A/B/C сегментах;

\- GMV share по каждому сегменту;

\- orders share по каждому сегменту;

\- список категорий внутри каждого сегмента.



Используемые пороги:



\- A: первые 80% накопленного GMV;

\- B: от 80% до 95% накопленного GMV;

\- C: после 95% накопленного GMV.



\## Платежи



Нужны блоки:



1\. Payment value by payment type

2\. Orders by payment type

3\. Average installments by payment type

4\. Average GMV by installments bucket



Installments buckets:



\- 1

\- 2–3

\- 4–6

\- 7–10

\- 11+



\## Важные методологические ограничения



\- GMV считается как стоимость товаров без доставки.

\- Freight revenue анализируется отдельно.

\- Payment value ближе к GMV + freight, поэтому его нельзя напрямую называть GMV.

\- Основные KPI считаются только по delivered orders.

\- Review score находится на уровне заказа, а не товарной строки.

\- Для категорий review score считается через пары order\_id + category.

\- В данных нет маржи, себестоимости, комиссии маркетплейса и рекламных расходов.

