# 🛜 Smart Wearable Attendance System — ECG + GPS + ESP32

An IoT-based attendance system that verifies *who* you are and *where* you are before marking you present — combining ECG-based biometric identity with GPS geofencing, on an ESP32, synced to Firebase in real time.

![ESP32](https://img.shields.io/badge/ESP32-microcontroller-blue?logo=espressif&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-realtime%20DB-FFCA28?logo=firebase&logoColor=black)
![IoT](https://img.shields.io/badge/IoT-biometric%20%2B%20geofencing-green)
![Status](https://img.shields.io/badge/status-active-success)

---

## 📌 Overview

This project provides an automated, secure, and reliable attendance monitoring system by combining physiological biometrics with location tracking. ECG signals act as a unique biometric identifier, ensuring attendance is only marked when the authorized person is actually wearing the device — eliminating proxy attendance. GPS-based geofencing independently verifies that the person is physically present within the designated campus boundary. Attendance is only recorded when **both** conditions are satisfied, and the result is synced to Firebase in real time for storage and analysis.

The goal was to remove two persistent problems with manual attendance systems: proxy attendance (someone marking present for a friend who isn't there) and the administrative overhead of manual tracking.

<p align="center">
  <img src="assets/block_diagram.png" alt="Block diagram: ECG sensor and GPS module feed into ESP32, which uploads to Firebase over WiFi, marking attendance only when both checks pass" width="900">
</p>

## 🧩 How it works

1. **ECG authentication** — the wearable's ECG sensor captures the wearer's cardiac signal, used as a biometric identity check. This confirms the device is being worn by its registered owner, not handed off to someone else.
2. **GPS geofencing** — the GPS module checks the device's current coordinates against a predefined campus boundary.
3. **ESP32 decision logic** — attendance is marked present only when **both** the ECG identity check and the GPS geofence check pass.
4. **Firebase sync** — once verified, the attendance record is pushed to Firebase in real time, making it available instantly for dashboards, reports, or audits.

## ✅ Applications

- Automated, proxy-proof attendance for colleges, universities, and workplaces
- Real-time attendance sync to Firebase for instant dashboards, audits, and reporting
- Identity + location verification for secure or restricted-access environments

## 🎯 Use cases

- Attendance is marked automatically the moment an authorized student enters the campus geofence — no manual roll call
- A student cannot mark attendance on someone else's behalf; both ECG identity and GPS location must match
- Administrators get securely logged, auditable records for tracking regularity and punctuality over time

## ⚠️ Design challenge

A core engineering challenge in this system is signal reliability: ensuring ECG readings and GPS coordinates are stable and accurate enough to support real-time verification, since noisy biometric data or GPS drift near geofence boundaries can produce false negatives or false positives. The decision logic is built to require both checks to independently pass, which reduces the chance of either sensor's noise alone triggering an incorrect result.

## ⚙️ Tech stack

`ESP32` · `ECG Sensor` · `GPS Module` · `Firebase Realtime Database` · `C++ / Arduino`

## 📁 Repo structure

```
├── firmware/
│   └── esp32_attendance.ino       # ECG + GPS read, geofence check, Firebase upload
├── docs/
│   └── literature_survey.docx
├── assets/
│   └── block_diagram.png
└── README.md
```

