# EduTrack — School Management System

A production-ready School Management System with a **React web app**, **Flutter mobile app**, and **Firebase backend**. Supports Admin, Teacher, and Student roles with real-time attendance tracking and Power BI-style analytics dashboards.

---

## Project Structure

```
SchoolManagment/
├── web/                    # React + Vite + Tailwind CSS web application
│   ├── src/
│   │   ├── components/     # Sidebar, Header, StatCard, charts
│   │   ├── contexts/       # AuthContext (Firebase Auth + role detection)
│   │   ├── pages/          # Admin, Teacher, Student dashboards
│   │   └── firebase.js     # Firebase config (⚠️ add your keys here)
│   └── package.json
├── mobile/                 # Flutter mobile application
│   ├── lib/
│   │   ├── screens/        # Login, Dashboard, Attendance, Timetable, Profile
│   │   ├── services/       # AuthService, FirestoreService
│   │   └── models/         # AppUser, AttendanceRecord, TimetableEntry
│   └── pubspec.yaml
└── firebase/               # Firebase configuration
    ├── firestore.rules      # Role-based security rules
    ├── firestore.indexes.json
    ├── firebase.json        # Hosting + Firestore deployment config
    └── .firebaserc          # Project alias (⚠️ add your project ID)
```

---

## Quick Start

### Prerequisites
- **Node.js 18+** (for web app)
- **Flutter SDK 3.0+** (for mobile app)
- **Firebase project** created at [console.firebase.google.com](https://console.firebase.google.com)

### 1. Firebase Setup

1. Create a Firebase project and enable **Authentication** (Email/Password) and **Cloud Firestore**.
2. Register a **Web App** in your Firebase project and copy the config values.
3. Paste them into `web/src/firebase.js` (replace the placeholders).
4. Register an **Android App** and download `google-services.json` into `mobile/android/app/`.
5. Update `firebase/.firebaserc` with your project ID.

### 2. Firestore Initial Data

Create a user document in Firestore (`users` collection) with:
```json
{
  "email": "admin@school.com",
  "displayName": "Admin User",
  "role": "admin"
}
```
Then create the corresponding Firebase Auth user with the same email.

### 3. Web App

```bash
cd web
npm install
npm run dev          # Starts dev server at http://localhost:3000
npm run build        # Production build → web/dist/
```

### 4. Mobile App

```bash
cd mobile
flutter pub get
flutter run          # Launch on connected Android device/emulator
```

### 5. Deploy

```bash
# Deploy Firestore rules + web app to Firebase Hosting
cd firebase
firebase deploy
```

---

## User Roles

| Role | Capabilities |
|------|-------------|
| **Admin** | Manage users, classes, timetable. View analytics. Export CSV reports. |
| **Teacher** | Mark attendance, view schedule, see student lists. |
| **Student** | View own attendance, timetable, and profile. |

---

## Key Features

- 🔐 **Firebase Auth** — Email/password login with role-based routing
- 📊 **Real-time Dashboard** — Charts update instantly when attendance changes
- ✅ **Attendance Flow** — Select class → mark students → save → dashboard updates
- 📅 **Timetable Management** — Day-tab navigation with add/delete
- 📈 **Analytics** — Bar chart, donut chart, line graph (Power BI style)
- 📥 **CSV Export** — Download attendance reports
- 🔒 **Firestore Rules** — Role-based security enforced at database level
- 📱 **Mobile App** — Flutter with Material 3 design

---

## Tech Stack

| Component | Technology |
|-----------|-----------|
| Web Frontend | React 18 + Vite + Tailwind CSS |
| Mobile | Flutter (Dart) |
| Backend/DB | Firebase (Auth + Cloud Firestore) |
| Charts | Recharts (web), fl_chart (mobile) |
| Icons | Lucide React (web), Material Icons (mobile) |
| Hosting | Firebase Hosting / Vercel |
