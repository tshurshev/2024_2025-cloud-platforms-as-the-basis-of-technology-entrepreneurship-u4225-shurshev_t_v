University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Cloud platforms as the basis of technology entrepreneurship](https://itmo-ict-faculty.github.io/cloud-platforms-as-the-basis-of-technology-entrepreneurship/education/labs/#_2)

Year: 2024/2025

Group: U4225

Author: Shurshev Timofey Valerievich

Lab: Lab3

Date of create: 17.09.2025

Date of finished: 17.09.2025

## Порядок выполнения работы

### Создадим собственный Bucket

<img width="1026" height="215" alt="image" src="https://github.com/user-attachments/assets/6d1be53e-ada8-45f3-9764-8d045957d574" />

### Добавим файлы

<img width="965" height="385" alt="image" src="https://github.com/user-attachments/assets/034344e0-9802-4f06-8123-10e56d1a79b7" />

### Создадим папку и перенесем в неё файлы

<img width="896" height="363" alt="image" src="https://github.com/user-attachments/assets/ad8d46f0-afe5-4b2d-8bb4-1a51da8da1cb" />

### Создадим публичный доступ 

*Я тут ввел не ту роль, хотел Storage object viewer, но из-за невнимательности написал Storage admin. Тем не менее, все остальные шаги отработали верно.*

<img width="697" height="614" alt="image" src="https://github.com/user-attachments/assets/734c945c-be2a-4246-98c1-59379141b30c" />

### Перейдем по публичному URL

<img width="1151" height="555" alt="image" src="https://github.com/user-attachments/assets/2e418294-fa9a-42af-beab-ccd1b4fecf82" />

### Попадем на страничку с нашим файлом

<img width="1144" height="988" alt="image" src="https://github.com/user-attachments/assets/0c2336d6-d8ea-4322-9671-e529a01cf1e5" />

## Выводы
В ходе лабораторной работы были успешно изучены основы работы с объектным хранилищем Google Cloud Storage. Были выполнены и проанализированы следующие ключевые аспекты:

1.  **Создание и конфигурация бакета:** Бакет является основным контейнером для хранения данных в GCS. Важно понимать влияние выбора региона (задержки, стоимость) и класса хранения (частота доступа, цена) на будущий сервис
2.  **Загрузка и организация данных:** GCS предоставляет простой и понятный интерфейс для управления объектами. Важно помнить, что "папки" являются виртуальными и реализованы через префиксы в именах объектов, что является общей концепцией для объектных хранилищ в противовес блочным и файловым
3.  **Управление доступом:** Гибкая модель IAM GCS позволяет тонко настраивать права как на уровень всего бакета, так и на отдельные объекты
4.  **Доступ к данным:** Публичный доступ через сгенерированные URL-адреса позволяет легко встраивать объекты из GCS в веб-страницы или делиться ими

**Главное преимущество GCS**, которое было продемонстрировано — это простота использования, масштабируемость (можно хранить от мегабайт до петабайт данных без изменения подхода) и тесная интеграция с другими сервисами Google Cloud, что делает его идеальным хранилищем для данных приложений, бекапов и статических сайтов.
