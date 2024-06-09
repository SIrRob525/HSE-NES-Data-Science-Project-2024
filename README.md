# Анализ публикаций в области компьютерных наук на основе базы данных DBLP

**Внимание:** рекомендую смотреть проект в Google Colab: https://colab.research.google.com/drive/10EGY7fyP3YZHB2Wmpu_UnTzURL16TLaP?usp=sharing. Также, если хотите "прогнать" ноутбук сами, необходимо прогнать ячейку с созданием базы данных (работает 30 минут), либо скачать ее с моего Google Диска: https://drive.google.com/file/d/11q5xHg8Ol1ua5_p_vlx_YKQfCV02Z0gK/view?usp=sharing

**О проекте DBLP:** "DBLP (Digital Bibliography & Library Project) — это проект, который представляет собой электронную библиографическую базу данных по информатике. Он содержит информацию о научных публикациях, конференциях и других событиях в области информатики. Он поддерживается сообществом исследователей и разработчиков, которые вносят свой вклад в его развитие. База данных постоянно обновляется и расширяется, что делает её ценным источником информации для учёных, студентов и всех, кто интересуется информатикой." (Yandex GPT 3 Pro, ред.). Официальный сайт проекта: https://dblp.uni-trier.de/

**Задачи:**

1.   Проверить гипотезу о том, что количество работ растет экспоненциально с каждым годом.
2.   Визуализировать распределение количества публикаций по странам. Ожидается, что большая часть публикаций из крупных технологически развитых стран: США, Китай, Германия, Франция, Япония. 
3.   Визуализировать сетевой граф публикаций (где связь отражает цитирование). Ожидается, что мы увидим наличие больших кластеров работ со схожей тематикой.

**Выводы:** 
1. Подтвердилась гипотеза об экспоненциальном росте числа работ.
2. ![image](https://github.com/SIrRob525/HSE-NES-Data-Science-Project-2024/assets/74403363/a881c64c-a8ac-4765-855f-68707a0e99b9) ![image](https://github.com/SIrRob525/HSE-NES-Data-Science-Project-2024/assets/74403363/e130db99-e315-49a6-b514-c06d7af96062)


3. Частично подтвердилась гипотеза о распределении числа публикаций по странам. Чтобы получить корректный ответ, необходимо собрать более точные данные по всем работам, что, вероятно, очень непросто.
   ![image](https://github.com/SIrRob525/HSE-NES-Data-Science-Project-2024/assets/74403363/024e6f09-0968-46ca-87cb-92da1a2b5348)

   
4. Не подтвердилась гипотеза о виде сетевого графа. Необходимо собрать данные о связях между работами, чтобы построить общий граф.
   
   <img width="709" alt="image" src="https://github.com/SIrRob525/HSE-NES-Data-Science-Project-2024/assets/74403363/4b6e8e5f-e41c-4f9e-9acd-5002d1d02a14">

**Использованные технологии:**

1. Работа с XML для создания базы данных в формате .db (библиотека `lxml`);
2. Работа с SQL для получения данных из базы (библиотека `sqlite3`);
3. Использование библиотеки `sklearn` для построения линейной регрессии;
4. Использование регулярных выражений для парсинга страны из названия университета;
5. Работа с геоданными: использование библиотек `pycountry` (https://pypi.org/project/pycountry/), `iso3166` (https://pypi.org/project/iso3166/), `universities` (https://pypi.org/project/universities/) для парсинга кода страны из ее названия/названия университета;
6. Работа с геоданными: использование `plotly` для построения интерактивной карты;
7. Работа с `pandas`, в т.ч. группировка (по стране);
8. Работа с CrossRef REST API (https://www.crossref.org/documentation/retrieve-metadata/rest-api/) для получения данных о цитировании;
9. Построение сетевого графа с помошью `networkx` и `igraph`.
