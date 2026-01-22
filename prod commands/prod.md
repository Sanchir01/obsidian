321Employ -password

sudo docker-compose -f docker-compose.yml up -d --build - build new container rabbit-saver

sudo docker logs -f rabbit-saver_rabbit-saver_1 -посмотреть логи

sudo docker-compose -f docker-compose.prod.yml up -d db - поднятие employee db

sudo docker system prune



Логин:SEmgushov 
Пароль:1qazXDR%
В Гит с этими данными пробовал?

виртуала адрес: 172.20.0.197
ssh aivanov@172.20.0.197
пароль: 321Employ

glm-workpulse
10.0.83.13
glmuser
MndrNgHCmLX5YL3U
настроен sudo



sudo docker compose -f docker-compose.prod.yml up gateway



gitlab
Логин:SEmgushov 
Токен: wA24qyoioEJC24tCCxSz
Пароль: 1qazXDR%


docker dump
docker cp ./synchro_dump.sql atssynchronizer-db-1:/tmp/synchro_dump.sql


docker exec -it atssynchronizer-db-1 psql -U postgres -d ats_synchronizer_wrk -h localhost -p 5432 -f ./tmp/synchro_dump.sql



token gitlab
ZtPjcXYBe_u1TpPYYxVP