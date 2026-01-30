# MarkMe  
### AI-powered Attendance Intelligence System for Rural Schools

MarkMe is an **Android-based, AI-assisted attendance system** designed for rural and low-resource schools.  
It automates daily attendance using low-cost RFID and prevents proxy attendance through photo verification, while using AI to generate attendance insights and early risk alerts.

The solution aligns with the **AI for Communities, Access & Public Impact** problem statement by improving transparency, efficiency, and decision-making in public education systems.

---

## 🚩 Problem Statement

In many rural schools, attendance is still recorded manually. This leads to:
- Loss of teaching time  
- Human errors in records  
- Proxy attendance  
- Unreliable data affecting government education schemes  

There is a need for a **low-cost, reliable, and verifiable attendance system** that works with minimal infrastructure and supports large-scale public deployment.

---

## 💡 Solution Overview

MarkMe provides a **rural-first attendance intelligence platform** that goes beyond simple data recording.

- Attendance is captured using **RFID-based check-ins**
- **Random photo verification** prevents proxy attendance
- Data is stored securely on **AWS cloud infrastructure**
- An **AI analysis layer** converts attendance data into insights, summaries, and early warnings

The system is optimized for **entry-level Android smartphones**, low bandwidth, and minimal training.

---

## 🔑 Key Features

### Attendance & Verification
- RFID-based student attendance
- Random photo verification to prevent proxy attendance
- Automated session start and end by teachers

### AI-powered Insights
- Daily and weekly attendance summaries
- Attendance trend analysis
- Student risk classification (Low / Medium / High)
- Early warning alerts for irregular attendance

### Rural-first Design
- Android-first application for low-cost devices
- Works in low-bandwidth environments
- Minimal hardware and setup requirements

### Cloud & Scalability
- Secure cloud-based attendance records
- Scalable architecture suitable for government deployment
- Centralized reporting for schools and administrators

### Communication & Transparency
- Automated absentee alerts to parents
- Teacher and admin dashboards
- Government-ready attendance reports

---

## 🤖 Role of AI (Responsible Use)

AI in MarkMe is used **only for decision support**, not surveillance.

AI helps to:
- Detect attendance drops and irregular patterns  
- Identify students needing early attention  
- Generate easy-to-understand summaries for teachers  

❌ No facial recognition  
❌ No continuous monitoring  
✅ Explainable and ethical AI usage  

---

## 🏗️ High-Level Architecture

1. Student scans RFID card  
2. Android app captures attendance  
3. Data is stored in **:contentReference[oaicite:0]{index=0}**  
4. Verification images stored in **:contentReference[oaicite:1]{index=1}**  
5. AI layer analyzes attendance data  
6. Insights and risk alerts are generated  
7. Dashboards and notifications are updated  

---

## 🛠️ Technology Stack

- **Frontend:** Android (Kotlin, XML)  
- **Cloud Database:** Amazon DynamoDB  
- **Cloud Storage:** Amazon S3  
- **AI & Analytics:** Attendance pattern analysis and risk classification  
- **Hardware:** RFID reader and cards  
- **Notifications:** SMS / alert services  

---

## 🎯 Target Users

- Rural school teachers  
- School administrators  
- Students and parents  
- Education authorities  

---

## 🌍 Impact

- Saves teaching time by eliminating manual attendance  
- Prevents proxy attendance  
- Improves data accuracy and transparency  
- Enables early intervention for irregular attendance  
- Scalable for district and state-level education systems  

---

## 📌 Hackathon Alignment

- **AI for Communities, Access & Public Impact**
- AWS-powered cloud infrastructure
- Designed for rural and low-resource environments
- Scalable and government-ready
- Responsible and ethical use of AI

---

## 🚀 Future Enhancements

- Voice-based attendance summaries
- District-level analytics dashboards
- Deeper predictive insights with larger datasets

---

## 🏆 Team Skyrist

Built as part of national hackathon initiatives focused on solving real-world public education challenges through technology and AI.

---

> *MarkMe transforms attendance records into actionable intelligence for rural schools.*
