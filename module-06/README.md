# Module 06: Streaming (Kafka / Redpanda + PySpark)

Gửi dữ liệu green taxi 10/2019 vào Kafka rồi xử lý bằng Spark Structured Streaming.

| File | Vai trò |
|---|---|
| `docker-compose.yml` | Redpanda (Kafka API, `localhost:9092`). |
| `settings.py` | Topic, schema, đường dẫn dữ liệu (`resources/green_tripdata_2019-10.csv.gz`). |
| `script.ipynb` | Producer (`kafka-python`) gửi từng dòng vào topic `green-trips`; đọc stream bằng Spark, parse JSON, đếm điểm đến phổ biến theo window 5 phút. |
| `consumer.py` | Consumer PySpark in thử một dòng mỗi micro-batch. |
| `spark-submit.sh` | Submit job lên Spark master kèm các package Kafka/Avro. |
| `spark-sql-kafka-0-10_2.12-3.5.1.jar` | Connector Kafka cho Spark 3.5.1. |

## Chạy
```bash
pip install -r requirements.txt
docker compose up -d
mkdir -p resources   # đặt file green_tripdata_2019-10.csv.gz vào đây (không commit)
# chạy script.ipynb (producer) rồi python consumer.py
```
