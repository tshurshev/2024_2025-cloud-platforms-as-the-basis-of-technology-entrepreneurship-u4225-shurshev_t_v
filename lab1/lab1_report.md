University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Cloud platforms as the basis of technology entrepreneurship]([https://](https://itmo-ict-faculty.github.io/cloud-platforms-as-the-basis-of-technology-entrepreneurship/education/labs/#_2)) 

Year: 2024/2025

Group: U4225

Author: Shurshev Timofey Valerievich

Lab: Lab1

Date of create: 17.09.2025

Date of finished: 17.09.2025



Ход работы
1. Создание Service Account

В разделе IAM & Admin -> Service Accounts был создан новый сервисный аккаунт.

    Имя: tshurshev-sa-lab1 
  
    Роль: Storage Admin 

2. Создание виртуальной машины (Compute Engine)

В разделе Compute Engine -> VM instances была создана виртуальная машина со следующими параметрами:

    Имя: tshurshev-vm-lab1
   
    Machine type: e2-micro
   
    Настройки доступности: Spot

3. Копирование файлов из Cloud Storage Bucket

Был подключен к созданной VM через SSH . В открывшемся терминале были выполнены следующие команды:
<img width="640" height="484" alt="image" src="https://github.com/user-attachments/assets/cd21ea5d-ab97-4475-a52f-fd2f0f26a0e8" />

4. Изменение прав доступа Service Account и проверка
 
Были изменены права доступа созданного сервисного аккаунта.
<img width="775" height="51" alt="image" src="https://github.com/user-attachments/assets/0fc509b1-0771-4ee5-8567-20ace5b054e0" />

После этого была проведена попытка повторного выполнения команды копирования файлов из bucket.

<img width="814" height="209" alt="image" src="https://github.com/user-attachments/assets/1fcb267e-410f-401b-b219-16404818c102" />

5. Удаление созданных ресурсов
   
По окончании работы все созданные ресурсы были удалены 


Выводы:

В ходе лабораторной работы:

Было получено практическое знакомство с интерфейсом Google Cloud Console.

Изучен принцип работы с сервисными аккаунтами (Service Accounts) и ролями (IAM). Было наглядно продемонстрировано, что роли определяют уровень доступа к ресурсам GCP. Сервисный аккаунт с ролью Storage Admin имел права на чтение данных из Cloud Storage, а Compute Viewer не дает доступа к операциям с данными Storage, что и привело к ошибке 403 при попытке копирования файлов.

Получен опыт создания и настройки виртуальной машины (Compute Engine) в облаке, в том числе с использованием прерываемых экземпляров (Spot), что позволяет снизить стоимость вычислений.

Освоена базовая работа с утилитой командной строки gsutil для взаимодействия с Storage.

Закреплена важная практика удаления неиспользуемых ресурсов для оптимизации затрат — фундаментальный принцип работы с облачными платформами.

Работа успешно завершена, все цели достигнуты.
