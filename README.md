# Work with kafka and golang for event driven programmming

- create events and they frow through a stream called Kafka
- Multiple services can use those events. You need to define those events for both consumers and publishers

## KAFKA

- microservices can publish events
- microservices can subscribe to events
- kafka can store events for later retrieval
- kafka can replay events later in the event of failure
- kafka can transform or process events

### More on KAFKA

- event are organised and stored in topics. An example would be `Payments` were all events related to payments can be stored.
- define how long kafka can hold events, after that they can be discarded
- kafka is fault tolerant

### KAFKA Zookeeper

- kafka cluster is managed by kafka brokers called zookeeper

# Setup

1. Run :
```bash
docker compose -d up
```
2. Start producer:
```bash
cd producer
go run main.go
```

3. Start consumer:
```bash
cd worker
go run main.go
```

Try it out by sending post request to port :3000:
```bash
curl --location --request POST '0.0.0.0:3000/api/v1/comments' \
--header 'Content-Type: application/json' \
--data-raw '{ "text":"message 1" }'

curl --location --request POST '0.0.0.0:3000/api/v1/comments' \
--header 'Content-Type: application/json' \
--data-raw '{ "text":"message 2" }'
```