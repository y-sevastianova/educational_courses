
##  Educational courses
В данном проекте анализирую данные онлайн курсов с помощью SQL.

---

### 1. Очень усердные ученики.

#### Условие

Образовательные курсы состоят из различных уроков, каждый из которых состоит из нескольких маленьких заданий. Каждое такое маленькое задание называется "горошиной".

Назовём очень усердным учеником того пользователя, который хотя бы раз за текущий месяц правильно решил 20 горошин.

#### Задание
Дана таблица default.peas:

| Название атрибута | Тип атрибута | Смысловое значение                       |
|-------------------|--------------|------------------------------------------|
| st_id             | int          | ID ученика                               |
| timest            | timestamp    | Время решения карточки                   |
| correct           | bool         | Правильно ли решена горошина?            |
| subject           | text         | Дисциплина, в которой находится горошина |


Необходимо написать оптимальный запрос, который даст информацию о количестве очень усердных студентов. NB! Под усердным студентом мы понимаем студента, который правильно решил 20 задач за текущий месяц.

### 2. Оптимизация воронки

#### Условие

Образовательная платформа предлагает пройти студентам курсы по модели trial: студент может решить бесплатно лишь 30 горошин в день. Для неограниченного количества заданий в определенной дисциплине студенту необходимо приобрести полный доступ. Команда провела эксперимент, где был протестирован новый экран оплаты.

#### Задача
Дана таблицы: default.peas (см. выше), default.studs:

| Название атрибута | Тип атрибута | Смысловое значение                   |
|-------------------|--------------|--------------------------------------|
| st_id             | int          |  ID ученика                          |
| test_grp          | text         |  Метка ученика в данном эксперименте |

и default.final_project_check:

| Название атрибута | Тип атрибута | Смысловое значение                     |
|-------------------|--------------|----------------------------------------|
| st_id             | int          | ID ученика                             |
| sale_time         | timestamp    | Время покупки                          |
| money             | int          | Цена, по которой приобрели данный курс |
| subject           | text         |                                        |

Необходимо в одном запросе выгрузить следующую информацию о группах пользователей:

- ARPU 
- ARPAU 
- CR в покупку 
- СR активного пользователя в покупку 
- CR пользователя из активности по математике (subject = ’math’) в покупку курса по математике
- ARPU считается относительно всех пользователей, попавших в группы.

Активным считается пользователь, за все время решивший больше 10 задач правильно в любых дисциплинах.

Активным по математике считается пользователь, за все время решивший 2 или больше задач правильно по математике.
