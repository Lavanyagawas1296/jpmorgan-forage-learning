05️⃣ Kafka & Event-Driven Architecture
1️⃣ What Confused Me Initially

What exactly is Kafka?

Why do we need it if REST APIs already work?

What is Producer and Consumer?

What is a Topic?

When should we use event-driven architecture?

2️⃣ What I Understood Finally
🔹 What is Apache Kafka?

Apache Kafka is a distributed event streaming platform.

It is used for:

Real-time data streaming

Microservices communication

Handling large-scale systems

Asynchronous processing

Think of it like a messaging system for backend services.

3️⃣ Why Not Just Use REST?

REST is:

Synchronous

Request → Response

Client waits for response

Kafka is:

Asynchronous

Fire-and-forget

Services communicate through events

Example:

Bank transaction system:

Transaction Service → Sends event → Kafka
Fraud Service → Listens to event
Notification Service → Listens to event

No direct coupling.

4️⃣ Core Kafka Concepts
🔹 Producer

Sends message to Kafka topic.

Example:

@Autowired
private KafkaTemplate<String, String> kafkaTemplate;

public void sendMessage(String message) {
    kafkaTemplate.send("user-topic", message);
}
🔹 Topic

A channel where messages are stored.

Think of it like:
Queue name

Example:

user-topic
payment-topic
order-topic
🔹 Consumer

Reads messages from topic.

@KafkaListener(topics = "user-topic")
public void listen(String message) {
    System.out.println("Received: " + message);
}
🔹 Broker

Kafka server that stores messages.

5️⃣ How Kafka Flow Works

Producer
↓
Kafka Topic
↓
Consumer

Message remains in topic until consumed.

6️⃣ Event-Driven Architecture
What is it?

System reacts to events instead of direct calls.

Example Event:

User Registered

Payment Completed

Order Placed

Instead of:

Service A → Directly calls → Service B

We do:

Service A → Publish Event
Service B → Listens to Event

This makes system:

Loosely coupled

Scalable

Independent

7️⃣ Why Kafka is Powerful

High throughput

Fault tolerant

Distributed system

Horizontal scaling

Used in real big systems

Companies using Kafka:

Netflix

Uber

LinkedIn

Banks

8️⃣ Kafka vs REST Comparison
Feature	REST	Kafka
Type	Synchronous	Asynchronous
Coupling	Tight	Loose
Scalability	Medium	High
Real-time streaming	❌	✅
Microservices friendly	Limited	Very Good
9️⃣ Real-World Example (Banking System)

User makes payment.

Payment Service processes transaction

Sends event → "PaymentCompleted"

Fraud Detection Service listens

Notification Service listens

Analytics Service listens

No service directly depends on each other.

That is real backend architecture.

🔟 Key Annotations in Spring Kafka
Annotation	Purpose
@EnableKafka	Enables Kafka
@KafkaListener	Consumer listener
KafkaTemplate	Producer utility
1️⃣1️⃣ What I Learned

REST is not enough for scalable systems

Kafka enables event-driven design

Producer and Consumer are independent

Event-based communication reduces dependency

Used in large-scale enterprise systems

1️⃣2️⃣ Key Takeaways

Kafka is used for asynchronous messaging

Topic acts like a message channel

Producer sends, Consumer listens

Event-driven architecture increases scalability

Essential concept for backend engineering
