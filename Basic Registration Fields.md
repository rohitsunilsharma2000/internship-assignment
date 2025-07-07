
---

## 📝 Basic Registration Fields (Applicable to All User Roles)

| **Field Name**       | **Type**    | **Required** | **Description**                                                       |
| -------------------- | ----------- | ------------ | --------------------------------------------------------------------- |
| **Full Name**        | Text        | ✅ Yes        | Full legal name of the user                                           |
| **Email Address**    | Email       | ✅ Yes        | Must be unique; used for login and notifications                      |
| **Mobile Number**    | Phone       | ✅ Yes        | Used for contact and OTP verification                                 |
| **Username**         | Text        | ✅ Yes        | Unique system login ID                                                |
| **Password**         | Password    | ✅ Yes        | Secure password for login                                             |
| **Confirm Password** | Password    | ✅ Yes        | Ensure the user typed the correct password                            |
| **Role**             | Dropdown    | ✅ Yes        | One of: Admin, Doctor, Nurse, Receptionist, Billing Clerk, Pharmacist |
| **Department**       | Dropdown    | Optional     | Useful for Doctors/Nurses (e.g., Cardiology, Pharmacy)                |
| **Joining Date**     | Date        | ✅ Yes        | Official start date for the user in the system                        |
| **Profile Photo**    | File Upload | Optional     | Helps in user identification and printing on reports/cards            |
| **Status**           | Boolean     | ✅ Yes        | Active / Inactive toggle for access control                           |
| **Created By**       | Auto-filled | ✅ Yes        | Tracks who created the user (e.g., Super Admin or Admin)              |

---

### 🔐 Role Example Mapping:

* If `Admin` is creating a `Nurse`:

  * Fields required: name, email, mobile, username, password, role = Nurse, department = ICU, joining date.
* If `SUPER_ADMIN` is creating another `Admin`:

  * All same fields, role = Admin.

---

