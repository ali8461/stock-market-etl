
# 📈 Real-Time Stock Market Data Pipeline with Kafka and AWS

This project simulates a real-time stock market data stream using Kafka, processes it on an EC2 instance, stores the data on Amazon S3, and analyzes it using AWS Glue and Amazon Athena. The goal is to demonstrate a cost-effective real-time ETL pipeline for financial data analysis without using expensive stock market APIs.
---
### Architecture Diagram

![ETL Architecture](Architecture.jpg)

---
## 🧰 Project Structure

```
stock-market-etl/
├── Data/
│ └── indexProcessed.csv # Processed stock market data CSV (~10MB)
├── snippest/ # Screenshots and query images
│ ├── Athena query.PNG
│ ├── Athena row_count_1.PNG
│ ├── Athena row_count_2.PNG
│ ├── Athena row_count_3.PNG
│ ├── Athena row_count_4.PNG
│ ├── DB.PNG
│ ├── Glue crawler.PNG
│ └── S3.PNG
├── Architecture.jpg # System architecture diagram
├── KafkaConsumer.ipynb # Kafka consumer notebook for data ingestion
├── KafkaProducer.ipynb # Kafka producer notebook for data publishing
├── command_kafka.txt # Kafka command line instructions
├── README.md # Project documentation

```


## 🚀 Project Flow

1. **Simulate Stock Market Data**
   - `indexProcessed.csv` is used as the data source.
   - A Python script using `pandas` and `kafka-python` simulates real-time streaming.

2. **Kafka Setup on EC2**
   - Apache Kafka is installed and configured on an EC2 instance.
   - A topic `demo_topic_2` is created to stream stock market data.

3. **Consumer Writes to S3**
   - A Kafka consumer reads messages and writes them to Amazon S3.

4. **Data Cataloging and Analysis**
   - AWS Glue Crawler scans the S3 bucket to build the Data Catalog.
   - Amazon Athena is used to query and analyze the streaming data using SQL.


## Summary
Python (Producer) → Kafka → S3 (Consumer) → Glue Crawler → Glue Data Catalog → Athena Query


## 📦 Requirements

- Python 3.x
- Kafka & Zookeeper (installed on EC2)
- Jupyter Notebooks
- AWS CLI configured
- Python packages:
  - `kafka-python`
  - `boto3`
  - `pandas`
  - `s3fs`

## 💡 Use Case

This project is ideal for:
- Learning and demonstrating real-time data pipelines
- Testing Kafka integration with AWS services
- Practicing data lake architecture with simulated financial data

## 🧪 Sample Athena Query

```sql
SELECT * 
FROM "kafka_stock_database"."stock_market_data"
LIMIT 10;

```



![Sample](snippest/"Athena query".jpg)

