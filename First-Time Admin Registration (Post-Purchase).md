নিচে প্রথমবারের অ্যাডমিন রেজিস্ট্রেশনের জন্য Step 1 থেকে Step 5 বাংলায় দেওয়া হলো:

---

## 🛡️ **প্রথমবার অ্যাডমিন রেজিস্ট্রেশন (Post-Purchase)**

### 🎯 লক্ষ্য:

কোনও হাসপাতাল বা ক্লিনিক যখন সিস্টেমটি কিনে, তখন প্রথম ব্যবহারকারী (মালিক বা আইটি অ্যাডমিন) যেন নিরাপদভাবে অ্যাডমিন হিসাবে রেজিস্টার করতে পারেন — এটি নিশ্চিত করা।

---

### ✅ ধাপে ধাপে প্রক্রিয়া:

### 🔹 **Step 1: ক্রয় নিশ্চিতকরণ / প্রোডাক্ট অ্যাক্টিভেশন**

* ক্রয় সম্পন্ন হলে:

  * ক্লায়েন্ট একটি **অ্যাক্টিভেশন লিঙ্ক** ইমেইলে পাবেন (যেমনঃ ৪৮ ঘণ্টার জন্য বৈধ)
  * অথবা একটি **প্রথমবার রেজিস্ট্রেশন ফর্ম** লিঙ্ক পাবেন যেখানে গিয়ে অ্যাডমিন রেজিস্ট্রেশন করা যাবে

---

### 🔹 **Step 2: প্রথম অ্যাডমিন রেজিস্ট্রেশন ফর্ম**

* নিচের তথ্য সংগ্রহ করা হবে:

  * পুরো নাম
  * মোবাইল নম্বর ও ইমেইল
  * পছন্দের ইউজারনেম
  * পাসওয়ার্ড (পুনরায় কনফার্মসহ)
  * হাসপাতালের নাম
  * 🎯 **রোল অটো-অ্যাসাইন হবে: `SUPER_ADMIN`**

---

### 🔹 **Step 3: প্রথম অ্যাডমিন সেটআপ**

* রেজিস্ট্রেশনের পর:

  * সিস্টেমে প্রথম অ্যাডমিন ব্যবহারকারী তৈরি হবে
  * এই অ্যাডমিন পারবেন:

    * ডাক্তার, নার্স, বিলিং স্টাফ অ্যাড করতে
    * রোল অ্যাসাইন করতে
    * হাসপাতালের সেটিংস কনফিগার করতে

---

### 🔹 **Step 4: নিরাপত্তা নিশ্চিতকরণ**

* ইমেইল বা মোবাইল **ভেরিফিকেশন বাধ্যতামূলক**
* শক্তিশালী পাসওয়ার্ড নির্ধারণ করতে হবে
* "Terms of Use" দেখানো হবে এবং গ্রহণ করতে হবে

---

### 🔹 **Step 5: অ্যাডমিন ড্যাশবোর্ডে রিডাইরেক্ট**

* সবকিছু সফলভাবে সম্পন্ন হলে:

  * অ্যাডমিন ড্যাশবোর্ডে পাঠানো হবে
  * সেখান থেকে:

    * অন্যান্য স্টাফ অ্যাড করা যাবে
    * OPD/ডিপার্টমেন্ট সেটআপ করা যাবে
    * রোল, বিলিং, রিপোর্ট কনফিগার করা যাবে

---

## 📝 প্রাথমিক অ্যাডমিন রেজিস্ট্রেশনের জন্য প্রয়োজনীয় তথ্য (Necessary Fields for Admin)

| 🏷️ Field Name              | 📌 Type         | 🔒 Purpose / Reason                                                       |
| --------------------------- | --------------- | ------------------------------------------------------------------------- |
| **Full Name**               | Text            | ব্যক্তিগত পরিচয়ের জন্য (e.g., "Dr. Rakesh Sinha")                         |
| **Email Address**           | Email           | ভেরিফিকেশন ও লগইনের জন্য (must be unique)                                 |
| **Mobile Number**           | Phone           | OTP ভেরিফিকেশনের জন্য, যোগাযোগের জন্য                                     |
| **Username**                | Text            | সিস্টেমে লগইন করার জন্য (unique, e.g., admin01)                           |
| **Password**                | Password        | অ্যাকাউন্ট সুরক্ষার জন্য (strong password required)                       |
| **Confirm Password**        | Password        | ভুল পাসওয়ার্ড এন্ট্রি রোধে                                                |
| **Hospital/Clinic Name**    | Text            | অ্যাকাউন্ট কোন প্রতিষ্ঠানের জন্য সেটআপ হচ্ছে তা জানার জন্য                |
| **Hospital Type**           | Dropdown        | যেমন: Clinic, Nursing Home, Multispecialty Hospital (optional but useful) |
| **Address**                 | Text (Optional) | ভবিষ্যতের বিলিং ও কনফিগারেশনের জন্য                                       |
| **Registration Role**       | Hidden (fixed)  | Always set to `SUPER_ADMIN` — first-time admin only gets this             |
| **Agree to Terms & Policy** | Checkbox        | Terms of Use গ্রহণ না করলে রেজিস্ট্রেশন সাবমিট হবে না                     |

---

### ✅ Optional Fields (Good to have)

| Field Name         | Purpose                                        |
| ------------------ | ---------------------------------------------- |
| Hospital Logo      | Branding ও রিসিপ্টে/প্রেসক্রিপশনে দেখানোর জন্য |
| Preferred Language | UI ভাষা পছন্দ (বাংলা/ইংরেজি)                   |
| Timezone           | শিডিউলিং ও রিপোর্টের জন্য সময় গণনা সহায়ক       |

---

### Example Summary for Admin Signup Form:

> **👤 Name:** Dr. Rakesh Sinha
> **📧 Email:** [rakesh@abcclinic.com](mailto:rakesh@abcclinic.com)
> **📱 Mobile:** +91-9876543210
> **🏥 Hospital Name:** ABC Clinic
> **🆔 Username:** adminabc
> **🔐 Password:** \*\*\*\*\*\*\*\*
> **📍 Address:** 23, Salt Lake, Kolkata
> **🛡️ Role:** SUPER\_ADMIN (auto-assigned)
> **✅ Agree to Terms:** ☑️

---


Here's the **Java DTO** and **SQL table** definition for first-time admin registration **without annotations**, keeping it clean and framework-agnostic:

---

## 🧾 1. Java Class – `AdminRegistrationDTO` (No annotations)

```java
package com.example.hms.dto;

public class AdminRegistrationDTO {

    private String fullName;
    private String email;
    private String mobile;
    private String username;
    private String password;
    private String confirmPassword;
    private String hospitalName;
    private String hospitalType;        // Optional
    private String address;             // Optional
    private String preferredLanguage;   // Optional
    private String timezone;            // Optional
    private boolean agreeToTerms;
    private final String role = "SUPER_ADMIN"; // Auto-assigned

    // Getters and setters

    
}
```

---

## 🧱 2. SQL Table – `users`

```sql
CREATE TABLE users (
    id BIGSERIAL PRIMARY KEY,
    full_name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    mobile VARCHAR(15) NOT NULL,
    username VARCHAR(50) NOT NULL UNIQUE,
    password_hash VARCHAR(255) NOT NULL,
    hospital_name VARCHAR(100) NOT NULL,
    hospital_type VARCHAR(50),
    address TEXT,
    preferred_language VARCHAR(10),
    timezone VARCHAR(50),
    role VARCHAR(20) DEFAULT 'SUPER_ADMIN',
    terms_accepted BOOLEAN DEFAULT FALSE,
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---


