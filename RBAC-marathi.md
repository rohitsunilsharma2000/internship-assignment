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


Here is a **complete list** of:

* ✅ **Positive Case Scenarios**: When role-based user creation is allowed
* ❌ **Negative Case Scenarios**: When role-based creation should be denied
* ⚠️ **Edge Case Scenarios**: Unusual but important conditions to handle for robustness

---

### ✅ Positive Case Scenarios (Allowed Role Creations)

| Logged-In User Role | Can Create These Roles                                        | Reason                                                  |
| ------------------- | ------------------------------------------------------------- | ------------------------------------------------------- |
| **SUPER\_ADMIN**    | ADMIN, DOCTOR, NURSE, RECEPTIONIST, BILLING CLERK, PHARMACIST | Has full authority to manage the organization.          |
| **ADMIN**           | DOCTOR, NURSE, RECEPTIONIST, BILLING CLERK, PHARMACIST        | Handles hospital operations, but not strategic control. |
| **HR\_MANAGER**     | NURSE, RECEPTIONIST, BILLING CLERK                            | Focused on staff hiring, not admin or doctors.          |

---

### ❌ Negative Case Scenarios (Denied Role Creations)

| #  | Logged-In User Role | Attempted Creation | ❌ Reason                                | Working Status |
|----|---------------------|--------------------|------------------------------------------|----------------|
| 1  | **ADMIN**           | SUPER_ADMIN        | Cannot assign top-level role.            |  ✅    Working |
| 2  | **ADMIN**           | ADMIN              | Cannot create peers.                     | ❌ Not Working |
| 3  | **HR_MANAGER**      | SUPER_ADMIN        | Not permitted.                           |  ✅    Working |
| 4  | **HR_MANAGER**      | ADMIN              | Beyond HR scope.                         |  ✅    Working |
| 5  | **HR_MANAGER**      | DOCTOR             | Not a staff role.                        |  ✅    Working |
| 6  | **DOCTOR**          | Any role           | Doctors cannot manage users.             | Working but change validation message  |
| 7  | **NURSE**           | Any role           | Nurses have no access to user creation.  | ❌ Not Working |
| 8  | **RECEPTIONIST**    | Any role           | Not permitted.                           | ❌ Not Working |
| 9  | **BILLING CLERK**   | Any role           | No permission.                           | ❌ Not Working |
| 10 | **PHARMACIST**      | Any role           | No permission.                           | ❌ Not Working |


---

### ⚠️ Edge Case Scenarios (Special Handling Required)

| Edge Case                                         | Description                                             | Expected Behavior                                                    |
| ------------------------------------------------- | ------------------------------------------------------- | -------------------------------------------------------------------- |
| 🧪 **Invalid Role in Payload**                    | e.g., `"role": "CEO"` or typo                           | Reject with `400 Bad Request`, return: "Invalid role type."          |
| 🧾 **Missing Role Field in Request**              | Role field is null/missing                              | Reject with validation error: "Role is required."                    |
| 🔑 **JWT Token Tampering**                        | User claims a higher role in token                      | Reject with `403 Forbidden`, must validate against DB/secure source. |
| 🔐 **User Has No Role (Unassigned)**              | Logged-in user has no role                              | Deny creation with message: "User role not assigned."                |
| 🏛️ **HR\_MANAGER Role Not Configured in System** | Role logic missing in backend enum/map                  | Return 500 or fail gracefully with admin alert.                      |
| 📜 **Role Hierarchy Changes Over Time**           | HR\_MANAGER may later be allowed to create Doctors      | System should use config-based role matrix, not hardcoded rules.     |
| 🛑 **Disabled User Account**                      | Logged-in user is deactivated                           | Reject with `401 Unauthorized` or `403 Forbidden`.                   |
| 📅 **Future Role Activation Date**                | User has role assigned but activation date is in future | Deny with message: "Role not yet active."                            |
| 🧪 **Case-Sensitive Role Input**                  | `"doctor"` instead of `"DOCTOR"`                        | Enforce strict case or normalize input.                              |

---


