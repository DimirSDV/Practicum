# Рекомендательная система тарифов для "Мегалайн" (на основе ML)

## Ключевые навыки
Введение в машинное обучение: классификация в ML, метрика accuracy

## Используемые библиотеки
`sklearn` `scipy` `pandas` `numpy` `matplotlib` `seaborn` `plotly.express`

## Задачи проекта
Построить модель для задачи классификации тарифов, которая выберет подходящий тариф с максимально большим значением accuracy, но не менее 0.75

## Выводы
В результате исследования была достигнута цель проекта, а именно построенна модель для задачи классификации, которая выберет подходящий новый тариф («Смарт» или «Ультра») для предложения пользователям (в т.ч. архивных тарифов) оператора мобильной связи «Мегалайн». 
 Для достижения цели были проделаны следующие шаги и получены следующие выводы: 
   
 1) Файл открыт, данные загружены. Датафрейм не содержит пропущенных значений, не содержит дубликатов, типы данных приведены к требуемым по логике. Объекты признака is_ultra содержат только 0 или 1 (это единственный признак с категориальными значениями, остальные столбцы содержат количественные значения). 
 По построенной диаграммаме "ящик с усами" видно, что для объектов со значнением "is_ultra" == 1 (абонент пользовался тарифом "Ультра" в течение месяца) распределения по всем показателям (минуты, звонки, смс и интернет-траффик) содержит незначительное количество выбросов, медиана находится в районе середины первого и третьего квартиля, что может свидетельствовать о сбалансированности использования тарифа "Ультра" пользователями. Иными словами, пользователи "сидят на своем правильном тарифе", а количество пользователей, которые превышают или недоиспользуют звонки, смс и интернет по сравнению со среднестатистическим пользователем тарифа "Ультра", незначительно. По построенной диаграмме "ящик с усами" видно, что для объектов со значнением "is_ultra" == 0 (абонент пользовался тарифом "Смарт" в течение месяца) распределения по всем показателям (минуты, звонки, смс и интернет-траффик) содержит значительное количество выбросов, при этом медиана находится в районе середины первого и третьего квартиля, что может свидетельствовать о несбалансированности использования тарифа "Смарт" пользователями. Иными словами, пользователи "сидят не на своем правильном тарифе", а количество пользователей, которые превышают звонки и смс, а также превышают или недобирают интернет-траффик по сравнению со среднестатистическим пользователем тарифа "Смарт", значительное.
 Резюмируя можно сказать, что на исследуемом датасете есть возможность применить ML для подбора оптимального тарифа!.    
   
2) Исходные данные разделены на обучающую (60%), валидационную (20%) и тестовую выборки (20%). По статистикам видно, что данные разделены с относительно приемлемыми отклонениями по медианным и средним значениям, но отклонения присутствуют (это особенно важно для проверки моделей на тестовых данных).
    
3) Было проведено обучение и оценка качества различных моделей со сменой гиперпараметров. Места по точности предсказания распределились следующим образом: 
       первое место: RandomForestClassifier. Accuraccy на валидационной выборке: 0.8164852255054432 при Est (количество 'деревьев') =  41
       второе место: DecisionTreeClassifier. Accuraccy на валидационной выборке: 0.8149300155520995  при Depth (глубина 'дерева') =  5
       третье место: LogisticRegression. Accuraccy на валидационной выборке: 0.7463692946058091 при max_iter (количество итераций) = 300
    
4) Мы проверили качество моделей, обученных на предыдущем шаге, на тестовой выборке. Все гиперпараметры моделей, полученные на шаге №3, использованы для проверки на тестовой выборке. На тестовой выборке получены следующие результаты:
    первое место: RandomForestClassifier. Accuraccy на тестовой выборке: 0.8211508553654744 при Est (количество 'деревьев') =  41
    второе место: DecisionTreeClassifier. Accuraccy на тестовой выборке: 0.7947122861586314 при Depth (глубина 'дерева') =  5
    третье место: LogisticRegression. Accuraccy на тестовой выборке: 0.7371695178849145 при max_iter (количество итераций) = 300. 
Тестовая выборка не поменяла распределение мест для ранее обученных моделей: RandomForestClassifier увеличил точность на 0,5%, для LogisticRegression снизилась точность на 0,9%, а для DecisionTreeClassifier показатель качества модели (Accuraccy) снизился на 2%.  

5) Мы проверили модели на вменяемость - показатель точности (Accuraccy) у всех обученных моделей оказался выше, чем предсказания по DummyClassifier, выбранному для проверки моделей на вменяемость. Таким образом, с определенной долей вероятности можно утверждать, что обученные модели способны верно предсказывать используемый тариф. На предоставленных для исследования данных лучшие показатели у модели RandomForestClassifier (0.82 на валидационной и тестовой выборках) - именно эту модель рекомендуется использовать для анализа поведения клиентов, пользующихся в т.ч. архивными тарифами, с целью предложить им новый тариф: «Смарт» или «Ультра».
