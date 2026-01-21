KAFKA VERSION:  kafka_2.13-3.9.0
Display Commit Window: Alt+0

========== Only in kraft Mode =======
======= Use Gitbash ======
LENOVO L13 YOGA@DESKTOP-CH2QFKL MINGW64 /c/kafka

-----Generate a Cluster UUID----
$ KAFKA_CLUSTER_ID="$(bin/kafka-storage.sh random-uuid)"

----Format Log Directories-----------
$ bin/kafka-storage.sh format --standalone -t $KAFKA_CLUSTER_ID -c config/kraft/server.properties
Formatting dynamic metadata voter directory /tmp/kraft-combined-logs with metadata.version 3.9-IV0.

$ echo $KAFKA_CLUSTER_ID
U-bmAPi1RzWScbVG_rKTsQwd

-- Start Kafka Server ---
$ bin/kafka-server-start.sh config/kraft/server.properties

---- Create Topic ----
LENOVO L13 YOGA@DESKTOP-CH2QFKL MINGW64 /c/kafka
$ bin/kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092
Created topic quickstart-events.

--- Describe Topic ---
$ bin/kafka-topics.sh --describe --topic quickstart-events --bootstrap-server localhost:9092

--- Read Message From Topic ---
LENOVO L13 YOGA@DESKTOP-CH2QFKL MINGW64 /c/kafka
$ bin/kafka-console-consumer.sh --topic quickstart-events --from-beginning --bootstrap-server localhost:9092
Salaam
Hello World!