Certainly! Here's your complete English version of the HMS (Hospital Management System) prompt with role-based user creation logic, positive/negative/edge case scenarios, and module-level access rights clearly defined.

---

## 🏥 HMS Role-Based User Management & Module Access — English Prompt

### 📌 Step-by-Step Workflow:

1. ✅ When a hospital purchases the HMS system, the first SUPER\_ADMIN registers themselves. A maximum of 2 SUPER\_ADMINs are allowed.
2. 🔐 The SUPER\_ADMIN logs in to the admin panel.
3. 🧑‍⚕️ The SUPER\_ADMIN can create the following user roles:

   * ADMIN
   * DOCTOR
   * NURSE
   * RECEPTIONIST
   * BILLING CLERK
   * PHARMACIST
4. 🔐 The ADMIN logs in to manage internal hospital operations.
5. 🕐 Either SUPER\_ADMIN or ADMIN sets up doctor availability and time slots.

---

### ✅ Positive Case Scenarios (Allowed Role Creation)

| Logged-In Role         | Can Create Roles                                              | Reason                                                  |
| ---------------------- | ------------------------------------------------------------- | ------------------------------------------------------- |
| SUPER\_ADMIN           | ADMIN, DOCTOR, NURSE, RECEPTIONIST, BILLING CLERK, PHARMACIST | Has full authority and top-level administrative rights. |
| ADMIN                  | DOCTOR, NURSE, RECEPTIONIST, BILLING CLERK, PHARMACIST        | Manages hospital operations, not strategy.              |
| HR\_MANAGER (Optional) | NURSE, RECEPTIONIST, BILLING CLERK                            | HR-focused for staff hiring only.                       |

---

### ❌ Negative Case Scenarios (Denied Role Creation)

| Logged-In Role | Attempted Creation            | ❌ Reason                                    |
| -------------- | ----------------------------- | ------------------------------------------- |
| ADMIN          | SUPER\_ADMIN                  | Cannot create top-level role.               |
| ADMIN          | ADMIN                         | Not allowed to create peer-level roles.     |
| HR\_MANAGER    | SUPER\_ADMIN / ADMIN / DOCTOR | Outside of HR scope.                        |
| DOCTOR         | Any role                      | Doctors cannot create users.                |
| NURSE          | Any role                      | Nurses are restricted from user management. |
| RECEPTIONIST   | Any role                      | Not permitted.                              |
| BILLING CLERK  | Any role                      | No user management access.                  |
| PHARMACIST     | Any role                      | No permission.                              |

---

### ⚠️ Edge Case Scenarios (Special Handling Required)

| Edge Case                            | Description                                                 | Expected Behavior                                               |
| ------------------------------------ | ----------------------------------------------------------- | --------------------------------------------------------------- |
| 🧪 Invalid Role Input                | e.g., "CEO" or typo in role name                            | Reject with 400 Bad Request and message: "Invalid role type."   |
| 🧾 Missing Role Field                | Role is missing or null in request payload                  | Reject with validation error: "Role is required."               |
| 🔑 JWT Role Tampering                | User manipulates JWT to impersonate higher role             | Reject with 403 Forbidden after DB/secure role validation.      |
| 🔐 No Role Assigned to User          | User is logged in but has no role                           | Deny creation with: "User role not assigned."                   |
| 🏛️ HR\_MANAGER Role Not Implemented | Role not present in backend enum/config                     | Return 500 error or fail gracefully with alert to system admin. |
| 📜 Role Hierarchy Evolves            | e.g., HR\_MANAGER may be allowed to create DOCTOR in future | Prefer config-based dynamic role mapping (not hardcoded).       |
| 🛑 User Account Disabled             | User is inactive or deactivated                             | Reject with 401 Unauthorized or 403 Forbidden.                  |
| 📅 Future Role Activation Date       | Role assigned but not yet active                            | Deny creation with message: "Role not yet active."              |
| 🧪 Case-Sensitive Role Name          | e.g., "doctor" instead of "DOCTOR"                          | Enforce strict case or normalize input to upper-case roles.     |

---

### 🧭 Role-Based Module Access Matrix

| User Role    | Can Access Modules                                            |
| ------------ | ------------------------------------------------------------- |
| SUPER\_ADMIN | ADMIN, DOCTOR, NURSE, RECEPTIONIST, BILLING CLERK, PHARMACIST |
| ADMIN        | DOCTOR, NURSE, RECEPTIONIST, BILLING CLERK, PHARMACIST        |
| HR\_MANAGER  | NURSE, RECEPTIONIST, BILLING CLERK                            |

✅ Ensure each module endpoint is protected via Role-Based Access Control (RBAC) before allowing access.

---

Would you like help implementing this in:

* ✅ Java Enum + RBAC validator
* ✅ Configurable YAML or Database-driven access matrix
* ✅ Swagger/OpenAPI documentation with constraints
* ✅ Frontend visibility restrictions (based on role)

Let me know and I’ll assist with full implementation!
