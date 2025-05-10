# 🏠 Airbnb Clone - Backend Documentation

This repository contains the technical documentation for the **Airbnb Clone Backend** project. It includes the data model, core features, technical and non-functional requirements, and sample data scripts.

---

## 📌 Contents

- [`erd/airbnb_erd.png`](./erd/airbnb_erd.png) – Entity Relationship Diagram (ERD)
- [`features-and-functionalities/airbnb-backend-functionalities.png`](./features-and-functionalities/airbnb-backend-functionalities.png) – Functionalities Flowchart
- [`sql/sample_data.sql`](./sql/sample_data.sql) – SQL script with sample data
- [`normalization.md`](./normalization.md) – Normalization explanation up to 3NF

---

## 📊 Visual Overview

### 🎯 Entity Relationship Diagram (ERD)
![ERD](./erd/airbnb_erd.png)

### 🔧 Backend Functionalities Flowchart
![Functionalities Flowchart](./features-and-functionalities/airbnb-backend-functionalities.png)

---

## 🛠 Proposed Tech Stack

- **Database**: PostgreSQL or MySQL
- **API**: REST (optionally GraphQL)
- **Authentication & Authorization**: JWT, OAuth2, RBAC
- **File Storage**: Local or cloud (e.g., AWS S3)
- **Notifications**: SendGrid, in-app notifications
- **Payments**: Stripe, PayPal
- **Testing**: Pytest, automated API testing

---

## 📂 Project Structure

```bash
.
├── erd/
│   └── airbnb_erd.png
├── features-and-functionalities/
│   └── airbnb-backend-functionalities.png
├── sql/
│   └── sample_data.sql
├── normalization.md
└── README.md
