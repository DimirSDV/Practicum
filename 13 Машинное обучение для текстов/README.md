# Классификация текстовых комментариев (на основе ML)

## Ключевые навыки
Машинное обучение для текстов: BERT, spacy, автоматический подбор гиперпараметров

## Используемые библиотеки
`nltk` `torch` `spacy` `sklearn` `lightgbm` `catboost` `time` `numpy` `pandas` `seaborn` `matplotlib` `tqdm` `transformers` `pathlib` `pymystem3`

## Задачи проекта
Подобрать и обучить ML-модели для классификации текстовых комментариев пользователей интернет-магазина на позитивные и негативные

## Выводы
В результате проведения исследования достигнута цель проекта - обучена модель, которая способна классифицировать комментарии на позитивные и негативные, при этом значение метрики качества F1 превышает требуемые 0.75! `LinearRegression`, `CatBoostClassifier`, `LightGBM` значительно превзошли требуемую метрику качества. Лучшей по качеству оказалась модель `LightGBM`
    
    1) LightGBM (гиперпараметры)
    params = {
        'metric': 'f1',
        'max_depth': 10, 
        'learning_rate': 0.1,
        'n_estimators': 1000,
        'num_leaves': 8,
        'verbose': 0}
