MONGO_INITDB_ROOT_USERNAME:=$(shell cat .env | grep "MONGO_INITDB_ROOT_USERNAME" | awk -F '=' '{print $$2}')
MONGO_INITDB_ROOT_PASSWORD:=$(shell cat .env | grep "MONGO_INITDB_ROOT_PASSWORD" | awk -F '=' '{print $$2}')

start:
	docker-compose -f ./mongo.yml up -d --build

stop:
	docker-compose -f ./mongo.yml down

repair:
	docker-compose -f ./mongo.yml run mongo mongod --repair

restart: stop start

logs:
	docker logs -f --tail 100 $$(docker container ls -a | grep '\-mongo' | grep -v "mongo-express" | awk '{print $$1}')

bash:
	docker run -it --network $$(docker network ls | grep 'mytgbot-mongo' | awk '{print $$2}') --rm mongo:7 mongo \
	--host $$(docker ps | grep '\-mongo' | grep -v "mongo-express" | awk '{print $$NF}') \
	-u${MONGO_INITDB_ROOT_USERNAME} -p${MONGO_INITDB_ROOT_PASSWORD} --authenticationDatabase=admin mytgbot

stat:
	docker run -it --network $$(docker network ls | grep 'mytgbot-mongo' | awk '{print $$2}') --rm mongo:7 mongostat \
        --host $$(docker ps | grep '\-mongo' | grep -v "mongo-express" | awk '{print $$NF}') \
        -u${MONGO_INITDB_ROOT_USERNAME} -p${MONGO_INITDB_ROOT_PASSWORD} --authenticationDatabase=admin

top:
	docker run -it --network $$(docker network ls | grep 'mytgbot-mongo' | awk '{print $$2}') --rm mongo:7 mongotop \
        --host $$(docker ps | grep '\-mongo' | grep -v "mongo-express" | awk '{print $$NF}') \
        -u${MONGO_INITDB_ROOT_USERNAME} -p${MONGO_INITDB_ROOT_PASSWORD} --authenticationDatabase=admin
