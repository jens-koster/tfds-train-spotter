# tfds-train-spotter
A streaming data lab aiming to provide real-time info on the Øresund trains between Malmö and Copenhagen.

# Plan
Discovery and development of the Øresund train spotter.

Current assumption is that we take data from the TrafikLab API for Øresund trains.
* **TrafikLab->Kafka** - We'll build a custom tfds service for this
* **Kafka->Spark** - For analytics. Using Spark Structured Streaming
* **Kafka->Apache Druid** - Using Druid Kafka Indexing Service
* **Apache Druid->Apache Superset** - Superset has native Druid connectivity

Maybe: **Kafka->Materialise** - Materialize has native support for Kafka

Project: https://github.com/users/jens-koster/projects/3

Data: https://www.trafiklab.se/


**Phase 1:** Show current info

**Phase 2:** Rate the trains, regarding how full they'll be and how likely to be cancelled and such, which can be deduced by looking at delay, time since last train, number of carriages  and the final destination.

**Phase 3:** improve departure predictions. It's not hard since they don't update properly as it is... but a simple ML solution would be a nice touch. We'll need measuring of prediction quality, our own and the provided one.

## 1. Getting the data
There's static (NetEX) data and real-time (siri) at https://www.trafiklab.se/.
We'll need something to get that data and stuff it into kafka.

This'll be work enough for a while...
