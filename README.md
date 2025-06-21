

---

🚀 Hiring Task: Full-Stack Hospital Management System (HMS)

🏥 Project Title: SmartHMS – Modular Hospital Management System

🎯 Objective:

Design and implement a modular hospital management system covering key departments:

Out-Patient Department (OPD)

In-Patient Department (IPD)

Pharmacy

Billing & Payments


The system should demonstrate:

Backend: Clean Spring Boot architecture using SOLID principles and design patterns

Database: Use Oracle for persistence

Messaging: Integrate Apache Kafka for event-driven operations (e.g., billing events, admission notifications)

Frontend: A React-based web UI for users (Admin, Doctor, Nurse, Cashier, Pharmacist)

DevOps: Containerized deployment using Docker + Docker Compose



---

🧩 Functional Expectations:

1. OPD Module

Register and manage out-patient visits

Allow appointment scheduling with time slots

Enable doctors to record consultation notes and generate prescriptions


2. IPD Module

Admit patients into available wards/beds

Allow nurse to record vitals and doctors to add daily notes

Generate discharge summaries with patient progress


3. Pharmacy Module

Maintain inventory with batch and expiry

Dispense medicines based on prescriptions (OPD/IPD)

Track purchase orders and return logs


4. Billing Module

Generate bills for OPD visits, IPD stay, and pharmacy transactions

Support partial payments and refunds

Generate downloadable receipts



---

🏗️ Architectural Requirements:

Implement SOLID principles with layered architecture (Controller, Service, Repository, DTOs, Mappers)

Use appropriate design patterns (e.g., Strategy for billing modes, Factory for patient roles, Observer for Kafka events)

Decouple responsibilities using interfaces, DTOs, mappers, and services

Integrate Kafka to emit/consume events like PatientAdmitted, BillingGenerated, MedicineDispensed

Build React UI with views for Admin, Doctor, Nurse, Pharmacist, and Cashier roles

Use JWT-based authentication with role-based routing on UI

Store data in Oracle, use Liquibase/Flyway for schema versioning

Containerize everything using Docker, including:

Spring Boot services

Oracle XE DB

Kafka + Zookeeper

React frontend

NGINX (optional) for frontend delivery




---

📦 Deliverables:

1. ✅ GitHub Repository with:

Docker Compose setup for full stack

Environment README with run instructions

SQL migration scripts or Liquibase config

Sample data loader



2. ✅ Functional React UI


3. ✅ Kafka listeners with logs (e.g., on patient admission, medicine dispense)


4. ✅ Oracle database running in a container with seeded data


5. ✅ Hosted Demo (e.g., Render, Railway, EC2, or Localhost + ngrok demo video)


6. ✅ Documented architecture: folder structure, design pattern rationale, Docker architecture diagram (PDF or README)




---

👨‍💻 Evaluation Criteria:

Category	Description

Code Quality	SOLID principles, clean code, modular structure
Architecture	Proper service decoupling, reuse, and scalability
React UI	Functional, responsive, role-based routing
Kafka Usage	Real event-driven workflows
Oracle Integration	Clean schema, queries, indexing
DevOps	Fully working local Docker setup
Bonus	Deployment on cloud or public demo link



---


