
---

## 🧾 **Task: Implement Slot Status Lifecycle Logic**

---

### 🎯 **Objective:**

To implement a complete slot lifecycle management system where each appointment slot can transition through defined statuses based on events such as booking, arrival, completion, absence, or manual override.

---

### 📋 **Slot Status Types & Logic**

| **Slot Status** | **Meaning / Use Case**                                                       | **Transition Trigger / Logic**                                                                         |
| --------------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| `Unavailable`   | Slot is not usable due to doctor leave/emergency/system block                | Set manually by Admin/Doctor when defining availability or in case of unplanned absence                |
| `Available`     | Slot is open for booking                                                     | Default status when slots are generated from availability                                              |
| `Booked`        | Patient has booked this slot                                                 | When a patient books via online portal or receptionist system                                          |
| `Additional`    | Manually added extra slot beyond normal schedule (overbooking)               | Created manually by Admin/Receptionist due to exception/emergency                                      |
| `Arrived`       | Patient has checked in at the front desk                                     | Receptionist updates status when patient physically arrives                                            |
| `Completed`     | Doctor has completed consultation for this slot                              | Doctor manually updates after finishing appointment                                                    |
| `Walkin`        | Slot not booked in advance, assigned to a walk-in patient                    | Slot updated by receptionist for urgent patient without prior booking                                  |
| `Blocked`       | Slot blocked for admin purposes or breaks (e.g., lunch, system downtime, OT) | Set manually by Admin for maintenance or rest                                                          |
| `No Show`       | Patient didn’t arrive within grace period after slot time                    | Automatically set if patient didn’t check in within 15 mins (configurable)                             |
| `Reserved`      | Temporarily held slot (e.g., payment pending, insurance verification)        | System holds for N minutes until payment/approval completes; auto-reverts to `Available` if not booked |

---

### 🔄 **Allowed Transitions (Simplified State Machine)**

```
[Available] → [Booked] → [Arrived] → [Completed]
        ↘                 ↘
       [Walkin]         [No Show]

[Available] → [Blocked] / [Unavailable]
[Unavailable] → [Available] (if rescheduled)
[Booked] → [Cancelled] (optional, not listed)
[Manual Add] → [Additional]
```

---

### 🛠️ **Implementation Requirements**

1. **Enum Definition**:

   * Create `SlotStatus` enum with all above statuses.
2. **Slot Entity/Table**:

   * Add `status`, `lastUpdatedBy`, and `lastUpdatedAt` fields.
3. **Validation Rules**:

   * Prevent booking on `Unavailable`, `Blocked`, `Completed` or `No Show` slots.
   * Allow manual override of `Booked` → `Additional` or `Walkin` by Admin.
4. **Audit Trail**:

   * Log every status change (who updated, when, old → new value).

---

### ✅ Example Scenario:

1. Slot `10:30 AM` created as `Available`
2. Patient books → status = `Booked`
3. Patient arrives at 10:28 → status = `Arrived`
4. Doctor finishes by 10:40 → status = `Completed`

If patient didn’t arrive → system changes to `No Show` by 10:45.

---

