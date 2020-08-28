#![Yamdb workflow](https://github.com/SvetlanaIa/yamdb_final/workflows/yamdbworkflow/badge.svg)
![Yamdb workflow](https://github.com/SvetlanaIa/yamdb_final/workflows/yamdb%20workflow/badge.svg)

# api_yamdb
## Проект по реализации API

Создано с помощью Django REST Framework

### Описание:
реализация REST API для сервиса YaMDb — базы отзывов о фильмах, книгах и музыке. Проект YaMDb собирает отзывы (Review) пользователей на произведения (Title). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (Category) может быть расширен (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).

Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.

В каждой категории есть произведения: книги, фильмы или музыка. Например, в категории «Книги» могут быть произведения «Винни Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Насекомые» и вторая сюита Баха. Произведению может быть присвоен жанр из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). Новые жанры может создавать только администратор.

Благодарные или возмущённые читатели оставляют к произведениям текстовые отзывы (Review) и выставляют произведению рейтинг (оценку в диапазоне от одного до десяти). Из множества оценок автоматически высчитывается средняя оценка произведения.

#### Ресурсы API YaMDb:
* Ресурс AUTH: аутентификация.
* Ресурс USERS: пользователи.
* Ресурс TITLES: произведения, к которым пишут отзывы (определённый фильм, книга или песенка).
* Ресурс CATEGORIES: категории (типы) произведений («Фильмы», «Книги», «Музыка»).
* Ресурс GENRES: жанры произведений. Одно произведение может быть привязано к нескольким жанрам.
* Ресурс REVIEWS: отзывы на произведения. Отзыв привязан к определённому произведению.
* Ресурс COMMENTS: комментарии к отзывам. Комментарий привязан к определённому отзыву.

### Установка:
Для установки ПО необходимо 
1. Создать .env с переменными окружения:
    - DB_ENGINE
    - DB_NAME
    - DB_USER
    - DB_PASSWORD
    - DB_HOST
    - DB_PORT
    - POSTGRES_USER
    - POSTGRES_PASSWORD
2. docker-compose up
3. docker container ls 
4. docker exec -it <id_контейнера_web> bash
5. В контейнере web выполнить миграции, создать суперюзера и загрузить данные:
- python manage.py migrate
- python manage.py createsuperuser
- python manage.py loaddata fixtures.json


### Доступные методы:
метод                                                         | GET | POST | PUT | PATCH | DEL |
--------------------------------------------------------------|-----|------|-----|-------|-----|
/api/v1/auth/email/ | - | V | - | - | - |
/api/v1/auth/token/| - | V | - | - | - |
/api/v1/token/refresh/ | - | V | - | - | - |
/api/v1/users/me/| V | - | - | V | - |
/api/v1/titles/ | V | V | - | - | - |
/api/v1/titles/{titles_id}/ | V | - | - | V | V |
/api/v1/titles/{title_id}/reviews/  | V | V | - | - | - |
/api/v1/titles/{title_id}/reviews/{review_id}/ | V | - | - | V | V |
/api/v1/titles/{title_id}/reviews/{review_id}/comments/ | V | V | - | - | - |
/api/v1/titles/{title_id}/reviews/{review_id}/comments/{comment_id}/ | V | - | - | V | V |
/api/v1/users/ | V | V | - | - | - |
/api/v1/users/{username}/ | V | - | - | V | V |
/api/v1/categories/ | V | V | - | - | - |
/api/v1/categories/{slug}/ | - | - | - | - | V |
/api/v1/genres/ | V | V | - | - | - |
/api/v1/genres/{slug}/ | - | - | - | - | V |
