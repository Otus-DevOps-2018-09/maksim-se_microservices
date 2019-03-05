# maksim-se_microservices
maksim-se microservices repository

# HW-12
## в процессе выполнения работы сделано:
1. Установлен docker
2. Запущен контейнер hello world!
3. Отработали выполнение различных команд docker
4. Закоммитен образ из запущенного контейнера
5. Просмтрена разница между образом и контейнером.
6. Удалены образы и контейнеры.


# HW-13
## в процессе выполнения работы сделано:
1. создан новый проект в gcp
2. добавлен новый проект на локальной машине, установлен docker на локальной машине, docker-machine в облаке
3. подключились к докеру-gcp и проверили изоляцию процессов
4. написаны скрипты
5. создан образ из созданного Dokerfile
6. запусщен контейнер в облаке, приложение доступно по порту 9292
7. запушен образ в dockerhub
8. для проверки локально запущен образ из dockerhub, приложение доступно на локалхосте
9. пересоздали контейнер для проверки.

## TODO: выполнить задание со *

# HW-14
## в процессе выполнено
1. загружены исходники с вашего репозитория
2. написаны Dokerfile для сервисов post, comment, ui
3. собрали образы сервисов, скачали образ монги
4. запустили контейнеры
5. создал образы на базе alpine. Размеры уменьшелись сущеснтвенно:
   maks123/post          2.0-alpine          117MB
   maks123/comment       2.0-alpine          56.5MB
   maks123/ui            2.0-alpine          57.8MB
   maks123/ui            1.0                 778MB
   maks123/comment       1.0                 775MB
   maks123/post          1.0                 198MB
6. Добавлен volune для базы mongo, что подволило сохнарять состояние базы при перегрузках контейнеров

# HW-15
## в процессе выполнено
1. были запущены контейнеры с различными драйверами: none, host, bridge
2. созданы 2 сети: back_net, front_net
3. изучили правила iptables, создаваемый докером для контейнеров
4. написали для docker-conpose конфигурацию с параметрами
5. имя проекта задается в файле .env
6. создан docker-compose.override.yml с параметрами запуска puma для ruby приложений в дебаг режиме с двумя воркерами.  Для реализации унификации образов приложений надо создать еще один контейнер с приложением, которое клонирует репозиторий https://github.com/express42/reddit.git в определенную директорию appsrv, монтируемую в отдельный volume. Потом этот volume монтируется сервисы ui, post и comment.
## TODO: реализовать задание со *

# HW-16
## в процессе выполнено
1. Создана ВМ с помощью docker-machine
2. Запущен и настроен gitlab в контейнере.
3. создана группа, проект
4. залили в проект исходники
5. настроили pipeline .gitlab-ci.yml
6. создали и зарелистрировали gitlab-runner
7. отработал pipeline, сбилдился проект и успешно прошли тесты

# HW-17
## в процессе сделано
1. создал окружение
2. настроили ручное запуск раннеров дял stage и production
3. добавил создание динамических окружений

## TODO: реализовать задание со * и **

# HW-18
## в процессе выполнено
1. запущен Prometheus в докере
2. создан собственный образ Prometheus с конфигурацией нашего приложения
3. пересобрали приложения и Prometheus 
4. подняли приложения и Prometheus, убедились что Prometheus запустился и видит сервисы
5. подняли node-exporter для сбора статистики с хоста

   Ссылка на dockerhub: https://hub.docker.com/u/maks123

# HW-19
## в процессе выполнено
1. создан хост для работы
2. разделил docker-compose.yml на 2 файла: с приложение и с мониторингом
3. добавили cAdvisor, который занимается мониторингом ресурсов докер-контейнеров. Открыли порт 8080 для cAdvisor
4. добавили grafana, добавили источники для метрик контейнеров и приложений
5. добавили alertmanager и настроили оповещение в slack при статусе "down" какого-нибудь сервиса

## TODO: реализовать задание со * / ** / *** (конда-нибудь, судя по объёму работы ))))
 
# HW-20
## в процессе выполнено
1. залита новая версия приложения
2. сменил tag на logging
3. запущен EFK
4. настроили вывод логов контейнеров в fluent
5. прикрутили фильтры ввиде регулярок
6. настроили грок-шаблоны

## TODO: реализовать задание со * / ** / *** (конда-нибудь, судя по объёму работы ))))

# HW-21
## в процессе выполнено
1. написаны депройменты для сервисов mongo, comment, post, ui
2. утановили k8s по инструкции https://github.com/kelseyhightower/kubernetes-the-hard-way 
3. созданы поды из созданных манифестов, поды поднялись.
```
red02@SKRS1358 ~/otus/maksim-se_microservices/kubernetes/the_hard_way (kubernetes-1) $ kubectl get pods
NAME                                 READY   STATUS    RESTARTS   AGE
busybox-bd8fb7cbd-pzjhr              1/1     Running   0          31m
comment-deployment-c5fb5d4d7-887x6   1/1     Running   0          12m
mongo-deployment-6fdb44964c-l5hcp    1/1     Running   0          13m
nginx-dbddb74b8-d8r9z                1/1     Running   0          30m
post-deployment-b668dc698-9l789      1/1     Running   0          12m
ui-deployment-6bdc89d75-nmwx2        1/1     Running   0          12m
untrusted                            1/1     Running   0          27m
red02@SKRS1358 ~/otus/maksim-se_microservices/kubernetes/the_hard_way (kubernetes-1) $
```

# HW-22
## в процессе выполнено
1. установлен kubectl
2. установлен minikube
3. созданы деплойменты и сервисы
4. добавили алиасы для сервисов, что б сервисы видели базу данных
5. создали dev окружение, запустили в нем приложение
6. создали кластер k8s в gke, перенесли в namespace dev приложение, создали правило файрвола и подключились к приложению из вне. Скриншот приложен.

# HW-23
## в процессе выполнено
1. создали ui-service типа NodePort с открытым портом на всех нодах: куб сам переправляет запросы на поды
2. создали ui-service типа LoadBalancer: используется внешний LB, который форвардит запросы на ноды автоматом
3. создали ingress для ui, и вернули NodePort
4. создали сертификаты, с ним создали секрет, переключили приложение на https
5. создали networkPolicy для mongo с доступом только для comment, но по файкту "факир был пьян" и оно не работало, создали правило и для post
6. создали persistentVolume и persistentVolumeClaim для деплоймента mongo, теперь данные базы сохранаются и выделяются динамически

# HW-24
## в процессе выполнено
1. установили helm и tiller, выдали права на под тиллера
2. написаны шаблоны миктосервисов. поиграоись с релизами
3. создали _helpers.tpl
4. создали основной chart reddit с ссылками на микросервисы
5. установили gitlab-omnibus, создали группу, проекты (ui, post, comment, reddit-deploy), загрузили соответствующие компоненты по проектам
6. настроили gitlab-ci для reddit-deploy, создали автоматическое создание окружений для staging и proda, настроели деплой среды по-кнопкам.

