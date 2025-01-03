# Real-Time Streaming Data Engineering Pipeline

## Overview
This project implements a modern real-time data engineering pipeline that processes streaming data through a distributed architecture. The system leverages Apache Kafka for stream processing, Apache Spark for data transformation, and Cassandra for data storage, all orchestrated using Apache Airflow and containerized with Docker.

## Architecture
![Architecture Diagram](/data-arq.png)

The pipeline consists of the following components:

### 1. Data Ingestion
- **Python Streaming Client**: Custom implementation to connect to the streaming API
- **Apache Kafka**: Message broker for handling real-time data streams
- **Schema Registry**: Manages and validates data schemas
- **Kafka Control Center**: Monitoring and management interface for Kafka ecosystem

### 2. Orchestration
- **Apache Airflow**: Workflow management and scheduling
- DAGs for coordinating data pipeline components
- Error handling and retry mechanisms
- Monitoring and alerting integration

### 3. Stream Processing
- **Apache Spark**: Distributed processing framework
- Master-Worker architecture for scalable computation
- Real-time data transformation and analysis


### 4. Data Storage
- **Cassandra**: Distributed NoSQL database
- Optimized for write-heavy workloads
- Scalable and highly available storage solution

### 5. Containerization
- **Docker**: Container platform for consistent deployment
- Docker Compose for multi-container orchestration
- Isolated environments for each component

## Setup and Installation

### Prerequisites
- Docker and Docker Compose
- Python 3.9+
- Access to the streaming API

### Running the Pipeline

1. Start all services:
```bash
docker compose up -d
```

2. Access Airflow interface and trigger the DAG (it will connect to the API and stream data for 60 seconds to Kafka Producer)
   http://localhost:8080

3. Run the spark_stream script to process the data and stream it to Cassandra
```bash
python spark_stream.py
```

4. Access Cassandra database to verify the data

