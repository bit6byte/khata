# 📒 Khaata — Project Overview

> **Khaata** ek modern, offline-first ledger / udhaar (khata) management app hai jo dukaandaaron aur chhote businesses ke liye banaya gaya hai. Isse customer-wise udhaar, partial payments, aur due dates ko ek clean dark-themed interface mein track kiya ja sakta hai.

---

## 🎯 Project Title & Summary

| Field | Detail |
|-------|--------|
| **App Name** | Khaata |
| **Tagline** | *Your ledger, simplified* |
| **Type** | Mobile Application (Android-first, Flutter) |
| **Primary Purpose** | Customer-wise khata/udhaar tracking with partial payments, payment history, due-date tracking aur JSON backup/restore |
| **Target Audience** | Retail shopkeepers, kirana store owners, small traders, aur koi bhi vyakti jo informal credit (udhaar) maintain karta hai |

**Core idea:** Ek customer ka saara udhaar record rakho, partial payments receive karo, aur real-time remaining balance dekho — bina internet ya kisi server ke.

---

## ✨ Key Features

### 📝 1. Khaata (Udhaar) Entry
- Customer name, multiple line-items (name + price), return/due date aur description ke saath naya khaata banao.
- Total amount automatically items ke sum se calculate hota hai.

### 💰 2. Partial Payments
- Ek khaate ke against **kai baar** partial payment receive kar sakte ho.
- Har payment ka **amount, date aur optional note** save hota hai.
- Remaining amount real-time update hota hai; poora hone par khaata auto "Fully Paid" ho jaata hai.
- Overpayment se bachne ke liye applied amount remaining tak cap hota hai.

### 🧾 3. Khaata Detail Page
- Total / Paid / Remaining ka **progress bar** status card.
- Items list, return date, paid-on date, description.
- **Payment history** (latest first) — har entry ka amount, date, note.

### 👤 4. Customer Detail Page
- Customer ka **Total Khaata, Remaining, % received** progress card.
- Saare khaatas ki list (Paid / Partially Paid / Unpaid badges).
- Per-khaata tap → detail page; "Receive Payment" shortcut.

### 🏠 5. Home Dashboard
- Active aur Paid **tabs** (TabController).
- Customer-wise cards: total outstanding, active/paid counts, credit score badge.
- Summary card with overall balance.

### 📊 6. Credit Scoring
- Har customer ka score (0–200) based on on-time vs delayed/overdue payments.
- Labels: **Excellent / Good / Average / Poor / Bad** with color coding.

### 💾 7. Backup & Restore (JSON)
- **Backup:** user apna folder pick karta hai, app wahan timestamped `.json` file save karti hai.
- **Restore:** JSON file pick karke saara data import (upsert by id).

### ⚙️ 8. Settings
- **Dynamic app version** (pubspec se auto-fetch via `package_info_plus`).
- **Danger Zone:** "Delete All Data" with confirmation dialog.
- Backup / Restore actions.

### 🖼️ 9. Camera (Experimental)
- Standalone camera screen (front/back toggle, capture) — `camera` package.

---

## ⚖️ Pros & Cons / Trade-offs

### ✅ Pros
| Strength | Why it matters |
|----------|----------------|
| 🚀 **Blazing local DB** | Hive is key-value, no-SQL — extremely fast reads/writes |
| 📴 **Fully offline** | No server/internet needed; data device par safe |
| 🧩 **Clean separation** | Models / Provider / Screens — easy to maintain |
| 💵 **Partial payments** | Real-world credit tracking with per-payment history |
| 🔄 **Reactive UI** | `Consumer` + `notifyListeners` → instant refresh |
| 📦 **Portable backup** | Plain JSON — human-readable, easy to migrate |
| 🛡️ **Backward compatible storage** | Old Hive data safely upgrades |
| 🎨 **Polished dark UI** | Consistent Material 3 design system |

### ⚠️ Cons / Limitations
| Limitation | Detail / Edge case |
|------------|--------------------|
| 🖼️ **Image support incomplete** | `image_picker`/`camera` declared; camera screen standalone, not wired into add-khaata; `khaata_card.dart` unused |
| 🧪 **Sample data seed** | First launch demo records add karta hai — production mein real empty-start chahiye |
| 🌐 **No cloud sync** | Multi-device sync / accounts nahi hain (intentional offline design) |
| 🔢 **No edit/delete single item** | Khaata edit karne ka flow nahi (sirf delete poora khaata) |
| 📉 **Score heuristics** | Credit score simple delta formula hai, configurable nahi |
| 🗃️ **Backup = full upsert only** | Restore merge/delete conflict handling basic hai |
| 🧾 **No PDF/WhatsApp share** | Statement export/share abhi nahi hai |
| ♻️ **Deprecated APIs** | `withOpacity` / `material.dart` widespread — future Flutter par migrate karna hoga |


<p align="center">
  <b>📒 Khaata</b> — <i>Your ledger, simplified.</i><br/>
   Develop by Ahmed Khan • Built with Flutter 
</p>
