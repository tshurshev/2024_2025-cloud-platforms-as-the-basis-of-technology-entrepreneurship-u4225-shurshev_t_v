University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Cloud platforms as the basis of technology entrepreneurship](https://itmo-ict-faculty.github.io/cloud-platforms-as-the-basis-of-technology-entrepreneurship/education/labs/#_2)

Year: 2024/2025

Group: U4225

Author: Shurshev Timofey Valerievich

Lab: Lab4

Date of create: 17.09.2025

Date of finished: 17.09.2025


### Цель работы
Спроектировать и обосновать архитектуру MVP AI-приложения для трех этапов его жизненного цикла (PoC, Beta, Production) в Google Cloud Platform, а также провести оценку затрат на его эксплуатацию.

### Исходные данные
*   Приложение: Анализ эмоциональный окраски текстовых отзывов .
*   Стек: Python, ML-библиотеки, микросервисная архитектура.
*   Нагрузка:
    *   PoC: ~100 запросов/день.
    *   Beta: ~5 000 запросов/день.
    *   Production: ~100 000 запросов/день, требования к отказоустойчивости.

### 1. Проектирование архитектуры

#### 1.1. Этап 1: Начальное состояние (Proof of Concept)
Цель: Минимизация cost и времени на развертывание.

Схема архитектуры:

<img width="603" height="454" alt="image" src="https://github.com/user-attachments/assets/33f02d0d-890c-4b7b-bc03-98781b2a1348" />


Описание:
*   Frontend: Статический SPA(Single-Page Application), размещенный в Cloud Storage.
*   Backend: Микросервис на Cloud Run. Обрабатывает запросы, использует предобученную модель.
*   Данные: Постоянное хранение не требуется. Логируются в Cloud Logging.

#### 1.2. Этап 2: Тестирование партнерами (Beta)
Цель: Стабильность, сбор данных.
Схема архитектуры:
(Вставьте ссылку на изображение из draw.io или вставьте скриншот)

Описание:
*   Frontend: Тот же Cloud Storage, подключен Cloud CDN.
*   Backend: Cloud Run с увеличенным лимитом экземпляров.
*   Данные: Firestore (NoSQL) для сохранения запросов и результатов анализа.
*   Мониторинг: Cloud Monitoring, Cloud Logging.

#### 1.3. Этап 3: Продовое решение (Production)
Цель: Высокая доступность, масштабируемость.
Схема архитектуры:
(Вставьте ссылку на изображение из draw.io или вставьте скриншот)

Описание:
*   Frontend: Cloud Storage + Cloud CDN + Global HTTPS Load Balancer.
*   Backend: Cloud Run (или GKE для полного контроля).
*   Кэш: Memorystore (Redis) для кэширования повторяющихся запросов.
*   Данные: Cloud SQL (PostgreSQL) с включенным HA.
*   Безопасность: Cloud IAP / Identity Platform.

### 2. Расчет экономической модели

Расчеты произведены с помощью [Google Cloud Pricing Calculator](https://cloud.google.com/products/calculator) для региона `europe-west1`.
*   Этап PoC (в мес.) = Cloud Run(~0) + Cloud Storage(~0) = ~1$
  <img width="482" height="458" alt="image" src="https://github.com/user-attachments/assets/5b68387d-0c62-490c-9eca-2fd56ea91809" />
  
*   Этап Beta (в мес.) = Cloud Run(~6) + Cloud Storage(~0) + Firestore(~0) + Cloud CDN(~6) = ~12$
  <img width="398" height="617" alt="image" src="https://github.com/user-attachments/assets/a04fcc9c-4924-4333-bf91-e8986ce140cc" />
  
*   Этап Production (в мес.) = Cloud Run(~123) + Cloud Storage(~0) + Cloud SQL(~73) + Cloud CDN(~15) + Load Balancer(~20) = ~140$
  <img width="527" height="743" alt="image" src="https://github.com/user-attachments/assets/11725c85-472e-4138-bc83-a36ed7a85a0a" />
                                                                                  

### 3. Обоснование выбора ресурсов

*   Cloud Run: Основной выбор для backend. Позволяет избежать управления инфраструктурой, что критически важно на ранних этапах для быстрого старта и валидации гипотезы. Автомасштабирование и оплата только за реальное использование ресурсов делают его эффективным решением для всех этапов, вплоть до прода
*   Firestore -> Cloud SQL: На этапе beta важна скорость разработки и гибкость данных, поэтому выбран  NoSQL-инструмент Firestore. На этапе production приоритеты смещаются в сторону надежности, согласованности данных и сложных запросов, поэтому производится миграция на  реляционную БД Cloud SQL
*   Global Load Balancer + CDN: На production-этапе необходимо обеспечить низкую задержку и высокую доступность для глобальной аудитории. Load Balancer распределяет трафик между backend-экземплярами, а CDN кэширует статику на edge-локациях, разгружая backend и ускоряя загрузку для конечных пользователей
*   Memorystore (Redis): Вводится на production-этапе для кэширования результатов анализа часто повторяющихся отзывов. Это позволяет значительно снизить нагрузку на backend и базу данных, уменьшая время отклика и общую стоимость вычислений.

### Выводы

В ходе работы была спроектирована трехэтапная архитектура для MVP AI-приложения в Google Cloud Platform. Ключевым принципом выбора сервисов был баланс между стоимостью, простотой управления и функциональностью на каждом этапе жизненного цикла продукта:

1.  PoC-этап максимально использует serverless-подход (Cloud Run, Cloud Storage) для достижения практически нулевой стоимости и минимального времени развертывания.
2.  Beta-этап добавляет managed-сервисы для данных и мониторинга (Firestore, Cloud Monitoring), обеспечивая стабильность для первых пользователей без резкого роста затрат.
3.  Production-этап фокусируется на отказоустойчивости, производительности и глобальной доступности, для чего в архитектуру добавляются Global Load Balancer, CDN, реплицированная БД и кэш.

Данный подход позволяет постепенно наращивать сложность и надечность инфраструктуры параллельно с ростом аудитории и требований к приложению, избегая преждевременной оптимизации и избыточных затрат на ранних этапах.
