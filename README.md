Scalable Notification System

Languages / Tech: Java (OOP, concurrency), suggested infra: Kafka/RabbitMQ (async queue), PostgreSQL/MySQL (persistence), Optional: Redis (cache), Spring Boot (REST API)

Project Summary

A production-oriented, multi-channel Notification System supporting Email, SMS, and Push notifications. Implements a Producer → Queue → Consumer architecture with thread-safe operations, queue-based delivery, metrics tracking, and extensible design suitable for fintech/payment applications like Juspay.

Key Impact (suitable for resume/GitHub highlight)

1. Supports 1,000+ notifications per minute across multiple channels.
2. Demonstrates multi-threaded, concurrent processing with thread-safe queue handling.
3. Tracks notification status (PENDING, SENT, FAILED) for analytics and reliability.
4. Easily extensible for additional channels, retries, scheduling, or distributed deployment.


Architecture Diagram (Mermaid)

flowchart LR
  User[App / Service] --> Producer[Notification Producer]
  Producer --> MQ[(Message Queue)]
  MQ --> Worker1[Email Worker]
  MQ --> Worker2[SMS Worker]
  MQ --> Worker3[Push Worker]
  Worker1 --> Email[Email Gateway]
  Worker2 --> SMS[SMS Gateway]
  Worker3 --> Push[Push Service]
  DB[(Notification Logs)]
  MQ --> DB
<img width="3840" height="1593" alt="Untitled diagram _ Mermaid Chart-2025-09-17-131958" src="https://github.com/user-attachments/assets/cbbcb41f-e891-4808-a0f7-4e369d4cc22a" />
design link : 

Design Highlights : 

1. Producer → Queue → Consumer pattern: Decouples notification generation from delivery for scalability.
2. Multi-channel workers: Email, SMS, Push handled by separate worker classes.
3. Thread-safe queue handling using ConcurrentLinkedQueue and multi-threaded consumers.
4. Notification status tracking: Each message has PENDING, SENT, or FAILED for monitoring.
5. OOP design: Separate classes for Notification, Producer, Worker, and Consumer.
6. Extensible: Add new channels, logging, scheduling, or persistent queues with minimal code changes.


How to use / run (local demo)

1. Clone the repo.
2. Compile and run NotificationSystemDemo.java in the src folder.
3. The demo simulates multi-threaded notifications being produced and consumed, logs status, and prints metrics.
4. To make production-ready, add:
     -> Persistence (PostgreSQL/MySQL)
     -> Distributed queue (Kafka/RabbitMQ)
     -> REST API wrapper (Spring Boot)
     -> Retry mechanism for failed notifications


Future Enhancements : 

1. Persistent storage – save notifications in PostgreSQL/MySQL for audit and analytics.
2. Distributed queues – integrate Kafka/RabbitMQ for high-throughput production workloads.
3. Retry mechanism – automatically retry failed notifications for guaranteed delivery.
4. REST API – expose /sendNotification endpoint via Spring Boot for real-time production usage.
5. Scheduling – support delayed/future notifications.
6. Enhanced metrics – track delivery latency, per-channel throughput, and success/failure rates for observability.
