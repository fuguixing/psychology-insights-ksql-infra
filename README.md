<p align="center">
  <a href="https://www.terraform.io/"><img src="https://img.shields.io/badge/Terraform-Infrastructure%20as%20Code-blue.svg" alt="Terraform"></a>
  <a href="https://kafka.apache.org/"><img src="https://img.shields.io/badge/Kafka-Distributed%20Streaming%20Platform-orange.svg" alt="Kafka"></a>
  <a href="https://ksqldb.io/"><img src="https://img.shields.io/badge/KSQL-Streaming%20SQL%20Engine-blue.svg" alt="KSQL"></a>
  <a href="https://debezium.io/"><img src="https://img.shields.io/badge/Debezium-Change%20Data%20Capture-brightgreen.svg" alt="Debezium"></a>
  <a href="https://www.elastic.co/"><img src="https://img.shields.io/badge/Elasticsearch-Distributed%20Search%20%26%20Analytics-yellow.svg" alt="Elasticsearch"></a>
  <a href="https://www.mysql.com/"><img src="https://img.shields.io/badge/MySQL-Relational%20Database-blue.svg" alt="MySQL"></a>
</p>

# Psychology Insights KSQL Infra

This repository contains the code and resources for the infrastructure of the rate app in the Psychology Insights project.

## Getting Started

To set up the KSQL infrastructure, follow these steps:

### Prerequisites

Azure subscription: If you don't have an Azure subscription, create a free account before you begin.
Install and configure Terraform

### Use Terraform to create a Linux VM

1. Clone this repository :
```bash
git clone https://github.com/fuguixing/psychology-insights-ksql-infra.git
```
2. Initialize Terraform:
```bash
terraform init -upgrade
```
3. Create and apply a Terraform execution plan:
```bash
terraform plan -out main.tfplan
terraform apply main.tfplan
```
4. SSH to VM:
```bash
terraform output -raw tls_private_key > id_rsa
terraform output public_ip_address
chmod 600 id_rsa 
ssh -i id_rsa azureuser@<public_ip_address>
```
5. Run the containers:
```bash
docker-compose up -d
```
6. Clean up resources:
```bash
terraform plan -destroy -out main.destroy.tfplan
terraform apply main.destroy.tfplan
```

### Web UI

- **Kafka Topics UI**

  `Kafka Topics UI` can be accessed at http://localhost:8085

- **Kafka Connect UI**

  `Kafka Connect UI` can be accessed at http://localhost:8086

- **Schema Registry UI**

  `Schema Registry UI` can be accessed at http://localhost:8001

- **Kafka Manager**

  `Kafka Manager` can be accessed at http://localhost:9000

- **Elasticsearch**

  `Elasticsearch` can be accessed at http://localhost:9200

## Acknowledgements

1. The app is modified from [springboot-kafka-connect-debezium-ksqldb](https://github.com/ivangfr/springboot-kafka-connect-debezium-ksqldb) Many thanks to the original author!
2. Special thanks to Confluent Kafka, KSQL, and Azure!

## Contributing

Welcome contributions to improve the machine learning training process in the Snowflake Training Repository. If you'd like to contribute, please follow these guidelines:

- Fork the repository and create a new branch for your feature or improvement.
- Commit your changes and push your branch to your forked repository.
- Submit a pull request, describing your changes in detail.

## License

This project is licensed under the [MIT License](LICENSE).