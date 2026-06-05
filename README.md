# 💇‍♀️ FSR Beauty Salon — Management System

Application web de gestion pour salons de beauté : rendez-vous, clients, services et tableau de bord.

---

## 👥 Équipe

| Membre | Rôle |
|---|---|
| Karibi Mohammad | Chef de projet / Développeur |
| Yassine Bekkali | Product Owner |
| Douaa Doumiri | Développeur / Testeur |

---

## 🌐 Déploiement

| Service | URL |
|---|---|
| 🖥️ Frontend (Vercel) | https://salon-frontend-nine.vercel.app |
| ⚙️ Backend (Railway) | https://salon-backend-production-5139.up.railway.app |

---

## 🏗️ Architecture

```
Navigateur
    ↓
Vercel — React (frontend/)
    ↓ fetch API
Railway — PHP (backend/)
    ↓ PDO
Railway — MySQL
```

---

## 📁 Structure du dépôt

```
salon-management/
├── frontend/                  ← Application React
│   ├── src/
│   │   ├── api.js             ← Appels HTTP vers le backend
│   │   ├── pages/
│   │   │   ├── Homepage.jsx
│   │   │   ├── Dashboard.jsx
│   │   │   ├── Bookings.jsx
│   │   │   ├── Clients.jsx
│   │   │   └── Services.jsx
│   │   └── components/
│   ├── index.html
│   ├── package.json
│   └── vite.config.js
│
├── backend/                   ← API PHP
│   ├── api/
│   │   ├── bookings.php
│   │   ├── clients.php
│   │   ├── services.php
│   │   └── dashboard.php
│   ├── config/
│   │   ├── db.php
│   │   └── cors.php
│   └── Dockerfile
│
└── README.md
```

---

## 🛠️ Technologies

- **Frontend :** React 18, Vite, CSS, HTML, JavaScript
- **Backend :** PHP 8.2, PDO
- **Base de données :** MySQL (Railway)
- **Déploiement :** Vercel (frontend) + Railway (backend)

---

## 🗄️ Base de données

```sql
CREATE TABLE clients (
  id INT AUTO_INCREMENT PRIMARY KEY,
  patient VARCHAR(100) NOT NULL,
  numero VARCHAR(20) NOT NULL,
  ville VARCHAR(100) NOT NULL,
  note TEXT,
  statut ENUM('actif','inactif') DEFAULT 'actif',
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE services (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nom VARCHAR(100) NOT NULL,
  prix DECIMAL(10,2) NOT NULL,
  employe VARCHAR(100) NOT NULL,
  duree INT NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE bookings (
  id INT AUTO_INCREMENT PRIMARY KEY,
  patient VARCHAR(100) NOT NULL,
  service VARCHAR(100) NOT NULL,
  date DATE NOT NULL,
  price DECIMAL(15,2) NOT NULL,
  statut ENUM('confirme','en-attente','annule') DEFAULT 'en-attente',
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

> `patient` et `service` dans bookings sont du **texte libre** — pas de clés étrangères.

---

## ⚙️ Variables d'environnement (Railway Backend)

```
MYSQLHOST=mysql.railway.internal
MYSQLPORT=3306
MYSQLDATABASE=railway
MYSQLUSER=root
MYSQLPASSWORD=...
```

---

## 🚀 Commande pour lancer en local

### Frontend
```bash
cd frontend
npm install
npm run dev
# → http://localhost:5173
```

### Backend
```bash
cd backend
php -S localhost:8080 -t .
# → http://localhost:8080
```

---

## 📦 Livrables

- `docs/CDC.pdf`
- `docs/WBS-Gantt.pdf`
- `docs/Backlog.pdf`
