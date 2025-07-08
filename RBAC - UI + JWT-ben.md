নিচে একটি 🔐 সম্পূর্ণ ও কনসোলিডেটেড Problem Statement তৈরি করা হয়েছে বাংলা ভাষায়, যা শিক্ষানবিসদের জন্য উপযোগী। এতে UI-based Role-Based Access Control (RBAC), JWT authentication simulation, এবং প্রতিটি রোলের জন্য কী কী মডিউল দেখা যাবে তার বিস্তারিতসহ রয়েছে। এটি আপনি Next.js + Tailwind CSS ব্যবহার করে হাতে-কলমে বাস্তবায়ন করতে পারবেন।

---

## 🧪 সমস্যা বিবৃতি: Hospital Management System (HMS) UI – Role-Based Access Control + JWT

### 🎯 লক্ষ্য:

Next.js এবং Tailwind CSS ব্যবহার করে একটি Dashboard তৈরি করুন, যেখানে ইউজার লগইন করার পর JWT টোকেন অনুযায়ী তার Role পাওয়া যাবে এবং সেই Role অনুযায়ী শুধুমাত্র নির্ধারিত মডিউল UI-তে দেখা যাবে। এটি শিক্ষানবিসদের জন্য RBAC ও JWT ধারণা শেখার অনুশীলন হবে।

---

### 🧑‍⚕️ সিমুলেটেড ইউজার রোলসমূহ:

1. SUPER\_ADMIN
2. ADMIN
3. HR\_MANAGER
4. DOCTOR
5. NURSE
6. RECEPTIONIST
7. BILLING\_CLERK
8. PHARMACIST

---

### 🔐 JWT Authentication (সিমুলেটেড):

* একটি mock login form তৈরি করুন (username/password না চাইলে role selector)
* লগইনের পরে frontend নিজেই একটি সিমুলেটেড JWT তৈরি করবে:

  ```json
  {
    "username": "adminuser",
    "role": "ADMIN"
  }
  ```
* এই JWT localStorage বা cookie-তে সংরক্ষণ করুন।
* Dashboard পেজে token ডিকোড করে role বের করুন।
* তারপর সেই role অনুযায়ী মডিউল access কনফিগার করুন।

📦 Optional: আপনি jwt-decode লাইব্রেরি ব্যবহার করতে পারেন বা JSON.parse ব্যবহার করলেও চলবে।

---

### 🧭 Role-to-Module Access Matrix:

| Logged-In Role | ✅ Can Access Modules                                           | ❌ Cannot Access   |
| -------------- | -------------------------------------------------------------- | ----------------- |
| SUPER\_ADMIN   | Admin, Doctor, Nurse, Receptionist, Billing, Pharmacy, Profile | None              |
| ADMIN          | Doctor, Nurse, Receptionist, Billing, Pharmacy, Profile        | Admin Panel       |
| HR\_MANAGER    | Nurse, Receptionist, Billing Clerk, Profile                    | Admin, Doctor     |
| DOCTOR         | Profile, Patient List (Optional)                               | All other modules |
| NURSE          | Profile, Assigned Patients                                     | Others            |
| RECEPTIONIST   | Profile, Appointment Dashboard                                 | Others            |
| BILLING\_CLERK | Profile, Billing Dashboard                                     | Others            |
| PHARMACIST     | Profile, Medicine Stock                                        | Others            |

---

### 🧾 Optional Modules:

| Module                | Visible To     |
| --------------------- | -------------- |
| Patient List          | DOCTOR         |
| Assigned Patients     | NURSE          |
| Appointment Dashboard | RECEPTIONIST   |
| Billing Dashboard     | BILLING\_CLERK |
| Medicine Stock        | PHARMACIST     |

---

### 🛠️ UI Instructions (Tailwind + Next.js):

1. Create a login page with a dropdown to select role → generate JWT and store in localStorage.
2. On dashboard page:

   * Read and decode token.
   * Determine the current user's role.
   * Use a JavaScript object (RBAC matrix) to decide which modules to show.
3. Each module card can be a Tailwind-styled component.
4. If unauthorized access occurs (e.g., manually visiting `/admin-panel`):

   * Show a 403 "Access Denied" page.
5. Add logout button to clear token.

---

### ✅ Example UI Behavior:

* ✅ If SUPER\_ADMIN logs in → sees all modules
* ✅ If HR\_MANAGER logs in → sees Nurse, Receptionist, Billing Clerk only
* ✅ If PHARMACIST logs in → sees only their own profile and medicine stock
* ❌ If any restricted module is accessed → show “🔒 Access Denied” page

---

### 📚 শেখার লক্ষ্য:

* 🧠 Role-Based UI Filtering
* 🔐 JWT token decoding and role validation
* 🎨 Tailwind CSS ব্যবহার করে Responsive Module UI
* 🧪 RBAC matrix-এর মাধ্যমে authorization কনফিগারেশন

---

✅ আপনি চাইলে আমি Tailwind সহ:

* `login.jsx`
* `dashboard.jsx`
* `rbacMatrix.js`
* `PrivateRoute.jsx` (optional wrapper for route protection)

— এগুলো তৈরির প্রাথমিক কোড বেস দিয়ে দিতে পারি। জানালে শুরু করে দেব।
