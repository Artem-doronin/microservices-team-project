# Corporation x — социальная сеть для стартапов

Учебный командный проект: приложение на микросервисной архитектуре.

## 📌 О проекте

Социальная сеть для стартапов и предпринимателей. Проект разрабатывался командой в рамках учебной программы под руководством техлида. Цель — отработать промышленные подходы: микросервисы, event-driven взаимодействие, облачное хранение.

**Роль:** Java-разработчик (участник команды).

## 🛠 Стек

- Java 17+, Spring Boot
- PostgreSQL, Redis
- Apache Kafka (event-driven)
- MinIO (S3-совместимое хранилище)
- Docker, Docker Compose
- Git, Merge Requests, код-ревью

## 🧩 Микросервисы (9)

Проект состоял из 9 независимых сервисов. Ниже — те, в разработке которых я участвовал лично:

| # | Сервис | Ответственность | Мой вклад | Ссылка на ветку / репозиторий |
|---|---|---|---|---|
| 1 | **URL Shortener** | Сокращение ссылок | Самостоятельная разработка сервиса: генерация коротких кодов, редиректы, хранение в БД | [UrlShortener](https://github.com/Artem-doronin/url_shortener_service/tree/titan-ArtemUrlShortener-stream9) |
| 2 | **PostService** | Посты пользователей | Командная разработка: CRUD-логика постов, работа с PostgreSQL | [post_service](https://github.com/Artem-doronin/post_service) |
| 3 | **UserService** | Профили пользователей | Командная разработка: регистрация и обновление профилей | [user_service](https://github.com/Artem-doronin/user_service/tree/titan-master-stream9) | 
| 4 | **ProjectService** | Стартап-проекты | Командная разработка: логика создания и ведения проектов | [project_service](https://github.com/Artem-doronin/project_service/tree/titan-master-stream9) |
| 5 | **PaymentService** | Платежи | Командная разработка: обработка транзакций и статусов оплаты | [payment_service](https://github.com/Artem-doronin/payment_service/tree/titan-master-stream9) |
| 6 | **NotificationService** | Уведомления | Командная разработка: отправка уведомлений по событиям | [notification_service](https://github.com/Artem-doronin/notification_service) |
| 7 | **AnalyticsService** | Аналитика | Командная разработка: сбор и агрегация метрик активности | [analytics_service](https://github.com/Artem-doronin/analytics_service) |
| 8 | **AchievementService** | Система достижений | Командная разработка на event-driven подходе: подписка на события, начисление достижений | [achievement_service](https://github.com/Artem-doronin/achievement_service) |
| 9 | **AccountService** | Аккаунты | Командная разработка: управление аккаунтами и балансом | [account_service](https://github.com/Artem-doronin/account_service/tree/titan-master-stream9) |


## 🔄 Event-driven взаимодействие

Сервисы общались асинхронно через Kafka:
- AchievementService подписывался на события действий пользователей и начислял достижения.
- NotificationService отправлял уведомления по событиям из других сервисов.
- Это позволяло развязать сервисы и не блокировать основные операции.

## 🚀 Запуск локально

Каждый сервис — отдельное Spring Boot-приложение со своим репозиторием.

### Требования
- JDK 17+
- Docker и Docker Compose
- Maven

### Запуск сервиса
```bash
git clone https://github.com/Artem-doronin/post_service
cd post_service
./mvnw spring-boot:run
