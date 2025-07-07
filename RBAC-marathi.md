---

## 🛠️ **RBAC Task: Who Can Create Which Type of User?**

### 🎯 Goal:

Ensure that each role can only create specific types of users based on predefined rules.

---

### 🧑‍💼 **Role-to-User Creation Mapping:**

| **Logged-In User Role**                  | **Users They Can Create**                                                | **Reason / Limitation**                                     |
| ---------------------------------------- | ------------------------------------------------------------------------ | ----------------------------------------------------------- |
| **SUPER\_ADMIN**                         | All roles: Admin, Doctor, Nurse, Receptionist, Billing Clerk, Pharmacist | Full control, first and top-level admin of the organization |
| **ADMIN**                                | Doctor, Nurse, Receptionist, Billing Clerk, Pharmacist                   | Responsible for internal hospital management                |
| **HR\_MANAGER** (optional role)          | Nurse, Receptionist, Billing Clerk                                       | Only responsible for creating staff-related roles           |
| **DOCTOR**                               | ❌ Cannot create any users                                                | Doctor can only perform medical tasks                       |
| **NURSE / RECEPTIONIST / BILLING CLERK** | ❌ Cannot create any users                                                | They have limited access                                    |

---

### 🔐 Examples:

* A `SUPER_ADMIN` can create both `Doctor` and `Admin` users.
* An `Admin` can create a new `Receptionist` or `Pharmacist`, but **not** another `Admin` or `Super_Admin`.
* A `Doctor` cannot create any other user.

---

### 📝 Tasks:

1. Create a function/method that validates user creation permissions based on role.
2. Show an "Access Denied" message if permission is not granted.
3. Log each user creation – who created whom and when.

---

**Enforcing these rules will ensure a secure and well-controlled RBAC system.**

---

## 🛠️ **RBAC Task: कोणता युजर कोणता प्रकारचा युजर तयार करू शकतो?**

### 🎯 उद्दिष्ट:

प्रत्येक भूमिका (Role) फक्त ठराविक प्रकारचे युजर्सच तयार करू शकेल – हे नियम सुनिश्चित करणे.

---

### 🧑‍💼 **भूमिका-प्रकार युजर निर्मिती मॅपिंग:**

| **सध्या लॉगिन असलेली भूमिका**            | **कोणते युजर तयार करू शकतो**                                                      | **कारण / मर्यादा**                          |
| ---------------------------------------- | --------------------------------------------------------------------------------- | ------------------------------------------- |
| **SUPER\_ADMIN**                         | सर्व प्रकारचे युजर: Admin, Doctor, Nurse, Receptionist, Billing Clerk, Pharmacist | संस्थेचा प्रमुख, सर्व अधिकार प्राप्त असतो   |
| **ADMIN**                                | Doctor, Nurse, Receptionist, Billing Clerk, Pharmacist                            | हॉस्पिटलची अंतर्गत व्यवस्थापनाची जबाबदारी   |
| **HR\_MANAGER** (पर्यायी)                | Nurse, Receptionist, Billing Clerk                                                | फक्त स्टाफ भरतीसंबंधी भूमिकाच तयार करू शकतो |
| **DOCTOR**                               | ❌ कोणताही युजर तयार करू शकत नाही                                                  | डॉक्टर फक्त वैद्यकीय काम करतात              |
| **NURSE / RECEPTIONIST / BILLING CLERK** | ❌ कोणताही युजर तयार करू शकत नाही                                                  | त्यांच्या भूमिका मर्यादित आहेत              |

---

### 🔐 उदाहरणे:

* `SUPER_ADMIN` नवीन `Doctor` आणि `Admin` दोघांनाही तयार करू शकतो.
* `Admin` नवीन `Receptionist` किंवा `Pharmacist` तयार करू शकतो, पण दुसरा `Admin` किंवा `Super_Admin` नाही.
* `Doctor` कोणताही नवीन युजर तयार करू शकत नाही.

---

### 📝 काम:

1. एक फंक्शन तयार करा जे वापरकर्त्याच्या भूमिकेवर आधारित युजर तयार करण्याची परवानगी तपासेल.
2. परवानगी नसेल तर "Access Denied" संदेश दाखवा.
3. प्रत्येक युजर निर्मिती लॉग करा – कोणी, कोणाला, आणि कधी तयार केलं.

---

**हे नियम योग्य प्रकारे अंमलात आणल्यास, RBAC सिस्टिम सुरक्षित व नियंत्रणात राहील.**

---

