
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

## 🧪 UI Testing Steps

Follow the steps below to test the **React-based frontend** and verify end-to-end functionality across all modules.

---

### ✅ **1️⃣ OPD (Outpatient Department)**

#### 🔹 Patient Registration

* Go to `/opd/register`
* Fill in details: name, age, gender, contact, address, upload photo
* Submit → Check if a unique Patient ID is generated and displayed

#### 🔹 Doctor Appointment Booking

* Go to `/opd/appointment`
* Select patient, doctor, date, and available time slot
* Choose walk-in or online (if online, trigger payment screen)
* Confirm → View in “Upcoming Appointments”

#### 🔹 Doctor Consultation + Digital Prescription

* Login as doctor → Go to `/opd/consultation`
* Select today’s appointment
* Add symptoms, diagnosis, and prescribe medicines
* Save → Verify PDF prescription is auto-generated and downloadable

#### 🔹 OPD Visit History

* Go to `/opd/history/{patientId}`
* View all past visits, filters by date/doctor
* Select any visit → Check symptoms, diagnosis, prescription from previous consultation

---

### ✅ **2️⃣ IPD (Inpatient Department)**

#### 🔹 Admission Workflow

* Go to `/ipd/admit`
* Select patient → Assign ward, bed, doctor
* Add admission notes, attendant details
* Upload insurance if applicable → Submit → Ensure initial deposit flow is triggered

#### 🔹 Bed Allocation & Transfer

* Go to `/ipd/bed-dashboard`
* View current bed statuses (vacant/occupied/cleaning)
* Click on a patient → Reallocate to different ward/ICU
* Ensure old bed is marked for cleaning

#### 🔹 Nursing Vitals & Doctor Rounds

* Go to `/ipd/vitals/{patientId}`
* Nurse logs BP, temp, pulse at intervals
* Doctor logs round notes via `/ipd/rounds`
* Verify if entries are timestamped and shown in timeline

#### 🔹 Treatment Plan & Progress

* Visit `/ipd/treatment/{patientId}`
* Check active investigations, medication schedules
* Update status → e.g., “Blood test done”, “Fever subsiding”

#### 🔹 Discharge Summary Generation

* Go to `/ipd/discharge`
* Select patient → System shows hospitalization summary
* Click "Generate PDF" → Verify complete info (admission, treatment, final advice)
* Block download until full bill is cleared

---

### ✅ **3️⃣ Pharmacy**

#### 🔹 Inventory Management

* Go to `/pharmacy/inventory`
* Add new medicines with batch, quantity, expiry
* Verify auto-alerts for low stock and near-expiry items

#### 🔹 Prescription Fulfillment

* Go to `/pharmacy/orders`
* New order auto-arrives when doctor prescribes → Click “Dispense”
* Select batch, quantity → Update stock
* Payment required for OPD; IPD items linked to bill

#### 🔹 Sales with Billing

* Go to `/pharmacy/sale`
* Add medicines manually for over-the-counter sales
* Generate bill → See tax split and total → Confirm payment method

#### 🔹 Return & Refund

* Go to `/pharmacy/return`
* Select invoice → Select items to return
* System updates stock and processes refund (original mode/credit note)

---

### ✅ **4️⃣ Billing & Payments**

#### 🔹 OPD Billing

* Go to `/billing/opd/{appointmentId}`
* Shows consultation + lab + procedure costs
* Pay via cash/card/UPI → System marks as “Paid”

#### 🔹 IPD Bill Consolidation

* Go to `/billing/ipd/{patientId}`
* View charges: room, surgery, medicine, labs
* Check bill split: paid, pending → Export PDF
* Mark as paid to unlock discharge summary

#### 🔹 Insurance & TPA Handling

* Go to `/billing/insurance`
* Upload documents → Select TPA (e.g., MediAssist)
* Submit → Track status (pending, approved, partial)

#### 🔹 Pending Payment Alerts

* Go to `/billing/dashboard`
* Check patient list → See unpaid amounts flagged in red
* Test “Remind” or “Settle Now” button functionality

---

### ✅ **🔄 Cross-Module Testing**

#### 🔹 Role-Based Access

* Login as: Admin, Doctor, Nurse, Pharmacist, Billing Staff
* Ensure proper access:

  * Pharmacist cannot update bills
  * Doctor cannot assign beds
  * Billing staff cannot modify prescriptions

#### 🔹 Audit Logs & Reports

* Go to `/admin/reports`
* Generate reports:

  * Daily OPD visits
  * Top 10 prescribed medicines
  * Unpaid bills
* Export in Excel/PDF

---

## 📦 Additional UI Notes

* Every form must have validations (required fields, date pickers, number limits)
* Auto-refresh dashboards every 10 seconds (e.g., beds, vitals)
* Use breadcrumbs, clear headers, and role-based menu items
* Responsiveness: Mobile/tablet-friendly interface



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

## 📊 Evaluation Criteria (with Percentage Weights)

| Evaluation Area                     | Description                                                                                              | Weight (%) |
| ----------------------------------- | -------------------------------------------------------------------------------------------------------- | ---------- |
| ✅ **Backend Design & Architecture** | Follows SOLID principles, clean separation of layers, design patterns used (Strategy, Builder, Observer) | 20%        |
| ✅ **Kafka Integration**             | Kafka used effectively for events (e.g., prescription dispatch, admission alerts, stock updates)         | 10%        |
| ✅ **Database Design (Oracle)**      | Efficient ER modeling, relational constraints, normalized schema, indexing                               | 10%        |
| ✅ **Frontend UI (React)**           | Intuitive, clean, mobile-responsive UI with proper validation and role-based rendering                   | 15%        |
| ✅ **Docker & Environment Setup**    | Working Docker Compose for Oracle, Kafka, Spring Boot, and React; proper `.env` usage                    | 10%        |
| ✅ **Cross-Module Integration**      | End-to-end flow across OPD, IPD, Pharmacy, Billing works as expected                                     | 10%        |
| ✅ **Testing & Documentation**       | Complete README with curl commands, Swagger docs, test instructions                                      | 10%        |
| ✅ **Code Quality & Standards**      | Use of DTOs, exception handling, validations, clear variable/method naming                               | 10%        |
| ✅ **Bonus Features (Optional)**     | PDF exports, audit trail, dashboard charts, patient portal login                                         | 5%         |

---

### 🎯 Pass Criteria:

* **Minimum Passing Score**: 70%
* **Bonus consideration** for:

  * Real-time notifications (websocket or Kafka-driven UI refresh)
  * CI/CD integration or GitHub Actions
  * Testing: Unit + Integration test coverage > 60%

---



## ✅ Bonus Points

* PDF export for prescription/discharge
* Patient portal login (JWT/Session)
* Audit trail of user actions
* Integration with lab/insurance APIs

---

