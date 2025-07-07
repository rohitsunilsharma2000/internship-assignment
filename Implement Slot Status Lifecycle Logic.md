

---

## 🧾 **Task: Implement Slot Status Lifecycle Logic**

### 🗂️ স্লট স্ট্যাটাস পরিচালনা লজিক

---

### 🎯 **Objective / লক্ষ্য**

To manage the **status transitions of appointment slots** in a controlled way throughout their lifecycle — from available to booked, completed, no-show, etc.
**অ্যাপয়েন্টমেন্ট স্লটগুলোর অবস্থা (status) কীভাবে সময় ও ঘটনার উপর ভিত্তি করে পরিবর্তিত হবে তা সিস্টেমে যুক্ত করা।**

---

### 📋 **Slot Status Definitions | স্লট স্ট্যাটাস ব্যাখ্যা**

| **Status**    | **Meaning (English)**                             | **ব্যাখ্যা (Bengali)**                                           |
| ------------- | ------------------------------------------------- | ---------------------------------------------------------------- |
| `Unavailable` | Doctor not available (emergency/leave)            | ডাক্তারের জরুরি অনুপস্থিতি বা ছুটির জন্য স্লট বন্ধ               |
| `Available`   | Slot is open for booking                          | স্লট খোলা আছে, যে কেউ বুক করতে পারে                              |
| `Booked`      | A patient has booked the slot                     | একজন রোগী স্লট বুক করেছেন                                        |
| `Additional`  | Manually added slot beyond normal hours           | ম্যানুয়ালি অ্যাড করা অতিরিক্ত স্লট                              |
| `Arrived`     | Patient has arrived and checked in                | রোগী এসে গেছেন এবং রিসেপশনে চেক-ইন করেছেন                        |
| `Completed`   | Doctor has completed the consultation             | ডাক্তার রোগী দেখা শেষ করেছেন                                     |
| `Walkin`      | Patient came without booking, assigned manually   | পূর্ব বুকিং ছাড়াই রোগী এসেছেন, রিসেপশন থেকে অ্যাসাইন করা হয়েছে |
| `Blocked`     | Temporarily unavailable (break/maintenance/lunch) | লাঞ্চ বা মেইনটেন্যান্স ইত্যাদির জন্য স্লট ব্লক করা               |
| `No Show`     | Booked patient did not show up in time            | নির্ধারিত সময়ে রোগী আসেননি                                      |
| `Reserved`    | Slot is temporarily held (e.g., payment pending)  | স্লট সাময়িকভাবে ধরে রাখা হয়েছে (যেমন পেমেন্ট পেন্ডিং)           |

---

### 🔁 **Slot Status Transitions | স্লট স্ট্যাটাস পরিবর্তনের নিয়ম**

```text
[Available] → [Booked] → [Arrived] → [Completed]
        ↘             ↘
      [Walkin]      [No Show]

[Available] → [Blocked] / [Unavailable]
[Booked] → [Cancelled] (optional future)
[Manual Add] → [Additional]
```

| From Status | To Status  | Trigger (English)                           | ট্রিগার (Bengali)                         |
| ----------- | ---------- | ------------------------------------------- | ----------------------------------------- |
| Available   | Booked     | Patient books appointment                   | রোগী অ্যাপয়েন্টমেন্ট বুক করে             |
| Booked      | Arrived    | Patient checks in at hospital               | রোগী চেক-ইন করে                           |
| Arrived     | Completed  | Doctor completes the consultation           | ডাক্তার দেখা শেষ করেন                     |
| Booked      | No Show    | Patient doesn’t arrive in time              | রোগী নির্ধারিত সময়ে আসে না               |
| Available   | Blocked    | Admin blocks slot (e.g., lunch/maintenance) | অ্যাডমিন স্লট ব্লক করেন                   |
| Available   | Walkin     | Walk-in patient assigned manually           | রিসেপশন থেকে ওয়াক-ইন রোগী অ্যাসাইন করা হয় |
| Any         | Additional | Manual extra slot added due to emergency    | অতিরিক্ত স্লট ম্যানুয়ালি অ্যাড করা হয়েছে  |

---

### 🛠️ **Implementation Requirements | বাস্তবায়ন সংক্রান্ত নির্দেশনা**

#### 1️⃣ SlotStatus Enum Class:

Create an enum with these values:

```java
public enum SlotStatus {
    UNAVAILABLE, AVAILABLE, BOOKED, ADDITIONAL,
    ARRIVED, COMPLETED, WALKIN, BLOCKED, NO_SHOW, RESERVED
}
```

#### 2️⃣ Slot Entity/Table:

Add or confirm fields in the `slots` table/model:

| Field Name        | Type            | Description                    |
| ----------------- | --------------- | ------------------------------ |
| `status`          | ENUM or VARCHAR | Current status of slot         |
| `last_updated_by` | VARCHAR         | Who last modified it           |
| `last_updated_at` | TIMESTAMP       | When it was updated            |
| `priority_tag`    | VARCHAR         | Optional: for Walk-in priority |
| `slot_type`       | VARCHAR         | NORMAL / ADDITIONAL            |

#### 3️⃣ Business Rules:

* Blocked/Unavailable/Completed slots **cannot be booked**
* No overlapping slots allowed
* Reserved slot must expire within a timeout (e.g., 10 mins if payment not made)

---

### ✅ Example Scenario (English + Bengali)

| Time     | Status      | Action Taken                       | ব্যাখ্যা                                     |
| -------- | ----------- | ---------------------------------- | -------------------------------------------- |
| 10:10 AM | Available   | Patient books                      | → Booked                                     |
| 10:10 AM | Booked      | Patient arrives                    | → Arrived                                    |
| 10:10 AM | Arrived     | Doctor completes consultation      | → Completed                                  |
| 10:20 AM | Booked      | Patient doesn’t show up            | → No Show                                    |
| 11:00 AM | Unavailable | Doctor declared emergency          | স্লট unavailable করা হয়                      |
| 11:15 AM | Additional  | Emergency patient slotted manually | ম্যানুয়ালি স্লট তৈরি করে রমেশকে অ্যাড করা হয় |

---

