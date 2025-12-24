# TP : Développement d’une application avec Java et Apache Kafka

Ce projet est une application pratique réalisée dans le cadre du module JEE. L'objectif est de comprendre l'architecture d'Apache Kafka et de mettre en œuvre un système de publication/consommation de messages avec Java.

## 📋 Objectifs

* Comprendre l'architecture d'Apache Kafka (Brokers, Topics, Partitions, Zookeeper/KRaft).
* Installer et configurer un environnement Kafka (via Docker).
* Manipuler Kafka via la ligne de commande (CLI).
* Développer un **Producteur** et un **Consommateur** Kafka en Java.

## 🛠 Prérequis

* **Java JDK 17**
* **Maven**
* **Docker** (pour exécuter le serveur Kafka)
* **IntelliJ IDEA** (ou tout autre IDE Java)

## 🚀 Installation et Démarrage

### 1. Démarrer Kafka (Docker)

Assurez-vous que Docker est lancé, puis exécutez la commande suivante pour démarrer un broker Kafka (version 3.9.0) :

```bash
docker run -d -p 9092:9092 --name kafka apache/kafka:3.9.0
```

### 2. Créer un Topic

Créez le topic nécessaire pour l'application :

```bash
docker exec kafka /opt/kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --create --topic my-first-topic --partitions 1 --replication-factor 1
```

### 3. Cloner et Compiler le projet

```bash
git clone <votre-repo-url>
cd kafkaexample
mvn clean install
```

## 💻 Utilisation

L'application se compose de deux parties principales :

### 1. Le Consommateur (`MyConsumer.java`)

Ce programme écoute le topic `my-first-topic` et affiche les messages reçus en temps réel.

* **Classe** : `ma.formations.kafka.MyConsumer`
* **Action** : Lancez la méthode `main`. Le programme attendra les messages.

### 2. Le Producteur (`MyProducer.java`)

Ce programme envoie un message simple au topic `my-first-topic`.

* **Classe** : `ma.formations.kafka.MyProducer`
* **Action** : Lancez la méthode `main`.
* **Résultat** : Vous verrez "Message envoyé" dans la console du producteur et le message apparaître dans la console du consommateur.

## 📦 Architecture du Projet

```
kafkaexample/
├── pom.xml                   # Dépendances Maven (kafka-clients, log4j)
└── src/
    └── main/
        └── java/
            └── ma/
                └── formations/
                    └── kafka/
                        ├── MyConsumer.java   # Logique de consommation
                        └── MyProducer.java   # Logique de production
```

## 📝 Configuration

* **Serveur Kafka** : `localhost:9092`
* **Topic** : `my-first-topic`
* **Groupe de Consommateurs** : `MyFirstConsumer`
* **Sérialisation** : `StringSerializer` / `StringDeserializer`
