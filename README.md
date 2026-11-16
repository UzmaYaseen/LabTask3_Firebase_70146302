# 🖥️ UOL Lab Fault Desk

**UOL Lab Fault Desk** is a real-time Android application built in **Java** using **Firebase Realtime Database**. It streamlines computer lab maintenance at the Department of Software Engineering by allowing students to report faulty PCs instantly and providing lab staff with a live-updating board to track and mark faults as resolved.

## ✨ Key Features
- **Instant Fault Reporting:** Submit hardware, software, or network issues with Lab Room, PC Number, Problem Description, and Priority (`High` / `Normal`).
- **Input Validation:** Prevents incomplete submissions with inline `setError()` prompts.
- **Real-Time Sync Board:** Uses Firebase `ValueEventListener` and `RecyclerView` to display all reports newest-first without manual refresh buttons.
- **One-Tap Resolution:** Lab staff can tap any open fault card to update its status to `Fixed` in real time across all connected devices, visually distinguishing resolved cards.
- **Lifecycle & Loading Management:** Displays a `ProgressBar` during initial cloud fetch and cleanly detaches Firebase listeners in `onDestroy()` to prevent memory leaks.

## 🛠️ Tech Stack
- **Language:** Java
- **UI Components:** XML, Material Design 3, `RecyclerView`, `CardView`, `ConstraintLayout`
- **Backend / Cloud:** Firebase Realtime Database (`firebase-bom`, `firebase-database`)
- **IDE:** Android Studio

## 📂 Project Architecture
- `FaultReport.java` — POJO data model representing a fault report (`id`, `labRoom`, `pcNumber`, `problem`, `priority`, `status`).
- `ReportFaultActivity.java` — Form screen with validation and Firebase `push().setValue()` write logic.
- `MainActivity.java` — Live fault board attaching a real-time `ValueEventListener` to the `LabFaults` node.
- `FaultAdapter.java` — Custom `RecyclerView.Adapter` handling dynamic priority badges, card styling, and item click events.

## 🔒 Security Note
`app/google-services.json` is excluded from version control via `.gitignore` to keep Firebase project credentials private.
