# Определение рыночной стоимости автомобилей (на основе ML)

## Ключевые навыки
Численные методы: регрессия в ML, CatBoost,  LightGBM, замер времени, автоматический подбор гиперпараметров

## Используемые библиотеки
`sklearn` `lightgbm` `catboost` `math` `time` `itertools` `numpy` `pandas` `seaborn` `matplotlib`

## Задачи проекта
Подобрать и обучить модель для предсказания рыночной стоимости автомобилей, которая должна иметь высокое качество предсказания (RMSE не более 2500), высокая скорость предсказания и малое время обучения

## Выводы
В исследовании были подобраны параметры и обучены 3 модели: LinearRegression, CatBoostRegressor и LightGBM. Самой быстрой и точной оказалась модель LightGBM, незначительно ей уступает в точности CatBoostRegressor, при этом CatBoostRegressor на два порядка дольше всех обучается. Модель LinearRegression не прошла отбор по критерию качества - RMSE превысил максимально допустимое значение в 2500.
Цель исследования достигнута, а именно создана модель для предсказания рыночной стоимости автомобилей, которая должна иметь высокое качество предсказания (RMSE не более 2500), высокую скорость предсказания и малое время обучения. Такой моделью оказалась LGBMRegressor(learning_rate=0.2, max_depth=7, metric='rmse', objective='regression', verbose=0)
