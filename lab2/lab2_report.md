University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Cloud platforms as the basis of technology entrepreneurship](https://itmo-ict-faculty.github.io/cloud-platforms-as-the-basis-of-technology-entrepreneurship/education/labs/#_2)

Year: 2024/2025

Group: U4225

Author: Shurshev Timofey Valerievich

Lab: Lab2

Date of create: 17.09.2025

Date of finished: 17.09.2025

### Запустил Cloud Run

<img width="1309" height="352" alt="image" src="https://github.com/user-attachments/assets/a87d4bbf-23af-4bd5-b0d5-f17884285002" />

### Протестировал endpoint

<img width="921" height="693" alt="image" src="https://github.com/user-attachments/assets/1479bcdc-e1d3-4ca6-baed-546b9e2945f6" />

### Познакомился с метриками и логами 

#### Метрики

<img width="1510" height="470" alt="image" src="https://github.com/user-attachments/assets/7c24311c-2aa0-4aa3-8367-6997f5c6157a" />

#### Логи

<img width="1535" height="615" alt="image" src="https://github.com/user-attachments/assets/4f14ebae-8087-47b8-b071-13caad4e5c3a" />

### Изменил порт

Ожидал, что что-то вылетит, но, по итогу, нормально отработало(менял порты на 8090 и на этот)

<img width="1038" height="318" alt="image" src="https://github.com/user-attachments/assets/38b6f785-7c07-4bde-9bde-358a0c79c2f8" />

### Сделал переключение трафика и протестировал его

<img width="770" height="235" alt="image" src="https://github.com/user-attachments/assets/e14afea0-889b-4408-9952-9ad73dcb66c6" />


<img width="1211" height="817" alt="image" src="https://github.com/user-attachments/assets/718ef064-2ea8-4141-95e5-2b110df9c10c" />

Хотел просмотреть подробнее в метриках, но не разобрался, какой график мне нужен. Поэтому полез в логи, там было уведоимление об успешности обоих Revision

### Выводы
В ходе лабораторной работы был успешно развернут и протестирован сервис в Google Cloud Run. Были изучены ключевые особенности сервиса:
1.  **Простота развертывания:** Cloud Run позволяет быстро развернуть контейнер из готового образа
2.  **Автомасштабирование/самозапуск:** Сервис автоматически масштабируется до нуля, когда нет запросов (это позволяет экономить ресурсы и деньги), и сам запускается при новом трафике
3.  **Мониторинг:** Логи и метрики предоставляют всю необходимую информацию для анализа работы приложения и устранения неисправностей
4.  **Управление трафиком** : Позволяет перенаправлять трафик для распределения нагрузки и других задач
