# Evaluation - Java Hibernate Projects

This repository contains three Java exercises using Hibernate ORM for different domains: stock management, project management, and civil status management.

## 📋 Overview

- **Exercice 1**: Gestion de Stock (Stock Management)
- **Exercice 2**: Gestion de Projets (Project Management)
- **Exercice 3**: Gestion de l'État Civil (Civil Status Management)

## 🛠️ Technology Stack

- **Java**: 11 (Exercice 1 & 2), 8 (Exercice 3)
- **Hibernate**: 5.6.9.Final (Exercice 1), 5.6.15.Final (Exercice 2 & 3)
- **Database**: MySQL 8.0
- **Build Tool**: Maven
- **IDE Support**: IntelliJ IDEA

## 📦 Prerequisites

1. **Java JDK**: 11 or 8 (depending on exercise)
2. **Maven**: 3.6+
3. **MySQL**: 8.0+
4. **Git**: For cloning the repository

## 🗄️ Database Configuration

All exercises use the same MySQL credentials:
- **Username**: `root`
- **Password**: `123456789`
- **Port**: `3306`

### Exercise-Specific Databases

- **Exercice 1**: `gestion_stock`
- **Exercice 2**: `projet_db`
- **Exercice 3**: `etatcivil`

## 📁 Exercise Details

---

## 🏪 Exercice 1: Gestion de Stock

**Purpose**: Develop an application to manage stock for a computer products store.

### Domain Model

- **Categorie**: Product categories (Ordinateurs, Imprimantes, Périphériques)
- **Produit**: Products with reference, designation, price, quantity
- **Commande**: Customer orders with date
- **LigneCommande**: Order lines linking products to orders with quantities

### Relationships

```
Categorie (1) ──< Produit (N)
Produit (1) ──< LigneCommande (N)
Commande (1) ──< LigneCommande (N)
```

### Key Features

- ✅ CRUD operations for all entities
- ✅ List products by category
- ✅ Query products by price (Named Query)
- ✅ Query products ordered between dates
- ✅ Display order details with products and quantities

### Files Structure

```
exercice1/
├── pom.xml
├── src/
│   ├── main/
│   │   ├── java/ma/projet/
│   │   │   ├── classes/          # Entity classes
│   │   │   ├── dao/              # DAO interface
│   │   │   ├── service/          # Service classes
│   │   │   ├── test/             # Test class
│   │   │   └── util/             # HibernateUtil
│   │   └── resources/
│   │       └── application.properties
```

### How to Run

```bash
cd exercice1
mvn clean compile
mvn exec:java
```

**Test Class**: `TestGestionStock.java`

<img width="1440" height="865" alt="exercice 1" src="https://github.com/user-attachments/assets/d23f675b-4f1a-4793-afd7-2e31614417cb" />

---

## 🏗️ Exercice 2: Gestion de Projets

**Purpose**: A consulting firm wants to track time spent on projects and calculate overall costs.

### Domain Model

- **Employe**: Employees with matricule, nom, prenom, email, tel, adresse, dateNaissance
- **Projet**: Projects with name, start/end dates, price, and a manager (chef)
- **Tache**: Tasks with planned and actual dates, price
- **EmployeTache**: Junction table tracking hours worked by employees on tasks

### Relationships

```
Employe (1) ──< Projet (N) [as chef]
Projet (1) ──< Tache (N)
Employe (1) ──< EmployeTache (N)
Tache (1) ──< EmployeTache (N)
```

### Key Features

- ✅ CRUD operations for all entities
- ✅ Get tasks assigned to an employee
- ✅ Get projects managed by an employee
- ✅ Display tasks completed for a project
- ✅ Filter tasks by price (Named Query > 1000 DH)
- ✅ Query tasks by date range

### Files Structure

```
exercice2/
├── pom.xml
├── src/
│   ├── main/
│   │   ├── java/ma/projet/
│   │   │   ├── classes/          # Entity classes
│   │   │   ├── dao/              # DAO interface
│   │   │   ├── service/           # Service classes
│   │   │   └── util/              # HibernateUtil
│   │   └── resources/
│   │       └── hibernate.cfg.xml
│   └── test/
│       └── java/
│           └── TestApplication.java
```

### How to Run

```bash
cd exercice2
mvn clean compile
mvn exec:java
```

**Test Class**: `TestApplication.java`

<img width="1440" height="860" alt="exercice2" src="https://github.com/user-attachments/assets/34dacfb6-7e0b-456a-9723-e2676ba89ed6" />

---

## 👥 Exercice 3: Gestion de l'État Civil

**Purpose**: Create an application to manage citizens and their matrimonial relationships in a province.

### Domain Model

- **Homme**: Men with nom, prenom, dateNaissance
- **Femme**: Women with nom, prenom, dateNaissance
- **Mariage**: Marriages with start/end dates, number of children, references to homme and femme

### Relationships

```
Homme (1) ──< Mariage (N)
Femme (1) ──< Mariage (N)
```

### Key Features

- ✅ CRUD operations using Generic DAO pattern
- ✅ Find oldest woman
- ✅ Count children of a woman between dates
- ✅ Find women married at least twice (Named Query)
- ✅ Count men married to 4 women between dates
- ✅ Display all marriages of a man with details (ongoing vs failed marriages)

### Files Structure

```
exercice3/
├── pom.xml
├── src/
│   └── main/
│       ├── java/ma/projet/
│       │   ├── beans/             # Entity classes
│       │   ├── dao/               # GenericDao + IDao
│       │   ├── services/          # Service classes
│       │   ├── main/              # Test program
│       │   └── util/              # JPA HibernateUtil
│       └── resources/
│           └── META-INF/
│               └── persistence.xml
```

### How to Run

```bash
cd exercice3
mvn clean compile
mvn exec:java -Dexec.mainClass="ma.projet.main.TestProgram"
```

**Test Class**: `TestProgram.java`

<img width="1439" height="862" alt="exercice3" src="https://github.com/user-attachments/assets/7a33bc87-b9e9-44d9-b816-8706f1630a90" />

---

## 🚀 Quick Start Guide

### 1. Clone the Repository

```bash
git clone https://github.com/Satsujii/Evaluation.git
cd Evaluation
```

### 2. Setup MySQL

Make sure MySQL is running on localhost:3306 with credentials:
- Username: `root`
- Password: `123456789`

The databases will be created automatically by Hibernate.

### 3. Navigate to an Exercise

```bash
cd exercice1  # or exercice2, exercice3
```

### 4. Build and Run

```bash
mvn clean compile exec:java
```

---

## 📝 Configuration Files

### Exercice 1
- **Hibernate**: Programmatic configuration in `HibernateUtil.java`
- **Database**: `gestion_stock`
- **Driver**: MySQL Connector 8.0.33

### Exercice 2
- **Hibernate**: XML configuration (`hibernate.cfg.xml`)
- **Database**: `projet_db`
- **Connection Pool**: C3P0

### Exercice 3
- **JPA**: `persistence.xml`
- **Database**: `etatcivil`
- **Provider**: Hibernate JPA

---

## 🔑 Key Concepts Demonstrated

### Exercice 1
- Basic Hibernate annotations (@Entity, @Table, @Column)
- Relationships (@OneToMany, @ManyToOne)
- Named Queries
- HQL (Hibernate Query Language)
- Programmatic SessionFactory configuration

### Exercice 2
- Hibernate XML configuration
- Complex relationships with self-referencing associations
- Named Queries at entity level
- Query parameters and date handling
- Service layer architecture

### Exercice 3
- JPA with Hibernate
- Generic DAO pattern (DRY principle)
- JPQL (Java Persistence Query Language)
- Native SQL queries
- More complex business logic queries

---

## 📚 Entity Relationship Diagrams

### Exercice 1
```
┌─────────────┐       ┌─────────┐       ┌──────────────┐
│ Categorie  │───────│ Produit │───────│ LigneCommande│
└─────────────┘  1:N └─────────┘  1:N  └──────────────┘
                              └─────────┐
                                         │ 1:N
                                   ┌─────┴─────────┐
                                   │   Commande    │
                                   └───────────────┘
```

### Exercice 2
```
┌──────────┐       ┌──────────┐       ┌─────────────────┐
│ Employe  │───────│  Projet  │───────│      Tache      │
└────┬─────┘ 1:N   └──────────┘ 1:N   └────────┬────────┘
     │                                          │
     │                        ┌────────────────┴────────────────┐
     └────────────────────────┤       EmployeTache              │
                               └────────────────────────────────┘
```

### Exercice 3
```
┌──────────┐       ┌──────────────┐       ┌────────┐
│  Homme   │───────│   Mariage    │───────│ Femme  │
└──────────┘ 1:N   └──────────────┘ N:1   └────────┘
```

---

## 🧪 Testing

Each exercise includes comprehensive test classes that demonstrate:
- Entity creation and persistence
- Querying with various criteria
- Complex relationship navigation
- Data retrieval and formatting

### Running Tests

```bash
# Exercice 1
cd exercice1
mvn test

# Exercice 2
cd exercice2
mvn test

# Exercice 3
cd exercice3
mvn test
```

---

## 📦 Maven Dependencies

All exercises share common dependencies:
- **Hibernate Core**: ORM framework
- **MySQL Connector**: JDBC driver
- **JPA API**: Persistence annotations
- **SLF4J**: Logging framework

---

## 🎯 Learning Objectives

This repository demonstrates:

1. **Object-Relational Mapping** (ORM) using Hibernate
2. **JPA** (Java Persistence API) specifications
3. **Database Design** with proper relationships
4. **DAO Pattern** and **Service Layer** architecture
5. **Query Languages**: HQL, JPQL, Native SQL
6. **Named Queries** and **Criteria API**
7. **Transaction Management**
8. **Configuration**: Programmatic vs XML vs JPA

---

## 📄 License

This project is for educational purposes.

---

## 👤 Author

**Satsujii**

GitHub: [@Satsujii](https://github.com/Satsujii)

---

## 🤝 Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.

---

## 📧 Support

If you have any questions or issues, please feel free to open an issue on GitHub.

---

**Happy Coding! 🚀**

