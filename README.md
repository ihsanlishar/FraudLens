# FraudLens 🔍
A real-time fraud detection system that uses streaming data and stream processing to detect suspicious financial transactions instantly.

## What It Does
FraudLens monitors live financial transactions and automatically flags suspicious ones in real time. It combines Apache Kafka for streaming with Flink SQL for instant fraud detection logic running continuously in the cloud.

## Architecture
```
Python Producer → Kafka (transactions) → Flink SQL → Kafka (flagged_transactions)
```

## Tech Stack
- **Confluent Cloud** — Managed Kafka cluster for real-time streaming
- **Apache Kafka** — Transaction data pipeline
- **Schema Registry** — Data governance and format validation
- **Flink SQL** — Real-time stream processing and fraud detection
- **Python** — Transaction data producer

## How to Run

### Prerequisites
- Python 3.x
- Confluent Cloud account

### Setup
1. Clone the repo
2. Create a virtual environment:
```
   python3 -m venv venv
   source venv/bin/activate
```
3. Install dependencies:
```
   pip install confluent-kafka python-dotenv
```
4. Create a `.env` file with your credentials:
```
   KAFKA_BOOTSTRAP_SERVER=your_bootstrap_server
   KAFKA_API_KEY=your_kafka_api_key
   KAFKA_API_SECRET=your_kafka_api_secret
   SCHEMA_REGISTRY_URL=your_schema_registry_url
   SCHEMA_REGISTRY_API_KEY=your_sr_api_key
   SCHEMA_REGISTRY_API_SECRET=your_sr_api_secret
```
5. Run the producer:
```
   python producer.py
```

## Fraud Detection Logic
- Transactions above **$1,000** are flagged as suspicious
- Flagged transactions are written to a separate Kafka topic in real time
- Flink SQL processes the stream continuously with zero latency

## What's Working
- ✅ Live transaction data streaming into Kafka every 2 seconds
- ✅ Schema Registry enforcing data contracts
- ✅ Flink SQL fraud detection running continuously
- ✅ Flagged transactions flowing into dedicated topic in real time

## Future Improvements
- AI-generated explanations for each flagged transaction
- Frontend dashboard for visual monitoring
- Machine learning anomaly detection
- Automated responses to fraud alerts
- Integration with real banking systems
