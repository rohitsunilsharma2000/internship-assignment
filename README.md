
---

## 🏥 MODULES AND DETAILED USE CASES

---


## 1️⃣ **OPD (Outpatient Department)** – Walk-in or scheduled patients

### 🔹 Use Case 1: Patient Registration

* **What it does**: Creates a record for a new patient.
* **Example**: A receptionist enters name, age, gender, contact, address, photo, and assigns a unique Patient ID.
* **Purpose**: Helps track visit history, bills, and prescriptions.

### 🔹 Use Case 2: Doctor Appointment Booking

* **What it does**: Lets staff or patients book an appointment with a doctor.
* **Example**: A patient books Dr. Rakesh at 11:00 AM for a skin rash.
* **Optional Feature**: SMS/email reminder 1 day before.
* **💰 Payment:**

    * **✅ Online Booking:** Advance payment required to confirm.

    * **🚶 Walk-in:**  Pay after consultation at billing counter.
  
### 🔹 Use Case 3: Doctor Consultation + Digital Prescription

* **What it does**: The doctor writes notes, diagnosis, and prescribes medicine on a digital interface.
* **Example**: Doctor marks symptoms, adds "Allergic Dermatitis" diagnosis, and prescribes "Cetirizine 10mg".
* **Outcome**: A downloadable and printable prescription PDF is generated.
   * **💰 Payment Booking:** Paid via OPD consultation bill after service.

### 🔹 Use Case 4: OPD Visit History

* **What it does**: Tracks all previous OPD visits.
* **Example**: On the 3rd visit, the doctor compares today's symptoms with the last one using the visit timeline.

---

## 2️⃣ **IPD (Inpatient Department)** – Patients admitted in the hospital

### 🔹 Use Case 1: Admission Workflow

* **What it does**: Admits a patient into the hospital bed/ward.
* **Example**: Mr. Saha is admitted in General Ward, Bed 4 under Dr. Neha.
* **Details Captured**: Attendant info, admission notes, insurance.
* **💰 Payment:**

    * **✅  Booking:** Initial deposit required before admission (e.g., ₹10,000).
      
### 🔹 Use Case 2: Bed Allocation & Transfer

* **What it does**: Assigns, changes, or vacates a bed.
* **Example**: Shifts patient from General to ICU due to deterioration.
* **Feature**: Bed availability dashboard with color-coded statuses (vacant/occupied/cleaning).
* **💰 Payment:**

    * **✅  Fee:**  ✅ Cost is added to consolidated IPD bill, paid at discharge..
      
### 🔹 Use Case 3: Nursing Vitals & Doctor Rounds

* **What it does**: Nurses update vitals like BP, pulse, and doctors record rounds.
* **Example**: Nurse logs BP = 130/85 every 6 hours, doctor logs notes during morning rounds.
* **💰 Payment:**

    * **✅  Fee:**  Rounds included in final IPD bill.
      
### 🔹 Use Case 4: Treatment Plan & Progress

* **What it does**: Shows ongoing treatment plan, investigations, and patient progress.
* **Example**: Shows that blood test is scheduled, medicine is administered, and fever reduced.
* **💰 Payment:**

    * **✅  Fee:**  Charges included in final bill or insurance claim.
      
### 🔹 Use Case 5: Discharge Summary Generation

* **What it does**: Creates a final document summarizing the entire stay.
* **Example**: Shows reason for admission, diagnostics, treatment, medicines, and advice.
* **Export Options**: PDF, print.
* **💰 Payment:**

    * **✅  Fee:**   All dues must be cleared before summary is downloaded/printed.
---

## 3️⃣ **Pharmacy** – Manage medicines & sales

### 🔹 Use Case 1: Inventory Management

* **What it does**: Track stock levels of medicines with batch & expiry.
* **Example**: 50 strips of Paracetamol Batch #101, Expiry: Dec 2025.
* **Alert**: Low stock or expired batch warning.

### 🔹 Use Case 2: Prescription Fulfillment

* **What it does**: Fulfills digital prescriptions from OPD/IPD.
* **Example**: Pharmacy gets a notification for Mr. Roy’s prescription. Dispenses 10 tablets of Amoxicillin.
* **💰 Payment:**

    * **✅  OPD Patient:**   ✅ Must pay before receiving medicines.
    * **✅  IPD Patient:**   ✅ Charges added to consolidated bill.

### 🔹 Use Case 3: Sales with Billing

* **What it does**: Generates retail bill for sold medicines.
* **Example**: Rs. 350 for 3 medicines, includes tax breakdown, pharmacist name.
* **💰 Payment:**

    * **✅  Fee:**  ✅ Payment taken before medicine delivery (cash/card/UPI).
      
### 🔹 Use Case 4: Return & Refund

* **What it does**: Accepts returned medicines and adjusts stock & bill.
* **Example**: Patient returns 2 unused strips within allowed days.
* **💰 Payment:**

    * **✅  Fee:**   Refund processed to same mode (or credit note issued).
      
---

## 4️⃣ **Billing & Payments**

### 🔹 Use Case 1: OPD Billing

* **What it does**: Calculates consultation + procedure + lab charges.
* **Example**: Dr. Consultation ₹500 + ECG ₹300 = ₹800 total.
* **Mode**: Cash/Card/UPI.
* **💰 Payment:**

    * **✅  Fee:**  ✅ Must be paid before leaving OPD desk.
      
### 🔹 Use Case 2: IPD Bill Consolidation

* **What it does**: Aggregates all costs like bed charges, surgeries, lab tests, pharmacy, doctor visits.
* **Example**:

  * Room charges: ₹3000/day x 3 days = ₹9000
  * Medicines: ₹1200
  * Lab: ₹600
  * Total: ₹10,800
* **Feature**: Print bill or export PDF.
* **💰 Payment:**

    * **✅  Fee:**  ✅ Final bill paid before discharge. Partial payments during stay allowed.
      
### 🔹 Use Case 3: Insurance & TPA Handling

* **What it does**: Submit claims to Third Party Admins.
* **Example**: Bill breakdown with diagnosis and treatments is sent to MediAssist.
* **💰 Payment:**

    * **✅  Fee:**  ✅ Covered by insurance; balance paid by patient if any.
      
### 🔹 Use Case 4: Pending Payment Alerts

* **What it does**: Alerts staff if any dues left.
* **Example**: IPD bill partially paid ₹5000, pending ₹3000 shown at discharge time.
* **💰 Payment:**

    * **✅  Fee:**   ✅ Full settlement required before exit/discharge.
---

## 🔄 Cross-Module Use Cases

### ✅ Use Case: Role-Based Access

* **Example**: Only pharmacists can update medicine stock; only billing team can generate final invoices.
* **💰 Payment Impact:** Prevents unauthorized billing/discounts.

### ✅ Use Case: Audit Logs & Reports

* **Example**: Admin can see daily OPD footfall, top 10 prescribed medicines, or outstanding payments.
* **💰 Payment Impact:** Helps reconcile daily earnings & detect fraud.

---
<img src="https://raw.githubusercontent.com/rohitsunilsharma2000/internship-assignment/refs/heads/main/workflow.png"/>

## ✅ BONUS: Smart Features in Modern HMS

| Feature             | What It Does                                        | Example                                              |
| ------------------- | --------------------------------------------------- | ---------------------------------------------------- |
| 🔬 Lab Integration  | Auto-send blood test orders & receive reports       | CBC test ordered from OPD auto-routed to Lab         |
| 📩 Email/SMS Alerts | Appointment reminders, discharge intimation         | Patient gets SMS: “Your report is ready.”            |
| 📷 Document Upload  | Upload ID proof, reports, consent forms             | Upload Aadhaar or previous MRI reports               |
| 📊 Dashboard        | Visual summary of revenue, patients, staff workload | Admin sees: Today: 120 OPD, ₹45k Revenue             |
| 🌐 Patient Portal   | Login to view history, prescriptions                | Patients download their prescription or bill anytime |

---

## 📌 Summary for a  Developer

| Module   | Simple Analogy                                          |
| -------- | ------------------------------------------------------- |
| OPD      | Walk-in clinic visit (register, meet doc, get medicine) |
| IPD      | Like hotel check-in with rooms, nurse care, discharge   |
| Pharmacy | Like a medical shop inside hospital                     |
| Billing  | Like a final checkout counter                           |


---

