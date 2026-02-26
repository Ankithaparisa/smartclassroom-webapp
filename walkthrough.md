## 🚀 Firebase Cloud Setup

I have generated the essential security configurations and initial database structures for your Smart Classroom.

### 1. Cloud Firestore (Role-Based Access)
Role management is handled via Firestore. This ensures that a Faculty member cannot spoof an HOD's identity to gain control over the classroom hardware.

*   **Rules File**: `firestore.rules`
*   **Action**: Copy these rules into the **Firestore -> Rules** tab in your Firebase Console.
*   **Initial Data**: In your `users` collection, create a document with the **User's UID** (from Authentication) and add the field `role: "hod"` or `role: "faculty"`.

### 2. Realtime Database (RTDB) Sync
The RTDB is used for high-frequency updates, such as attendance logs and door lock status.

*   **Rules File**: `database.rules.json`
*   **JSON Seed**: `initial_database.json`
*   **Action**: Use the **Import JSON** feature in the **Realtime Database -> Data** tab to seed your project with initial attendance records and infrastructure nodes.

### 3. HOD Power Controls
The system is configured so that even if the UI is bypassed, the **Firebase backend will reject** any `write` requests to the `door_lock` or `automation` nodes unless the authenticated user has the `hod` role.

## 🛠️ Summary of Files Created

1.  `index.html`: Fully integrated web application with Firebase SDK.
2.  `firestore.rules`: Security logic for role-based Firestore access.
3.  `database.rules.json`: Security logic for Realtime Database nodes.
4.  `initial_database.json`: Seeding template for initial attendance and status logs.
