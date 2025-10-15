321Employ -password

sudo docker-compose -f docker-compose.yml up -d --build - build new container rabbit-saver

sudo docker logs -f rabbit-saver_rabbit-saver_1 -посмотреть логи

sudo docker-compose -f docker-compose.prod.yml up -d db - поднятие employe db

sudo docker system prune