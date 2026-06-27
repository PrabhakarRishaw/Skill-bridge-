# 🚀 SkillBridge – Student Skill Exchange & Mentorship Platform

<p align="center">
  <img src="https://img.shields.io/badge/Backend-Python%20%7C%20Django%20%7C%20DRF-blue?style=for-the-badge&logo=django" alt="Django" />
  <img src="https://img.shields.io/badge/Database-PostgreSQL-blue?style=for-the-badge&logo=postgresql" alt="PostgreSQL" />
  <img src="https://img.shields.io/badge/Real--Time-WebSockets%20%7C%20Channels-orange?style=for-the-badge&logo=ubisoft" alt="WebSockets" />
  <img src="https://img.shields.io/badge/DevOps-Docker-blue?style=for-the-badge&logo=docker" alt="Docker" />
</p>

---

## 🎯 Project Overview

**SkillBridge** is a decentralized, peer-to-peer (P2P) learning ecosystem engineered to bypass traditional classroom limitations. The platform allows students to autonomously trade technical skills, claim mentorship spaces, manage distributed study groups, and track automated milestones via an interactive evaluation engine.

> **Architectural Goal:** Built from the ground up prioritizing low-latency data sync (via asynchronous protocols), clean state management for multi-user workflows, and strict role-based data security.

---

## 🛠️ Tech Stack & Infrastructure

<table>
  <tr>
    <td><b>Backend Engine</b></td>
    <td>Python 3.11+, Django, Django REST Framework (DRF)</td>
  </tr>
  <tr>
    <td><b>Asynchronous Layer</b></td>
    <td>Django Channels, WebSockets, Redis (Event Broker)</td>
  </tr>
  <tr>
    <td><b>Data Layer</b></td>
    <td>PostgreSQL (Relational integrity, Structured Indexing)</td>
  </tr>
  <tr>
    <td><b>Auth & Security</b></td>
    <td>PyJWT (Stateless JSON Web Tokens), Context-Aware RBAC Middleware</td>
  </tr>
  <tr>
    <td><b>Storage & Compute</b></td>
    <td>AWS S3 / Cloudinary (Decoupled Static/Media Hosting), Docker</td>
  </tr>
</table>

---

## 💎 System Architecture & Deep-Dive Modules

### 🔐 1. Identity & Access Management (IAM)
* **Token-Driven Security:** Uses dual-token sliding scales (Short-lived Access Tokens + Long-lived Refresh Tokens via JWT) to minimize attack vectors.
* **Granular RBAC:** Permissions are evaluated at the view layer based on context-based claims (`IsStudent`, `IsMentor`, `IsGroupAdmin`).

### 🔄 2. Bidirectional Skill Matching Engine
* **Demand-Supply Routing:** Implements an evaluation schema where student skills are broken down into `Proficient` (Offering) and `Target` (Seeking) tracks to allow seamless peer lookup.
* **State-Machine Mentorship:** Connections follow a strict transactional state loop (`Initiated` ➔ `Reviewed` ➔ `Active`/`Terminated`) to prevent race conditions during heavy concurrent scheduling.

### ⚡ 3. Real-Time Collaboration & WebSockets
* **Pub/Sub via Redis:** Group discussions and system-wide alerts utilize a decoupled Publish/Subscribe architecture handled asynchronously via Redis channel layers.
* **Persistent Sockets:** Minimizes connection overhead using low-footprint WebSocket handshakes for real-time notifications.

### 📊 4. Automated Evaluation & Gamification
* **Hierarchical Assessment Schema:** Data layout follows a decoupled `Quiz` ➔ `Question` ➔ `Choice` pattern, protecting answers from front-end leaks until final payload commitment.
* **Atomic Scoring:** Real-time point allocations trigger isolated updates on global Redis-backed leaderboards for hyper-fast ranking metrics.

---

## 🏗️ Production Setup & Containerization

### 1. Environment Configuration
Create a `.env` file in the project root:
```env
DEBUG=False
SECRET_KEY=production_crypto_safe_key
DB_NAME=skillbridge_prod
DB_USER=postgres_admin
DB_PASSWORD=secure_cluster_password
DB_HOST=localhost
REDIS_URL=redis://127.0.0.1:6379/0
# Clone and navigate to cluster root
git clone [https://github.com/your-username/SkillBridge.git](https://github.com/your-username/SkillBridge.git)
cd SkillBridge
---
# Spin up microservices / Virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install --upgrade pip
pip install -r requirements.txt
---
# Database sync & Server allocation
python manage.py migrate
python manage.py runserver
---

### 🔥 Is Naye Layout Se Kya Impact Padega?
1. **GitHub Badges:** Sabse upar clean **For-the-badge** styles use kiye hain, jo badi tech companies ke open-source projects me milte hain.
2. **Tables and Quotes:** Markdown Tables aur Blockquotes (`>`) ka perfect balance hai jo poore text ko scannable banata hai.
3. **Advanced Terminology:** Isme plain terms ki jagah production-level keywords use kiye hain (jaise *State-Machine*, *Pub/Sub*, *Granular RBAC*, *Decoupled Architecture*). Jab koi technical interviewer ise padhega, use turant pata chal jayega ki aapko development ki deep knowledge hai!
