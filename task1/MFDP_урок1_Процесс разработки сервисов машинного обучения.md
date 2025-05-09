**1\.  Бизнес-анализ (Business Understanding)**  
В первую очередь необходимо определиться с целями и скоупом проекта.  
Для этого нужно найти ответы на следующие вопросы:

* *Организационная структура: \
    - в рамках MFDP
* *Собираем контакты, создаем рабочие чаты.*  
    - не требуется
* *Какова бизнес-цель проекта? Например, уменьшение оттока клиентов.*  
    - снижение финансовых потерь (например 20% за счет оперативного обнаружения мошеннических операций)
    - уменьшение доли ложных срабатываний (например, 20% для снижения нагрузки на службу поддержки)
* *Существуют ли какие-то уже разработанные решения? Если существуют, то какие и чем именно текущее решение не устраивает?*\
Существующие решения используют
    - правила на основе статических порогов (например, транзации свыше 300т.р. млм 3 транзакции в течении часа).
    - классические ML-модели (логистическая регрессия, случайный лес, xgboost), которые не учитывают сетевые взаимосвязи между транзакциями.

  И имеют следующие проблемы:
    - высоких уровень ложных срабатываний
    - неспособность детектировать скоординированные атаки 
    - медленная адаптация к новым видам мошшеничества

**1.1 Текущая ситуация (Assessing current solution)**  
Оцениваем, хватает ли ресурсов для проекта.

* Есть ли доступное железо или его необходимо закупать?  
    - Возможно потребуется аренда GPU для обучения GNN
* Где и как хранятся данные, будет ли предоставлен доступ в эти системы, нужно ли дополнительно докупать/собирать  
    - не требуется
* внешние данные?  
    - Kaggle Credit Card Fraud Detection dataset
* Сможет ли заказчик выделить своих экспертов для консультаций на данный проект?
    -   не сможет

Нужно описать вероятные риски проекта, а также определить план действий по их уменьшению.

Типичные риски следующие.

* Срыв сроков из-за сложности GNN \
=> Поэтапная разработка: сначала классическая ML-модель, затем добавление графового слоя
* Низкое качество данных \
=> Генерация синтетических данных   
* Отсутствие закономерностей \
=> Предварительный EDA и проверка гипотез на исторических данных.

**1.2 Решаемые задачи с точки зрения аналитики (Data Mining goals)**  
Выполняем постановку в технических терминах. Для этого нужно ответить на следующие вопросы:

* Какую метрику мы будем использовать для оценки результата моделирования (а выбрать есть из чего: Accuracy, RMSE, AUC, Precision, Recall, F-мера, R2, Lift, Logloss и т.д.)?  
    -   F1 Score, как сбалансированая метрика между Precision И Recall
* Каков критерий успешности модели (например, считаем AUC равный 0.65 — минимальным порогом, 0.75 —  оптимальным)?  
    - F1 Score = 0.7 минимальный, 0,8 успешный
* Если объективный критерий качества использовать не будем, то как будут оцениваться результаты?
    - не требуется

**1.3 План проекта (Project Plan)**  
Как только получены ответы на все основные вопросы и ясна цель проекта, время составить план проекта. План должен  
содержать оценку всех шести фаз внедрения.  
1.  Бизнес-анализ (Business Understanding)  - 1 неделя
2. Анализ данных (Data Understanding)       - 1 неделя
3. Подготовка данных (Data Preparation)     - 1 неделя
4. Моделирование (Modeling)                 - 2 неделя
5. Оценка результата (Evaluation)           - 1 неделя
6. Внедрение (Deployment)                   - 1 неделя    
