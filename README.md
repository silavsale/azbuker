# Книжная доска объявлений

Небольшой, но активно используемый книжный классифайд, запущенный в 2012-м году. 
Ежедневно десятки людей публикуют и находят новые книги. Проект написан давно, и умышленно оставлен 
почти в первозданном виде, чтобы было что улучшать и исправлять.

Улучшая проект, ты нарабатываешь скилл, репутацию и строчки в резюме!

Из технических решений тут есть: полнотекстовый поиск, полуавтоматическое утягивание базы книжек и обложек
с Озона, добавление нового объявления в один клик, отправка сообщений продавцам на почту, немного кэширования.

Проект выложен в open source с целью привлечения всех неравнодушных к развитию проекта. 
Сделано в рамках программы стажировки [«Хорошего программиста»](http://goodprogrammer.ru).
Как поучаствовать в проекте — читай [в разделе ниже](#как-участвовать-в-проекте). 

Автор проект Михаил Бутлицкий, о правах на использование кода [в конце](#лицензия-и-права). Вопросы — на почту mbutlitsky+github@gmail.com

# Установка проекта 

Проект пока работает на Ruby 2.1.5, Rails 3, Postgres 9.6 и живет по адресу [azbuker.ru](http://azbuker.ru). 
Для локальной работы и тестирования тоже нужен постгрес.

### 1. Подготовка
Установить и инициализировать (крайне желательно с локалью ru_RU.UTF-8) Postgres не ниже 9.4

На маке есть чудный [Postgres.app](https://postgresapp.com/), на линуксе — смотрите наши 
уроки [раз](https://www.youtube.com/watch?v=aJLRnDJ2CVg) и [два](https://www.youtube.com/watch?v=xg-oB5kzTMY), 

Если вы на Windows — сперва изучите [это](https://www.youtube.com/watch?v=vY9QNwX_IsY), потом [это](https://www.youtube.com/watch?v=tQLpAefAKuA),
и напоследок [это](https://www.youtube.com/watch?v=ZqNIpli5JGI).

С помощью RBENV/RVM установить Ruby 2.1.5

### 2. Код

* Скачиваем код
* `bundle install`
* `bundle exec rake db:migrate`
* Делаем свои файлы `.env` и `config/database.yml` аналогично примерам
* `.env` заполняем сразу, конфиг базы — след. шаг 

### 3. Данные

* Следуем инструкции из комментариев файла `config/database.example.yml`
* После создания баз — создаем свою копию `config/database.yml`
* Убеждаемся, что локально есть контакт `bundle exec rails c`

В принципе можно запускать и играться локально, но можно накидать немножко обложек из Озона. 
В корне проекта лежит небольшой фрагмент боевой базы `ozbooks.zip`.

После распаковки надо скормить его в вашу дев. базу.

```
psql -f (путь к файлу azbuker_oz_books.sql) (имя вашей dev базы азбукера)
```

После чего в автосаджесте при добавлении нового лота можно искать книги например *Стивен* и *Томас*

### 4. Деплой

Изучите deploy.rb и Capfile. Деплоить на свой хостинг есть смысл для тестов только если 
хотите мигрировать на новые рельсы и новый капистрано.

# Как участвовать в проекте

Приглашаются начинающие и опытные разработчики. Пока все желающие, но приоритет у студентов 
и выпускников наших [интенсивов по Ruby on Rails](http://goodprogrammer.ru/rails-winter-18?utm_source=github.com&utm_medium=readme&utm_campaign=azbuker).

Приглашаются и НЕ программисты (маркетологи, продуктологи, любители книг) — хорошие бизнес решения с удовольствием
внедрим, а если решения принесут деньги, то и поделимся.

Основной ваш вклад в проект — пулл-реквест с полезным кодом или Issue (https://github.com/aristofun/azbuker/issues) 
если это не связанное с кодом улучшение.

Официальный слак: http://bit.ly/azbukerslack 

**Внимание**, тут вас не будут учить программировать (для этого есть [курсы](http://goodprogrammer.ru)).
 Тут вы должны **приносить пользу**.

# Как приносить пользу?

Задачи для разработчиков есть на любой вкус и скилл. Идеи по развитию самого продукта — тоже велкам.
Это не проект для подражания, но проект для улучшения. Здесь полно проблем в коде, но проект живет 
и приносит пользу. 

А значит ваш труд по улучшнию проекта нужен людям. И главное — каждая активность это хорошая **строчка в резюме**.


### Для нубов
* Документирование проекта (вики — как работает сбор обложек с озона, какие есть кастомные rake таски, диаграмма зависимостей между моделями)
* Перевод документации (вот этого ридми например) на английский
* Исправление кодстайла и мелких ошибок, некрасивостей в коде (тысячи их!)
* Комментирование особо сложных и опасных мест в коде (такого тоже полно)
* Рефакторинг и упрощение тестов
* Написание дополнительных тестов

### Для продвинутых
* Миграция на свежие Rails, свежие капистрано и пр. (глобальная и крутая для скилла задача)
* Автоматизация (или переделка) импорта свежих озоновских книжек
* Рефакторинг кода, избавление от костылей и code smell
* Выделение Service Objects и отделение логики обработки объявлений от веб-представлений
* Миграция на последний Bootstrap
* Избавление от старой админки (прикручивание новой?)
* Поиск и исправление уязвимостей в коде

# Лицензия и права

Код можно использовать только в личных, учебно-позновательных целях и для развития данного проекта. 
Использование кода или его частей в других проектах разрешается только с явного согласия автора 
данного репозитория. 
