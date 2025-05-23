# Обнаружение Мошенничества в Финансовых Транзакциях (Fraud Detection)

## Описание Проекта

Данный проект представляет собой комплексное решение для обнаружения мошеннических операций в финансовых транзакциях с использованием различных методов машинного обучения. Целью проекта было построение робастной системы, способной эффективно выявлять аномальные транзакции, минимизируя финансовые риски и повышая безопасность.

Проект охватывает весь жизненный цикл создания ML-модели: от разведочного анализа данных (EDA) и Feature Engineering до разработки, обучения и оценки производительности моделей на основе градиентного бустинга (CatBoost) и глубоких нейронных сетей (PyTorch).

## Ключевые Компоненты и Методология

1.  **Разведочный Анализ Данных (EDA)** (`notebooks/01_EDA.ipynb`):
    * Первичное исследование структуры данных, типов признаков и их распределений.
    * Выявление пропущенных значений, аномалий и выбросов.
    * Визуализация ключевых зависимостей для глубокого понимания данных.

2.  **Генерация Признаков (Feature Engineering)** (`notebooks/02_FeatureEngineering.ipynb`):
    * Создание обширного набора новых, информативных признаков из исходных данных.
    * **Временные признаки:** Извлечение часа, дня недели, месяца, года, а также определение временных окон (например, ночные транзакции).
    * **Геопространственные признаки:** Расчет расстояний между пользователем и мерчантом (Haversine distance).
    * **Поведенческие признаки:** Агрегация статистик (среднее, медиана, стандартное отклонение, перцентили) по суммам транзакций, частоте операций для каждого пользователя и категории, а также на основе временных окон.
    * **Признаки аномалий:** Расчет Z-score для сумм транзакций относительно типичного поведения пользователя/мерчанта для выявления необычных паттернов.
    * **Хеширование категориальных признаков:** Использование хеширования для обработки высококардинальных категориальных признаков.

3.  **Разработка Модели CatBoost** (`notebooks/03_CatBoostModel.ipynb`):
    * Обучение классификатора CatBoost, известного своей эффективностью в работе с табличными данными и встроенной обработкой категориальных признаков.
    * Использование Stratified K-Fold Cross-Validation для надежной оценки производительности и снижения риска переобучения, особенно важного при работе с несбалансированными классами.
    * Применение библиотеки Optuna для автоматизированной оптимизации гиперпараметров, что позволило найти наилучшие конфигурации модели.
    * Оценка производительности с помощью метрик: ROC AUC, F1-score, Precision-Recall Curve (AUC PR), Classification Report, Confusion Matrix – ключевых показателей для задач с несбалансированными классами.

4.  **Разработка Модели PyTorch (Нейронная Сеть)** (`notebooks/pytorch.ipynb`):
    * Построение и обучение нейронной сети с использованием фреймворка PyTorch для сравнения с бустинговыми моделями и исследования возможности захвата более сложных нелинейных зависимостей.
    * Также использована Stratified K-Fold Cross-Validation и Optuna для оптимизации.
    * Оценка по тем же метрикам, что и для CatBoost, для прямого сравнения моделей.


## Будущие Улучшения
### Достаточно большая доля мошеннических транзакций все еще остается невыявленной, вот некоторые улучшения, которые стоит опробовать:
* Перепроверка обработки данных, а также улучшение фиче-инжиниринга
* Исследование более сложных архитектур нейронных сетей (например, с LSTM для временных рядов).
* Интеграция аномалийных детекторов без учителя (Unsupervised Anomaly Detection).
* Разработка веб-интерфейса для демонстрации работы модели.
* Исследование Explainable AI (XAI) методов для интерпретации решений модели.

## Используемые Технологии

* **Python**
* **Pandas, NumPy** 
* **Matplotlib, Seaborn** 
* **Scipy.stats** 
* **scikit-learn**
* **CatBoost** 
* **PyTorch** 
* **Optuna** 
* **Hashlib** 

## Результаты и Практическая Направленность

Проект продемонстрировал высокую эффективность разработанных моделей в выявлении мошеннических транзакций. Например, модель CatBoost достигла ROC AUC свыше 0.95 на валидационных данных, что является отличным показателем для данной задачи. Сравнение CatBoost и нейронных сетей показало, что оба подхода могут быть очень эффективными, при этом CatBoost часто требует меньше вычислительных ресурсов и проще в интерпретации, тогда как нейронные сети могут улавливать более сложные паттерны.

Практическая ценность проекта заключается в его прямом применении в финансовом секторе для:
* **Сокращения финансовых потерь** от мошенничества.
* **Повышения безопасности** клиентских операций.
* **Оптимизации процессов** ручной проверки транзакций за счет автоматизации.
* **Прокачки ключевых навыков** в области Data Science, включая работу с несбалансированными данными, Feature Engineering и использование различных ML-фреймворков.# Fraud_Detection
# Fraud_Detection
