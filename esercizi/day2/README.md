# day2
Document DB NoSQL (MongoDB)
---

## 1) Senza Docker

- installare Robo3T (gratis, non Studio3T): https://robomongo.org
- connettersi
        - nuova connessione
        - From URI: (`inserire-stringa-condivisa-a-lezione`)
        - name: reti-big-data-demo2
        - authentication > tick perform authentication (`user-e-pass-condivisi-a-lezione`)
        - test
        - save
        - doppio click o connect
- click destro su db: open shell
- nell'ordine:
        `db`
        `db.getCollectionNames()`
        `db.getCollection("pizzas").find().count()`

## 2) Con Docker

- `cd mongo-local`
- `docker-compose up -d`
- su browser, andare su `localhost:3100`
	- Add server -> `mongo1:27017`
- `mongosh`
	- `docker exec -it mongo-local-mongo1-1 mongosh`
		- `db`
		- `show collections`
		- `db.pizzas.find().count()`
	- `exit`
- `docker-compose down`