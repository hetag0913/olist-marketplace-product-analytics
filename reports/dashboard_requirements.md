# Dashboard Requirements — Olist Marketplace Analytics



## Цель дашборда



Дашборд должен объединять основные результаты продуктовой, финансовой, клиентской, seller-funnel и операционной аналитики маркетплейса Olist.



Основные задачи:



- отслеживать масштаб бизнеса и динамику GMV;

- контролировать товарные категории;

- оценивать удержание и ценность клиентов;

- анализировать привлечение и активацию продавцов;

- выявлять логистические риск-сегменты;

- контролировать качество клиентского опыта;

- использовать ML-скоринг для приоритизации рискованных заказов.



## Целевые пользователи



Дашборд может использоваться:



- руководителями продукта — для контроля ключевых KPI и продуктовых проблем;

- коммерческой командой — для анализа категорий и seller value;

- CRM-командой — для работы с retention и RFM-сегментами;

- операционной командой — для контроля доставки и сложных заказов;

- клиентской поддержкой — для приоритизации заказов с высоким риском негативного опыта;

- маркетинговой командой — для анализа seller acquisition funnel.



## Глобальные фильтры



Фильтры, применимые к основным разделам:



- период покупки;

- штат и город клиента;

- товарная категория;

- статус заказа;

- количество продавцов в заказе;

- наличие задержки;

- диапазон длительности доставки;

- RFM-сегмент;

- источник привлечения продавца;

- бизнес-сегмент продавца.



## Executive Overview



### KPI-карточки



- Delivered orders;

- Unique customers;

- GMV;

- Freight value;

- AOV;

- Average review score;

- Repeat customer rate;

- Bad review rate;

- Delayed orders rate;

- Multi-seller orders rate.



### Визуализации



1. Orders by month.

2. GMV by month.

3. AOV by month.

4. Average review score by month.

5. Order value composition: product value и freight value.



Основной сопоставимый период для месячной динамики:



- январь 2017 — август 2018.



Разреженные наблюдения 2016 года не следует использовать для сравнения с полноценными месяцами.





## Category Performance



### Метрики



- Orders;

- GMV;

- GMV share;

- AOV proxy;

- Freight value;

- Freight share;

- Average review score;

- ABC class.



### Визуализации



1. Top-15 categories by GMV.

2. Top-15 categories by orders.

3. Categories by average review score.

4. Categories by freight share.

5. GMV share by ABC class.

6. Scatter plot: AOV proxy vs average review score.

7. Detailed table by category.



### Правила отображения



- техническая категория `unknown` сохраняется в сверке общего GMV, но исключается из бизнес-сравнения;

- категории с малым количеством заказов должны быть помечены как статистически нестабильные;

- рейтинг по review score рекомендуется показывать только для категорий с минимальным числом заказов;

- `office_furniture` следует вынести в отдельный проблемный сегмент.



## ABC-анализ



Используемые пороги:



- A — категории, формирующие первые 80% накопленного GMV;

- B — следующие категории до 95% накопленного GMV;

- C — оставшийся длинный хвост.



Дашборд должен показывать:



- количество категорий в каждом классе;

- GMV и GMV share;

- количество заказов;

- список категорий;

- средний review score;

- freight share.



По текущим результатам:



- класс A — 17 категорий, около 81% GMV;

- класс B — 16 категорий, около 14% GMV;

- класс C — 40 категорий, около 5% GMV.



## Customer Retention & Value



### KPI-карточки



- Unique customers;

- Repeat customer rate;

- Median LTV proxy;

- GMV share of top-10% customers;

- Average customer frequency;

- Number of customers by RFM segment.



### Визуализации



1. Cohort retention heatmap.

2. Customer frequency distribution.

3. Customer share by RFM segment.

4. GMV share by RFM segment.

5. Customer share vs GMV share.

6. LTV proxy distribution.

7. Top customer segments table.



### Методология



- клиент идентифицируется через `customer_unique_id`;

- когорта определяется как месяц первой доставленной покупки;

- retention рассчитывается на уровне `customer_unique_id × order_month`;

- будущие недоступные периоды отображаются как пропуски, а не как нули;

- LTV является proxy через накопленный GMV;

- RFM-логика адаптирована под очень низкую повторность покупок.



### Основные ориентиры



- repeat customer rate — около 3%;

- месячный retention в большинстве когорт — менее 1%;

- медианный LTV proxy — 89,73;

- top-10% клиентов формируют около 41,14% GMV.



## Seller Acquisition Funnel



### KPI-карточки



- Marketing Qualified Leads;

- Closed Deals;

- MQL → Closed Deal conversion;

- Activated Sellers;

- Activation Rate;

- Sellers with Delivered Orders;

- Median Days to First Order;

- Median Seller GMV;

- Average Seller GMV.



### Визуализации



1. Funnel: MQL → Closed Deal → Seller with Orders → Seller with Delivered Orders.

2. MQL by acquisition channel.

3. Closed deals by channel.

4. Activation rate by channel.

5. Seller GMV by channel.

6. Median seller GMV by channel.

7. Days to first order distribution.

8. Seller value table by channel.



### Фильтры



- источник привлечения;

- business segment;

- business type;

- lead type;

- lead behaviour profile;

- период первого контакта;

- период закрытия сделки.



### Методология



- Marketing Funnel описывает привлечение продавцов, а не покупателей;

- продавец считается активированным, если после закрытия сделки получил хотя бы один заказ;

- seller GMV рассчитывается по доставленным заказам после привлечения;

- источник `unknown` сохраняется для контроля атрибуции, но не интерпретируется как управляемый маркетинговый канал;

- небольшие каналы необходимо интерпретировать с учётом размера выборки;

- без рекламных расходов нельзя рассчитать CAC и ROMI.



### Основные ориентиры



- 8 000 MQL;

- 842 закрытые сделки;

- MQL → Closed Deal conversion — 10,53%;

- 380 активированных продавцов;

- activation rate — около 45%;

- медианное время до первого заказа — около 44 дней;

- медианный seller GMV — 547,40.



## Delivery & Customer Experience



### KPI-карточки



- Bad Review Rate;

- Delayed Orders Rate;

- Average Delivery Days;

- Average Delivery Delay;

- Multi-seller Orders Rate;

- Bad Review Rate among Delayed Orders;

- Bad Review Rate among Multi-seller Orders.



### Визуализации



1. Bad review rate: delayed vs non-delayed orders.

2. Bad review rate: single-seller vs multi-seller orders.

3. Bad review rate by delivery duration bucket.

4. Average review score by delivery delay bucket.

5. Delivery days distribution.

6. Delayed orders by category.

7. Delayed orders by state.

8. Matrix: category × delivery risk.



### Риск-сегменты



- задержка относительно обещанной даты;

- задержка на три дня и более;

- доставка длительностью 15 дней и более;

- несколько продавцов в заказе;

- несколько товарных позиций;

- категории с высокой freight share;

- категории с низким review score.



### Основные ориентиры



- bad review rate без задержки — 17,34%;

- bad review rate при задержке — 73,25%;

- bad review rate у single-seller заказов — 20,53%;

- bad review rate у multi-seller заказов — 60,59%;

- при доставке 15 дней и более без просрочки bad review rate — 23,60%.



Наблюдаемые различия не следует интерпретировать как доказательство причинно-следственной связи.



## ML Risk Monitoring



### KPI-карточки



- ROC-AUC;

- PR-AUC;

- F1-score;

- Precision;

- Recall;

- Lift@10%;

- Predicted Positive Share;

- Bad Review Rate in Top-10% Risk;

- Number of High-Risk Orders.



### Визуализации



1. Logistic Regression vs CatBoost.

2. ROC-AUC and PR-AUC by model.

3. Precision, recall and F1-score by model.

4. Bad review rate in top-risk deciles.

5. Lift by risk percentile.

6. Distribution of predicted probabilities.

7. Feature importance.

8. SHAP summary plot.

9. High-risk orders table.



### Таблица рискованных заказов



Таблица должна содержать:



- `order_id`;

- дату покупки;

- регион клиента;

- категорию;

- количество товарных позиций;

- количество продавцов;

- длительность доставки;

- задержку относительно обещанной даты;

- прогнозируемую вероятность негативного отзыва;

- риск-группу;

- фактический результат, если он уже доступен.



### Сценарий использования



Модель предназначена для ранжирования заказов, а не для полностью автоматического принятия решений.



Операционная команда может:



- направлять top-risk сегмент в проактивную поддержку;

- выделять задержанные и сложные заказы;

- контролировать нагрузку на команду через выбранный порог;

- сравнивать качество модели между периодами и сегментами.



### Основные ориентиры CatBoost



- ROC-AUC — 0,650;

- PR-AUC — 0,364;

- lift@10% — 2,68;

- precision — 56,57%;

- recall — 20,05%;

- bad review rate в top-10% риска — около 44,5%;

- средний bad review rate тестовой выборки — около 16,6%.



### Ограничения модели



- модель обладает умеренной разделяющей способностью;

- текущая версия использует признаки, доступные после завершения доставки;

- результаты не следует использовать для автоматических санкций против продавцов;

- качество необходимо контролировать во времени;

- при изменении распределения заказов потребуется переобучение;

- для практического применения предпочтительна модель раннего предупреждения.



## Платежи



Нужны блоки:



1. Payment value by payment type

2. Orders by payment type

3. Average installments by payment type

4. Average GMV by installments bucket



Installments buckets:



- 1

- 2–3

- 4–6

- 7–10

- 11+



## Методологические ограничения



- основные KPI рассчитываются по доставленным заказам;

- GMV определяется как стоимость товаров без доставки;

- freight value анализируется отдельно и не называется выручкой маркетплейса;

- payment value ближе к стоимости заказа с доставкой, а не к GMV;

- таблицы разных уровней детализации нельзя объединять без предварительной агрегации;

- review score находится на уровне заказа;

- для категорий отзывы рассчитываются через уровень `order_id × category`;

- техническая категория `unknown` исключается из бизнес-сравнения категорий;

- клиент идентифицируется через `customer_unique_id`;

- LTV является proxy через накопленный GMV;

- Marketing Funnel относится к привлечению продавцов;

- seller GMV не является выручкой или прибылью маркетплейса;

- отсутствуют рекламные расходы, комиссия, маржа и себестоимость;

- наблюдательные зависимости не доказывают причинность;

- A/B-анализ является синтетической симуляцией;

- ML-модель использует ограниченный набор признаков;

- исторические данные охватывают период 2016–2018 годов.

