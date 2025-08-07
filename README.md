# Домашнее задание к занятию 14 «Средство визуализации Grafana»


## Обязательные задания

### Задание 1

1. Используя директорию [help](./help) внутри этого домашнего задания, запустите связку prometheus-grafana.
1. Зайдите в веб-интерфейс grafana, используя авторизационные данные, указанные в манифесте docker-compose.
1. Подключите поднятый вами prometheus, как источник данных.
1. Решение домашнего задания — скриншот веб-интерфейса grafana со списком подключенных Datasource.

   <img width="1530" height="683" alt="image" src="https://github.com/user-attachments/assets/fcf05fdb-c894-41c1-a645-b89e74f9270c" />


## Задание 2

Изучите самостоятельно ресурсы:

1. [PromQL tutorial for beginners and humans](https://valyala.medium.com/promql-tutorial-for-beginners-9ab455142085).
1. [Understanding Machine CPU usage](https://www.robustperception.io/understanding-machine-cpu-usage).
1. [Introduction to PromQL, the Prometheus query language](https://grafana.com/blog/2020/02/04/introduction-to-promql-the-prometheus-query-language/).

Создайте Dashboard и в ней создайте Panels:

- утилизация CPU для nodeexporter (в процентах, 100-idle);

avg by(instance)(rate(node_cpu_seconds_total{job="nodeexporter",mode="idle"}[$__rate_interval])) * 100

- CPULA 1/5/15;
avg by (instance)(rate(node_load1{}[$__rate_interval]))
avg by (instance)(rate(node_load5{}[$__rate_interval]))
avg by (instance)(rate(node_load15{}[$__rate_interval]))


- количество свободной оперативной памяти;

node_memory_MemAvailable_bytes{instance="nodeexporter:9100", job="nodeexporter"}



- количество места на файловой системе.

node_filesystem_free_bytes{fstype="ext4",instance="nodeexporter:9100",job="nodeexporter"}

Для решения этого задания приведите promql-запросы для выдачи этих метрик, а также скриншот получившейся Dashboard.


<img width="1642" height="734" alt="image" src="https://github.com/user-attachments/assets/2cf5f8d4-d2b3-489e-86d8-7f8d88ca335e" />




## Задание 3

1. Создайте для каждой Dashboard подходящее правило alert — можно обратиться к первой лекции в блоке «Мониторинг».
1. В качестве решения задания приведите скриншот вашей итоговой Dashboard.

<img width="1715" height="889" alt="image" src="https://github.com/user-attachments/assets/a4d79c21-2ccf-4b55-8e44-0ed6ddd03840" />




## Задание 4

1. Сохраните ваш Dashboard.Для этого перейдите в настройки Dashboard, выберите в боковом меню «JSON MODEL». Далее скопируйте отображаемое json-содержимое в отдельный файл и сохраните его.
1. В качестве решения задания приведите листинг этого файла.

https://github.com/olegveselov1984/10-monitoring-03-grafana/blob/05e0394e60a76868c2fd7755dabc12ff3ada608a/JSON%20Model

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
