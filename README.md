# Churn Brew

Модель машинного обучения для прогнозирования оттока клиентов сервиса доставки кофе **Happy Beans Coffee**.

## Описание

Бинарная классификация: предсказать, уйдёт ли клиент (churn = 1).
Датасет: 10 450 клиентов, 27 признаков (поведение в приложении, заказы, предпочтения).
Дисбаланс классов: ~6% оттока — основная метрика **PR AUC**.

## Результаты

| Модель | PR AUC (CV) |
|--------|------------|
| DummyClassifier (baseline) | 0.06 |
| LogisticRegression (baseline) | 0.67 |
| LogisticRegression + новые признаки | 0.68 |
| **LogisticRegression + тюнинг (финальная)** | **0.68 CV / 0.72 тест** |

## Ключевые выводы

- **Главный фактор оттока** — `app_crashes_last_month` (корреляция 0.50): сбои приложения напрямую приводят к уходу клиентов.
- Частота заказов и активность в приложении — ранние сигналы оттока.
- Клиенты с подпиской более лояльны.

## Структура проекта

```
Churn_Brew.ipynb   # Полный анализ: EDA, предобработка, обучение, тюнинг
```

## Стек

- `pandas`, `numpy` — обработка данных
- `scikit-learn` — Pipeline, LogisticRegression, GridSearchCV
- `matplotlib`, `seaborn` — визуализация
- `joblib` — сохранение модели

## Запуск

```bash
pip install pandas numpy scikit-learn matplotlib seaborn joblib
jupyter notebook Churn_Brew.ipynb
```
