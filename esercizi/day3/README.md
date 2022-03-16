# day3

+ Visualizzazione Kafka [online](https://softwaremill.com/kafka-visualisation/)
+ Lettura e scrittura su Kafka (via Docker)

---

## kafka-local (cluster+kowl)

### run environment
```bash
docker-compose up -d  # avvio
docker ps -a          # verifica container in esecuzione
docker-compose down   # spegnimento
```

## kafka-shell (Aiven data producer)
Generatore di dati simulati per: 
+ pizza
+ userbehaviour
+ stock
+ realstock
+ metric

### run client shell

```bash
docker run \
    -it \
    --rm \
    --name kafka-shell \
    --hostname kafka-shell \
    --env DATAGEN="pizza" \
    --network host \
    docker.io/gabrielecorni/kafka-shell:master-latest
```

### create new topic
    kafka-topics.sh --bootstrap-server localhost:9092 --create --topic reti-course --partitions 3 --replication-factor 1

### describe topic 
    kafka-topics.sh --bootstrap-server localhost:9092 --describe --topic reti-course

### delete topic
    kafka-topics.sh --bootstrap-server localhost:9092 --delete --topic reti-course

### write to topic 
    kafka-console-producer.sh --bootstrap-server localhost:9092 --topic reti-course
> **NOTA:**  
> ciao da gabriele  --> Text  
> eurovita          --> Text  
> [1,2,3]           --> JSON!

### read from topic
    kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic reti-course --from-beginning

### generate fake data
```bash
cd python-fake-data-producer-for-apache-kafka

python3 main.py --host localhost --port 9092 --topic-name reti-course --nr-messages 15 --max-waiting-time 5 --subject pizza 
```
> **NOTA:**  
> I messaggi con stessa chiave finiscono sempre sulla stessa partizione.