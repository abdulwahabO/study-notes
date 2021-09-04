## Overview

Apache Kafka is a distributed streaming platform for the storage and processing of streams of events. An event can be thought of as a independent piece of information. E.g., a user click on a website, A transaction on Amazon etc. Kafka is primarily used for building data pipelines and streaming solutions.
Kafka uses cases include:

- Messaging between different components.
- Metrics and logging.
- Stream processing.

Kafka is built aroun the concept of a _commit log_(also known as write-ahead log). A commit log is a sequence of records where each record has a unique identifier. It is immutable and records can only be added at the end. Commit logs are used extensively in software development. They serve as a reliable record of what has happened in a system and in what order. Databases and caches use commit logs to reconstruct the state of the system after a crash.

### Components of Kafka

- A **message** is the unit of data in Kafka. Messages are batched together to increase throughput. Latency increases as the number of messages in a batch increases. Batching can be configured. Message batches are compressed for efficiency. Kafka doesn't demand any schema for message. Infact to the Kafka broker messages are just arrays of bytes. It is recommend however to use a message format with structure that allows for easy understanding. Common formats are JSON, XML and Avro.

- A **topic** is where messages get written to and read from. Topics have subdivisions known as **partitions**. Messages are ordered by time within a partition and not across the entire topic. Partitions allow for horitonzal scaling as each partition can be hosted on a different server. 

- A **message** key can be used to control which partition a message is written to. Message keys are optional but all messages with the same key will land in the same partition.

- A single Kafka server is called a **broker**. Several brokers form a **cluster**. A broker known as the **controller** is elected from the live members of the cluster and is responsible for admin tasks like assigning partitions and monitoring cluster members for failure.

- A partition can be replicated across several brokers. This creates redundancy and ensures that partitions are available for read/write even if one the brokers goes downs. 

- A **producer** creates a message and writes it to Kafka broker. Producers can specify a message key or use a custom partitioner to determine which partition the message goes to.

- **Consumers** poll messages. They operate as part of a **consumer group(can consist of a single consumer)**. Members of a consumer group work together to read a topic. Although a consumer can read from several partition, each partition can only be accessed by one member of a consumer group. E.g., for a topic with 4 partitions and a consumer group with two members, every member will be assigned two partitions. 
One of the consumers in a group acts as **group coordinator**. 

- The group coordinator monitors heartbeats from other group members and triggers a **partition rebalance** when a member goes offline. Consumer groups are independent of each other. **Consumers** commit the **offsets** of the partitions they are reading so that if they went offline and another consumer can take over the partition and continue from where they stopped. Offset commit can be automatic or manual depending on configuration. 

- A partition rebalance is the process of changing ownership of a topic's partition. This happens when a consumer goes offline or new partition is added to the topic. Consumers can listen for rebalances and execute some logic before or after. 

**_TODO: Learn more about how each of these concepts work._**
