खाली एक नवशिक्यांसाठी उपयुक्त, पूर्णतः मराठीत दिलेलं समस्या विधान (Problem Statement) दिलं आहे. हे समस्या विधान Hospital Management System (HMS) साठी UI-आधारित Role-Based Access Control (RBAC) आणि JWT Authentication चा वापर करून Next.js आणि Tailwind CSS मध्ये Dashboard कसं तयार करायचं हे शिकवेल.

---

## 🏥 समस्या विधान: HMS डॅशबोर्डमध्ये Role-Based Access Control आणि JWT वापरून UI व्यवस्थापन (Next.js + Tailwind)

### 🎯 उद्दिष्ट:

Next.js आणि Tailwind CSS वापरून एक असे डॅशबोर्ड तयार करा जिथे प्रत्येक यूजर त्याच्या Role नुसार केवळ संबंधित मॉड्यूल्सच पाहू शकेल. Role माहिती JWT टोकनमधून घेतली जाईल. या प्रोजेक्टमुळे नवशिक्यांना RBAC आणि JWT Authentication हे महत्त्वाचे कॉन्सेप्ट्स समजतील.

---

### 👥 वापरकर्ता भूमिका (Roles):

1. SUPER\_ADMIN
2. ADMIN
3. HR\_MANAGER
4. DOCTOR
5. NURSE
6. RECEPTIONIST
7. BILLING\_CLERK
8. PHARMACIST

---

### 🔐 JWT Authentication (साधी पद्धत):

* एक "Login" पेज तयार करा जिथे Role निवडण्यासाठी dropdown असेल.
* Login नंतर एक dummy/simulated JWT तयार करा:

  ```json
  {
    "username": "adminuser",
    "role": "ADMIN"
  }
  ```
* हे टोकन localStorage मध्ये साठवा.
* Dashboard पेजमध्ये हे token वाचून त्यातून role प्राप्त करा आणि त्यानुसार UI मध्ये मॉड्यूल्स दाखवा.

📦 तुम्ही jwt-decode library वापरू शकता किंवा JSON.parse वापरून token decode करू शकता.

---

### 🧭 Role-to-Module Access Matrix (कोण काय पाहू शकतो):

| वापरकर्ता भूमिका | ✅ पाहू शकणारे मॉड्यूल्स                                        | ❌ पाहू शकत नाही |
| ---------------- | -------------------------------------------------------------- | --------------- |
| SUPER\_ADMIN     | Admin, Doctor, Nurse, Receptionist, Billing, Pharmacy, Profile | नाही            |
| ADMIN            | Doctor, Nurse, Receptionist, Billing, Pharmacy, Profile        | Admin Panel     |
| HR\_MANAGER      | Nurse, Receptionist, Billing Clerk, Profile                    | Admin, Doctor   |
| DOCTOR           | स्वतःचं प्रोफाईल, Patient List                                 | इतर सर्व        |
| NURSE            | स्वतःचं प्रोफाईल, Assigned Patients                            | इतर सर्व        |
| RECEPTIONIST     | स्वतःचं प्रोफाईल, Appointment Dashboard                        | इतर सर्व        |
| BILLING\_CLERK   | स्वतःचं प्रोफाईल, Billing Dashboard                            | इतर सर्व        |
| PHARMACIST       | स्वतःचं प्रोफाईल, Medicine Stock                               | इतर सर्व        |

---

### 🧾 पर्यायी मॉड्यूल्स:

| मॉड्यूल               | कोण पाहू शकतो? |
| --------------------- | -------------- |
| Patient List          | DOCTOR         |
| Assigned Patients     | NURSE          |
| Appointment Dashboard | RECEPTIONIST   |
| Billing Dashboard     | BILLING\_CLERK |
| Medicine Stock        | PHARMACIST     |

---

### 🛠️ UI साठी सुचना (Next.js + Tailwind):

1. Login पेज → Role निवडण्यासाठी dropdown.
2. Login नंतर simulate केलेलं JWT localStorage मध्ये साठवा.
3. Dashboard पेजवर:

   * Token वाचा आणि decode करा.
   * Role ओळखा आणि RBAC Matrix वापरून मॉड्यूल्स Filter करा.
4. प्रत्येक मॉड्यूल Tailwind CSS वापरून एका कार्ड स्वरूपात तयार करा.
5. अनधिकृत पेज/मार्गांवर 403 Access Denied पेज दाखवा.

---

### ✅ उदाहरण वर्तन:

* SUPER\_ADMIN लॉगिन केल्यास → सर्व मॉड्यूल्स दिसतील ✅
* HR\_MANAGER लॉगिन केल्यास → फक्त Nurse, Receptionist आणि Billing Clerk मॉड्यूल्स दिसतील ✅
* PHARMACIST लॉगिन केल्यास → फक्त स्वतःचं प्रोफाईल आणि Medicine Stock दिसेल ✅
* जर DOCTOR ने `/admin-panel` उघडलं → “🔒 Access Denied” दाखवा ❌

---

### 📚 शिका:

* Role-Based UI Visibility कसं करायचं
* JWT टोकन डिकोड करून Role मिळवणं
* Tailwind CSS वापरून कार्ड UI तयार करणं
* RBAC Matrix चा वापर करून सुरक्षिततेची अंमलबजावणी

---
