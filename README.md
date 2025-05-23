1. How much data does the publisher send in one run?
In your code, the publisher sends 5 messages, each containing a user_id and user_name string. The exact size depends on the string lengths, but it's small—likely under 1 KB total. It's just basic text data, so it’s very lightweight.

2. The same AMQP URL in publisher and subscriber—what does it mean?
Using the same URL (amqp://guest:guest@localhost:5672) means both publisher and subscriber connect to the same message broker—in this case, a RabbitMQ server running locally. The guest:guest part is the default username and password, and localhost:5672 points to the broker on your own machine. This setup lets them communicate through the same queue system.

## RABBITMQ

![initial_RabbitMQ](image/publisher1.png)

## RABBITMQ AFTER RUN

![initial_RabbitMQ](image/publisher2.png)

When cargo run is executed on the publisher, it sends 5 UserCreatedEventMessage events to the RabbitMQ broker. The subscriber receives and processes them right away, which is shown as a brief spike in the message rate graph on the RabbitMQ dashboard.

## RABBITMQ MONITOR

![initial_RabbitMQ](image/publisher3.png)

When the publisher runs, RabbitMQ shows a quick spike in the "message rates" chart, indicating a burst of messages being sent to the broker. These spikes reappear with each execution, confirming that messages are being actively published and quickly consumed by the subscriber.