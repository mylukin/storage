start:
	docker-compose --env-file ./.env -f ./es.yml up -d --build

stop:
	docker-compose --env-file ./.env -f ./es.yml down

restart: stop start

logs:
	docker logs -f --tail 100 $$(docker container ls -a | grep 'es:latest' | awk '{print $$1}')

bash:
	docker exec -it $$(docker container ls -a | grep 'es:latest' | awk '{print $$1}') bash

