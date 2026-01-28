# Q4 Finance - МФО Website

Корпоративный сайт микрофинансовой организации Q4 Finance на WordPress.

## Технологии

- **WordPress** - CMS
- **Tailwind CSS** - стилизация
- **Alpine.js** - интерактивность
- **Docker** - контейнеризация
- **MySQL 8** - база данных

## Требования

- Docker и Docker Compose
- Git

## Быстрый старт

### 1. Клонировать репозиторий

```bash
git clone https://github.com/init-mahpal/mfo.git
cd mfo
```

### 2. Запустить контейнеры

```bash
docker-compose up -d
```

Это запустит:
- WordPress на http://localhost:8080
- MySQL на порту 3306
- phpMyAdmin на http://localhost:8081

### 3. Первоначальная настройка WordPress

1. Откройте http://localhost:8080
2. Следуйте инструкциям установки WordPress
3. Используйте следующие данные для подключения к БД:
   - **Database Name**: wordpress
   - **Username**: wordpress
   - **Password**: wordpress
   - **Database Host**: db:3306
   - **Table Prefix**: init_ (или оставьте wp_)

### 4. Активировать тему

1. Войдите в админ-панель WordPress (/wp-admin)
2. Перейдите в **Внешний вид → Темы**
3. Активируйте тему **"Q4"**

### 5. Собрать CSS (для разработки)

```bash
cd wordpress/wp-content/themes/q4
pnpm install
pnpm run build
# Или для разработки с автокомпиляцией:
pnpm run watch
```

## Структура проекта

```
mfo/
├── docker-compose.yml       # Конфигурация Docker
├── wordpress/               # WordPress установка
│   └── wp-content/
│       ├── themes/
│       │   └── q4/         # Основная тема
│       └── plugins/
│           └── q4-applications/  # Плагин заявок
├── mysql/                   # Данные MySQL (не в git)
└── doc/                     # PDF документы
```

## Основные страницы

Создайте следующие страницы в WordPress и назначьте им шаблоны:

- **Главная** → Front Page (template-parts собираются автоматически)
- **New Car** → slug: `newcar`, шаблон: "New Car Credit"
- **Used Car** → slug: `usedcar`, шаблон: "Used Car Credit"
- **Auto Money** → slug: `automoney`, шаблон: "Auto Money Credit"
- **Бизнес** → slug: `business`, шаблон: "Business Credit"
- **Потребительский** → slug: `consumer`, шаблон: "Consumer Credit"
- **Документы** → slug: `documents`, шаблон: "Документы"
- **Контакты** → slug: `contacts`, шаблон: "Contacts Page"

## Цветовая схема (корпоративные цвета)

- **Primary**: #008BC6
- **Secondary**: #0E6291
- **Accent**: #3E637D
- **Primary Light**: #A2C5D8

## Разработка

### Работа с темой

```bash
cd wordpress/wp-content/themes/q4

# Установка зависимостей
pnpm install

# Разработка с автокомпиляцией
pnpm run watch

# Продакшн сборка
pnpm run build
```

### Работа с плагинами

Плагин заявок находится в `wordpress/wp-content/plugins/q4-applications/`

## Важные замечания

⚠️ **НЕ коммитить в git:**
- Папку `mysql/` (данные БД)
- Файл `wordpress/wp-config.php` (содержит секреты)
- `.env` файлы

## Бэкап

Для бэкапа базы данных используйте:

```bash
docker exec mfo-db-1 mysqldump -u wordpress -pwordpress wordpress > backup.sql
```

Для восстановления:

```bash
docker exec -i mfo-db-1 mysql -u wordpress -pwordpress wordpress < backup.sql
```

## Контакты

- Email: Q4Finance@q4tulpar-auto.kz
- Телефон: +7 (777) 401-45-51
- Адрес: г. Алматы, Жетысуский район, пр. Абылай Хана, дом. 3А

## Лицензия

Лицензия на осуществление микрофинансовой деятельности 02.24.0014.М от 05.11.2024 года выданная Агентством Республики Казахстан по регулированию и развитию финансового рынка.
