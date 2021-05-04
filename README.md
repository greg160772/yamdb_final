![Image of GitHub Action]
(https://github.com/greg160772/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
# *Проект YamDB*
Проект создает API интерфейс для управление базой данных произведений. Произведения делятся на категории: «Книги», «Фильмы», «Музыка». К произведениям можно оставлять отзывы. Пользователи так же могут комментировать оставленные отзывы и выставлять произведениям оценки.

# *Технологии*
- python 3.8.5
- django 3.0.5
- djangorestframework 3.11.0
- simplejwt 4.3.0
- gunicorn 20.1.0
- postgreSQL 12.4
- nginx 1.19.3
- docker

# *Запуск приложения*

Установить инструменты командной строки Xcode
```sh
xcode-select --install
```
Склонируйте приложение из репозитория в созданную ранее директорию проекта
```sh
mkdir <project-dir>
cd <project-dir>
git clone https://github.com/greg160772/infra_sp2
```

Создайте в директории файл .env и пропишите в нем следующие переменные окружения
в формате **VAR=value**

- **DB_ENGINE=django.db.backends.postgresql** - *указываем, что работаем с postgresql*
- **DB_NAME=postgres** - *имя базы данных*
- **POSTGRES_USER=postgres** - *логин для подключения к базе данных*
- **POSTGRES_PASSWORD=postgres** - *пароль для подключения к БД (установите свой)*
- **DB_HOST=db** - *название сервиса (контейнера)*
- **DB_PORT=5432** - *порт для подключения к БД*

Установите приложение [Docker](https://www.docker.com/products/docker-desktop)

Выполните команду для сборки образов и запуска контейнеров.
```sh
docker-compose up -d
```
*Процесс сборки может занять некоторое время*

Выполните команды для создания базы данных и загрузки статических файлов приложения.
```sh
docker-compose exec web python manage.py makemigrations
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py collectstatic
```
Создайте администратора для управления базой данных и пользователями
```sh
docker-compose exec web python manage.py createsuperuser
```
# *Администрирование базы данных*
Введите в браузере адрес 
```sh
127.0.0.1/admin
```
введите учетные данные администратора

# *Документация по API*
Докумнтация по API-интерфейсу для работы с базой данных
доступна по адресу
```sh
127.0.0.1/redoc
```
# *Автор*
Григорий Александров
