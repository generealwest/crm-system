# 🏗️ CRM Система для Строительной Компании

**Полнофункциональная цифровая система управления для строительных компаний**

---

## 📋 Содержание

- [Обзор](#обзор)
- [Функциональность](#функциональность)
- [Технологический стек](#технологический-стек)
- [Быстрый старт](#быстрый-старт)
- [Архитектура](#архитектура)
- [Разработка](#разработка)
- [Документация](#документация)

---

## 🎯 Обзор

Это **enterprise-grade CRM система** специально разработана для строительных компаний с полным функционалом:

✅ **Управление продажами** - воронка продаж, сделки, лиды  
✅ **Управление объектами** - объекты, этажи, квартиры, документация  
✅ **База подрядчиков** - подрядчики, работы, лицензии, рейтинги  
✅ **Финансы** - доходы, расходы, расчёты, прогнозы  
✅ **Аналитика** - KPI, графики, отчёты, экспорт  
✅ **Система заметок** - комментарии, уведомления, документооборот  

---

## ✨ Функциональность

### 🏢 Модуль "Воронка продаж"
- Управление сделками (от лида до контракта)
- Kanban доска для визуального управления
- История сделок и активности
- Прогноз доходов
- Интеграция с клиентами

### 📍 Модуль "Управление объектами"
- Иерархическая структура объектов (участок → дом → этаж → квартира)
- Галереи фото и планов
- Документация по объектам
- Тайм-лайн хода строительства
- Статусы и этапы

### 👥 Модуль "Подрядчики"
- База данных подрядчиков и ИП
- Типы работ и специализация
- Лицензии и сертификаты
- История работ и рейтинги
- Отзывы клиентов

### 💰 Модуль "Финансы"
- Доходы и расходы
- Расчёты с клиентами (счета, платежи)
- Расчёты с подрядчиками
- Кассовые потоки и прогнозы
- Бюджетирование

### 📊 Модуль "Аналитика"
- Главный дашборд с KPI
- Графики и диаграммы
- Сравнение периодов
- Экспорт отчётов (PDF, Excel)
- Real-time метрики

### 💬 Модуль "Заметки & Коммуникация"
- Система комментариев для всех объектов
- Упоминания (@mentions)
- Вложение файлов
- История комментариев
- Уведомления в реальном времени

---

## 🛠️ Технологический стек

### Backend
- **Runtime**: Node.js
- **Framework**: NestJS (TypeScript)
- **Database**: PostgreSQL (главная БД)
- **Cache**: Redis (кэширование, сессии)
- **API**: REST + WebSockets (real-time)
- **Auth**: JWT + Role-Based Access Control (RBAC)

### Frontend
- **Framework**: React 18+
- **Language**: TypeScript
- **Styling**: Tailwind CSS + Material-UI
- **State**: Redux / Zustand
- **HTTP**: Axios
- **Real-time**: Socket.io

### DevOps & Infrastructure
- **Containerization**: Docker
- **Orchestration**: Kubernetes (EKS)
- **CI/CD**: GitHub Actions
- **Infrastructure**: Terraform + AWS
- **Monitoring**: Prometheus + Grafana
- **Logging**: CloudWatch + ELK Stack

---

## 🚀 Быстрый старт

### Локальная разработка

#### Требования
- Node.js 18+
- Docker & Docker Compose
- PostgreSQL (опционально, если не использовать Docker)
- Git

#### Установка

```bash
# 1. Клонируй репо
git clone https://github.com/generealwest/crm-system.git
cd crm-system

# 2. Установи зависимости
npm install

# 3. Запусти Docker контейнеры
docker-compose up -d

# 4. Мигрируй БД
npm run db:migrate

# 5. Заполни тестовые данные (опционально)
npm run db:seed

# 6. Запусти backend
npm run start:backend

# 7. В другом терминале - запусти frontend
npm run start:frontend
```

### Доступ к приложению

| Компонент | URL |
|-----------|-----|
| Frontend (React) | http://localhost:3001 |
| Backend API | http://localhost:3000/api |
| API Documentation (Swagger) | http://localhost:3000/api/docs |
| Adminer (БД) | http://localhost:8080 |

### Тестовые учетные данные

```
Email: admin@example.com
Password: admin123

Роли в системе:
- ADMIN       - полный доступ
- MANAGER     - управление сделками и объектами
- ACCOUNTANT  - управление финансами
- CONTRACTOR  - доступ к своим работам
- VIEWER      - только чтение
```

---

## 🏗️ Архитектура

### Диаграмма системы

```
┌─────────────────────────────────────────────────────────────────┐
│                     Frontend (React)                            │
│  Dashboard | Sales | Projects | Contractors | Finance | Analytics│
└────────────────────────────┬────────────────────────────────────┘
                             │
                   REST API + WebSockets
                             │
┌─────────────────────────────┴────────────────────────────────────┐
│                    Backend (NestJS)                              │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │ Controllers & Routes                                     │   │
│  │ /api/sales | /api/projects | /api/contractors | ...     │   │
│  └──────────────────────────────────────────────────────────┘   │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │ Business Logic (Services)                                │   │
│  │ Sales Service | Project Service | Finance Service | ...  │   │
│  └──────────────────────────────────────────────────────────┘   │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │ Database Access (TypeORM)                                │   │
│  └──────────────────────────────────────────────────────────┘   │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │ Authentication & Authorization                           │   │
│  │ JWT | RBAC | Audit Logs                                 │   │
│  └──────────────────────────────────────────────────────────┘   │
└────────────────┬──────────────────────┬───────────────────────────┘
                 │                      │
        ┌────────┴──────┐        ┌──────┴──────────┐
        │                │        │                 │
    PostgreSQL        Redis    ElasticSearch    Sentry
    (Main DB)       (Cache)    (Search)       (Monitoring)
```

### Структура проекта

```
crm-system/
├── backend/                    # NestJS backend
│   ├── src/
│   │   ├── modules/           # Бизнес-модули
│   │   │   ├── auth/
│   │   │   ├── sales/
│   │   │   ├── projects/
│   │   │   ├── contractors/
│   │   │   ├── finance/
│   │   │   ├── analytics/
│   │   │   └── notes/
│   │   ├── common/            # Shared utilities
│   │   │   ├── guards/
│   │   │   ├── interceptors/
│   │   │   ├── filters/
│   │   │   └── decorators/
│   │   ├── database/          # TypeORM entities & migrations
│   │   └── main.ts
│   ├── test/                  # Unit & integration tests
│   └── package.json
│
├── frontend/                   # React frontend
│   ├── src/
│   │   ├── components/        # React компоненты
│   │   │   ├── Dashboard/
│   │   │   ├── Sales/
│   │   │   ├── Projects/
│   │   │   ├── Contractors/
│   │   │   ├── Finance/
│   │   │   └── Analytics/
│   │   ├── pages/            # Page components
│   │   ├── services/         # API clients
│   │   ├── store/            # Redux / Zustand
│   │   ├── hooks/            # Custom React hooks
│   │   ├── utils/            # Utilities
│   │   ├── styles/           # Global styles
│   │   └── App.tsx
│   ├── public/
│   └── package.json
│
├── docker/                    # Docker конфигурация
│   ├── docker-compose.yml
│   ├── Dockerfile.backend
│   └── Dockerfile.frontend
│
├── kubernetes/                # K8s manifests
│   ├── deployment.yml
│   ├── service.yml
│   └── ingress.yml
│
├── terraform/                 # Infrastructure as Code
│   ├── main.tf
│   ├── variables.tf
│   └── outputs.tf
│
├── .github/workflows/         # CI/CD
│   ├── lint.yml
│   ├── test.yml
│   └── deploy.yml
│
└── docs/                      # Документация
    ├── ARCHITECTURE.md
    ├── API.md
    ├── DATABASE.md
    └── DEPLOYMENT.md
```

---

## 💻 Разработка

### Команды

```bash
# Backend
npm run start:backend          # Запуск backend (dev mode)
npm run build:backend          # Build production
npm run test:backend           # Запуск тестов
npm run lint:backend           # Lint код

# Frontend
npm run start:frontend         # Запуск frontend (dev mode)
npm run build:frontend         # Build production
npm run test:frontend          # Запуск тестов

# Docker
docker-compose up              # Запуск всех сервисов
docker-compose down            # Остановка сервисов

# Database
npm run db:migrate             # Run migrations
npm run db:seed                # Fill test data
npm run db:reset               # Reset database
```

### Workflow разработки

1. **Создай ветку** из `develop`
   ```bash
   git checkout -b feature/your-feature
   ```

2. **Пиши код** с типизацией (TypeScript)
   ```bash
   npm run lint              # Проверь качество
   npm run test              # Напиши тесты
   ```

3. **Коммит с message** по стандарту
   ```bash
   git commit -m "feat: добавил функцию X"
   ```

4. **Push и создай Pull Request**
   ```bash
   git push origin feature/your-feature
   ```

5. **CI/CD автоматически**
   - Запустит тесты
   - Проверит качество кода
   - Если всё ок → merge в develop

---

## 📚 Документация

| Документ | Описание |
|----------|---------|
| [ARCHITECTURE.md](./docs/ARCHITECTURE.md) | Подробная архитектура системы |
| [API.md](./docs/API.md) | Документация всех API endpoints (50+) |
| [DATABASE.md](./docs/DATABASE.md) | ER диаграмма и схема БД |
| [DEPLOYMENT.md](./docs/DEPLOYMENT.md) | Инструкции по развёртыванию на production |
| [SETUP.md](./docs/SETUP.md) | Подробный setup локальной разработки |

---

## 🔐 Безопасность

- ✅ **Аутентификация**: JWT токены
- ✅ **Авторизация**: Role-Based Access Control (RBAC)
- ✅ **Шифрование**: bcrypt для паролей, TLS для коммуникации
- ✅ **Валидация**: All inputs validated server-side
- ✅ **Audit**: Полное логирование всех изменений
- ✅ **CORS**: Настроена под production
- ✅ **Rate Limiting**: По ролям пользователя
- ✅ **Secrets**: Хранятся в AWS Secrets Manager

---

## 📈 Production Deployment

### Развёртывание на AWS

```bash
# 1. Настрой AWS credentials
aws configure

# 2. Запусти terraform для инфраструктуры
cd terraform
terraform init
terraform plan
terraform apply

# 3. Развёрни приложение
cd ..
./scripts/deploy.sh production

# 4. Проверь статус
kubectl get pods -n crm
```

### Monitoring & Alerts

- **Prometheus**: Сбор метрик (`http://prometheus:9090`)
- **Grafana**: Визуализация (`http://grafana:3000`)
- **CloudWatch**: Логирование AWS
- **Sentry**: Tracking ошибок

---

## 🤝 Контрибьютинг

1. Fork репо
2. Создай feature ветку (`git checkout -b feature/amazing`)
3. Коммит (`git commit -m 'add amazing feature'`)
4. Push (`git push origin feature/amazing`)
5. Open Pull Request

---

## 📋 Roadmap

- [ ] v1.0 - Минимальный функционал (воронка + объекты)
- [ ] v1.1 - Финансы и аналитика
- [ ] v1.2 - Мобильное приложение
- [ ] v1.3 - AI-powered аналитика
- [ ] v2.0 - Интеграции (1C, Telegram, Email)

---

## 📞 Поддержка

- **Issues**: Открывай GitHub Issues для багов
- **Discussions**: Для вопросов и предложений
- **Email**: support@crm-system.com

---

## 📄 License

MIT License - смотри [LICENSE](./LICENSE)

---

## ✨ Спасибо!

Благодарим всех, кто способствует развитию этого проекта! 🚀

**Сделано с ❤️ для строительных компаний**
