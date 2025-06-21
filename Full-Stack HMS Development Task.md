
---

# 📝 Full-Stack HMS Development Task

## 🎯 **Objective**

Build a deployable, modular, real-world **Hospital Management System (HMS)** using:

* Backend: **Java 17, Spring Boot**, Oracle DB, **Kafka**, SOLID principles, design patterns
* Frontend: **React.js**
* Infrastructure: **Docker** (multi-container setup)
* Documentation: Detailed README with test and deployment steps

---

## 📦 Modules to Implement

### 1️⃣ **OPD (Outpatient Department)**

* Patient Registration
* Doctor Appointment Booking
* Doctor Consultation with Digital Prescription
* OPD Visit History View

### 2️⃣ **IPD (Inpatient Department)**

* Patient Admission with Initial Deposit
* Bed Allocation, Transfer, Vacating
* Nurse Vitals + Doctor Rounds Logging
* Treatment Plan & Progress Tracking
* Discharge Summary Generation

### 3️⃣ **Pharmacy**

* Medicine Inventory Management
* Prescription Fulfillment
* Medicine Sales Billing
* Return & Refund Workflow

### 4️⃣ **Billing & Payments**

* OPD Bill Calculation
* IPD Bill Consolidation
* Insurance/TPA Handling
* Pending Payment Alerts

---

## 📐 Architecture Guidelines

* Follow **SOLID** principles and layered architecture (Controller → Service → Repository)
* Use design patterns like:

  * Strategy (role-based access)
  * Builder (prescription PDF generation)
  * Observer (Kafka event handling for notifications)
* Use DTOs, Validation, Exception Handling (`@ControllerAdvice`)
* Kafka should handle:

  * Prescription dispatch to Pharmacy
  * Lab order notifications
  * Admission/discharge events

---

## 🧱 Tech Stack

| Layer      | Tech                            |
| ---------- | ------------------------------- |
| Backend    | Java 17, Spring Boot            |
| DB         | Oracle                          |
| Messaging  | Apache Kafka                    |
| Frontend   | React.js                        |
| Container  | Docker, Docker Compose          |
| PDF/Report | OpenPDF or iText                |
| API Docs   | Swagger/OpenAPI                 |
| Monitoring | Spring Boot Actuator (optional) |

---

## 🚢 Deployment Setup

* Use **Docker Compose** to run:

  * Oracle DB
  * Kafka + Zookeeper
  * Spring Boot App
  * React Frontend
* Use `.env` files for environment variables
* Add a **Makefile or shell script** for one-step setup

---

## 🔍 Example CURL/API Test Commands (include in README)

```bash
# Register a new patient
curl -X POST http://localhost:8080/api/patients \
  -H "Content-Type: application/json" \
  -d '{"name": "Anjali Roy", "age": 34, "gender": "Female", "contact": "9876543210"}'

# Book OPD Appointment
curl -X POST http://localhost:8080/api/appointments \
  -H "Content-Type: application/json" \
  -d '{"patientId": 1, "doctorId": 2, "slot": "2025-06-25T11:00"}'

# Generate Prescription
curl -X POST http://localhost:8080/api/prescriptions \
  -H "Content-Type: application/json" \
  -d '{"appointmentId": 10, "diagnosis": "Allergic Dermatitis", "medicines": ["Cetirizine 10mg"]}'
```

---

## 🌐 UI Testing Steps (include in README)

1. Start React frontend using Docker.
2. Navigate to: `http://localhost:3000`
3. Use UI to:

   * Register new patient
   * Book appointment (dropdown of doctors & slots)
   * Doctor login & write digital prescription
   * View past visits
   * Admit patient & assign bed
   * Process pharmacy orders
   * View/print discharge summary
4. Validate generated PDFs, alerts, and dashboards.

---

## 🚀 Deployment Instructions (README.md)

1. Clone repo
2. Set up `.env` file (Oracle DB, Kafka topics, etc.)
3. Run:

```bash
docker-compose up --build
```

4. Access:

   * Backend: `http://localhost:8080/swagger-ui.html`
   * Frontend: `http://localhost:3000`
   * Kafka UI (if added): `http://localhost:8081`

---

## 📊 Evaluation Criteria

| Area                    | Criteria                                                  |
| ----------------------- | --------------------------------------------------------- |
| Backend Design          | SOLID compliance, layered structure, clean code           |
| Kafka Usage             | Event-driven interaction between modules (e.g., Pharmacy) |
| DB Design               | Relational mapping, constraints, query optimization       |
| Dockerization           | Clean Dockerfile, Compose with working services           |
| React UI                | User-friendly, role-based access, dynamic forms           |
| Code Quality            | Exception handling, logging, validation                   |
| Testing & Documentation | CURL commands, Swagger, Readme with steps                 |
| Completeness            | At least 80% of use cases implemented                     |

---

## 🧠 Sample Interview Questions

### ☑️ Backend

1. **Explain how you followed the SOLID principles in your implementation.**
2. **How is Kafka used in your project? Explain topics and event flow.**
3. **What design pattern did you use for handling billing logic?**

### ☑️ Frontend

1. **How did you manage state in React (e.g., Redux or Context API)?**
2. **How do you validate patient form data before submission?**

### ☑️ DevOps

1. **Explain how you containerized Oracle DB and Spring Boot.**
2. **How can we scale this system if OPD gets 10,000 requests per day?**

---

## ✅ Bonus Points

* PDF export for prescription/discharge
* Patient portal login (JWT/Session)
* Audit trail of user actions
* Integration with lab/insurance APIs

---

