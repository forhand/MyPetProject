# MyPetProject
Демонстрационный проект, в котором я реализую новые освоенные инструменты и подходы в разработке.

**MyPetProject** - Репозиторий для всего проекта. Использует git submodule.

Чтобы склонировать весь репозиторий с субмодулями необходимо ввести команду
`git clone --recurse-submodules https://github.com/forhand/MyPetProject`

Сервисы и сущности будут постепенно усложняться, но изначально созданы в простой форме, 
для демонстрации функционала.

### infra

Для локального поднятия БД и других инструментов, создан отдельный репозиторий, 
который содержит в себе все инфраструктурные компоненты (БД, Redis, Kafka, Docker Compose и пр.)

### user-service

Сервис по работе с пользователями и подписками:

- CRUD
- [Публикация события при подписке на пользователя](https://github.com/forhand/user-service/blob/4cdab459623b19c64ef4e55b8d98525cf05e4b5f/src/main/java/org/example/user_service/publisher/AbstractEventPublisher.java)

### post-service

Сервис по работе с постами:

- CRUD
- [Публикация постов по расписанию](https://github.com/forhand/post-service/blob/main/src/main/java/org/example/service/post/PostService.java)
- [Временное кэширование опубликованных постов](https://github.com/forhand/post-service/blob/main/src/main/java/org/example/service/post/PostService.java)

### notification-service

Сервис для уведомления пользователей:

- [Слушатель событий](https://github.com/forhand/notification-service/blob/main/src/main/java/org/example/notification_service/listener/AbstractEventListener.java)
- [Отправка уведомления по Email](https://github.com/forhand/notification-service/blob/main/src/main/java/org/example/notification_service/service/EmailService.java)

### analytic-service

Сервис слушает события и сохраняет `AnalyticEvent` в базу данных

- [Получение аналитики за указанный период](https://github.com/forhand/analytic-service/blob/main/src/main/java/org/example/analytic_service/service/AnalyticService.java)
- [Получение аналитики за указанный интервал](https://github.com/forhand/analytic-service/blob/main/src/main/java/org/example/analytic_service/filter/impl/AnalyticsIntervalFilter.java)

### achievement-service

Сервис выдаёт пользователям достижения при выполнении условий и публикует событие для `notification-service`

- Заполнение кэша по расписанию всеми достижениями


