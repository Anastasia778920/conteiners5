# Задание
1) создать сервис, состоящий из 2 различных контейнеров: 1 - веб, 2 - БД
2) далее необходимо создать 3 сервиса в каждом окружении (dev, prod, lab)
3) по итогу на каждой ноде должно быть по 2 работающих контейнера
4) выводы зафиксировать

# Выполнение 
Применяем команду: 

        docker-compose up -d

Присваиваем тэг: 
        
        docker node update --label-add TAG=dev 

        docker node update --label-add TAG=prod 

        docker node update --label-add TAG=lab 

Команда
        
        docker compose -f compose.prod.yaml -f compose.dev.yaml -f compose.lab.yaml up -d
создаст сервисы на главной ноде и можно будет приступать к раскидке 

Раскидка: 

        docker stack deploy --compose-file <compoose.dev.yaml> dev

        docker stack deploy --compose-file <compoose.prod.yaml> prod

        docker stack deploy --compose-file <compoose.lab.yaml> lab

