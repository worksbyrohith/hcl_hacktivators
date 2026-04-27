<div align="center">

# 💊 Medi-fy

### *Your trusted online pharmacy — delivered with care*

**A modern, role-based pharmacy management platform built with Angular 21.**

Browse medicines · Upload prescriptions · Manage inventory · Track orders — all in one place.

<br />

[![Angular](https://img.shields.io/badge/Angular-21.2-DD0031?style=for-the-badge&logo=angular&logoColor=white)](https://angular.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.9-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![RxJS](https://img.shields.io/badge/RxJS-7.8-B7178C?style=for-the-badge&logo=reactivex&logoColor=white)](https://rxjs.dev/)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![License](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)](LICENSE)

<br />

[**Features**](#-features) •
[**Tech Stack**](#%EF%B8%8F-tech-stack) •
[**Quick Start**](#-quick-start) •
[**Docker**](#-run-with-docker) •
[**Roadmap**](#%EF%B8%8F-roadmap) •
[**Team**](#-the-hacktivators)

<br />

> 🏆 Built during the **HCL Hacktivators Hackathon** by Team Hacktivators

</div>

<br />

---

## 🌟 Overview

**Medi-fy** is a full-featured online pharmacy web application that connects three types of users — **Customers**, **Pharmacists**, and **Admins** — into a single, seamless ordering experience.

| 🛍️ **Customers**            | 💊 **Pharmacists**          | 🛠️ **Admins**                 |
| :--------------------------- | :--------------------------- | :----------------------------- |
| Browse 500+ verified medicines, upload prescriptions, and check out securely | Review prescription uploads and approve or reject submissions | Manage the catalog, process orders, and monitor stock levels |

<br />

---

## ✨ Features

<table>
<tr>
<td width="33%" valign="top">

### 🛍️ For Customers

- 🔍 **Smart Search** by name, brand, or category
- 📚 **Rich Catalog** — Pain Relief, Antibiotics, Vitamins, Skin Care, Diabetes, Heart & BP
- 🛒 **Live Cart** with quantity controls and pricing
- 🚚 **Free Delivery** with real-time order tracking
- 📄 **Prescription Upload** for Rx-only medicines
- 🔐 **Secure Account** with saved shipping address

</td>
<td width="33%" valign="top">

### 💊 For Pharmacists

- 📥 **Review Queue** of pending prescriptions
- ✅ **Approve / Reject** with one click
- 🗂️ **Status Filters** — Pending, Approved, Rejected
- 🖼️ **Visual Verification** of uploaded images
- 👤 **Customer Context** for every submission
- ⚡ **Fast Triage** workflow

</td>
<td width="33%" valign="top">

### 🛠️ For Admins

- 📊 **Dashboard** with quick-action cards
- 💉 **Medicine CRUD** — add, edit, deactivate
- 📦 **Order Processing** end-to-end
- ⚠️ **Low-Stock Reports** for restocking
- 🏷️ **Inventory Control** by category
- 📈 **Operations Overview** at a glance

</td>
</tr>
</table>

<br />

---

## 🏗️ Tech Stack

<div align="center">

| Layer            | Technology                                 |
| :--------------- | :----------------------------------------- |
| 🎨 **Framework**     | Angular 21.2 *(Standalone Components)*     |
| 🔤 **Language**      | TypeScript 5.9                             |
| ⚡ **Reactivity**    | RxJS 7.8                                   |
| 🧭 **Routing**       | Angular Router                             |
| 📝 **Forms**         | Angular Reactive Forms                     |
| 🎀 **Styling**       | CSS3 with custom design system             |
| 🔧 **Build Tool**    | Angular CLI + `@angular/build`             |
| 🧪 **Testing**       | Vitest / Jasmine                           |
| ✨ **Code Quality**  | Prettier + EditorConfig                    |
| 🐳 **Container**     | Docker                                     |

</div>

<br />

---

## 🚀 Quick Start

### 📋 Prerequisites

- 🟢 **Node.js** 20+ and **npm** 11+
- 🅰️ **Angular CLI** 21+ — `npm install -g @angular/cli`
- 🐳 *(Optional)* **Docker** for containerized runs

<br />

### 🛠️ Installation

**1️⃣ Clone the repository**

```bash
git clone https://github.com/worksbyrohith/hcl_hacktivators.git
cd hcl_hacktivators
```

**2️⃣ Install dependencies**

```bash
npm install
```

**3️⃣ Start the development server**

```bash
ng serve
```

🎉 Open your browser at **http://localhost:4200/** — the app live-reloads on every file change.

<br />

---

## 🐳 Run with Docker

```bash
# 🔨 Build the image
docker build -t medify-client .

# 🚀 Run the container
docker run -p 4200:4200 medify-client
```

Then visit **http://localhost:4200/** — the entire stack is containerized and ready to go.

<br />

---

## 📜 Available Scripts

<div align="center">

| Command           | Description                                       |
| :---------------- | :------------------------------------------------ |
| `npm start`       | 🚀 Start dev server on `0.0.0.0:4200`             |
| `npm run build`   | 📦 Production build into `dist/`                  |
| `npm run watch`   | 👀 Build in watch mode (development config)       |
| `npm test`        | 🧪 Run unit tests with Vitest                     |

</div>

<br />

---

## 📂 Project Structure

```
hcl_hacktivators/
│
├── 📁 public/                     # Static assets served as-is
├── 📁 src/
│   ├── 📁 app/
│   │   ├── 📁 components/         # Reusable UI components
│   │   ├── 📁 pages/              # Route-level pages
│   │   ├── 📁 services/           # API & business-logic services
│   │   ├── 📁 models/             # TypeScript interfaces
│   │   └── 📁 guards/             # Route guards (auth, role)
│   ├── 📁 assets/                 # Images, icons, fonts
│   └── 🎨 styles.css              # Global styles
│
├── 🐳 Dockerfile                  # Container definition
├── ⚙️ angular.json                # Angular workspace config
├── 📦 package.json                # Dependencies & scripts
└── 🔧 tsconfig.json               # TypeScript config
```

<br />

---

## 👥 User Roles

<div align="center">

| 🎭 Role           | 🔑 Capabilities                                                                          |
| :---------------- | :--------------------------------------------------------------------------------------- |
| 🛍️ **Customer**     | Browse medicines · Manage cart · Place orders · Upload prescriptions · Track deliveries |
| 💊 **Pharmacist**   | Review prescription uploads · Approve / reject submissions                              |
| 🛠️ **Admin**        | Manage medicine catalog · Process orders · View low-stock reports · Oversee operations  |

</div>

<br />

---

## 🗺️ Roadmap

- [ ] 💳 **Payment gateway integration** — Razorpay & Stripe
- [ ] 📱 **Progressive Web App** — Offline support & installable
- [ ] 🔔 **Real-time notifications** — Order updates via WebSockets
- [ ] 🌐 **Multi-language support** — English, Hindi, Tamil
- [ ] 📈 **Sales analytics dashboard** — Charts & insights for admins
- [ ] 🤖 **AI-powered recommendations** — Personalized medicine suggestions
- [ ] 🚚 **Live delivery tracking** — Map-based order tracking

<br />

---

## 🤝 Contributing

Contributions, issues, and feature requests are warmly welcomed!

```bash
# 1️⃣  Fork the project
# 2️⃣  Create your feature branch
git checkout -b feature/AmazingFeature

# 3️⃣  Commit your changes
git commit -m 'feat: add AmazingFeature'

# 4️⃣  Push to your branch
git push origin feature/AmazingFeature

# 5️⃣  Open a Pull Request 🎉
```

<br />

---

## 👨‍💻 The Hacktivators

<div align="center">

Built with ❤️ during the **HCL Hacktivators Hackathon**

> *"Making healthcare more accessible, one click at a time."*

</div>

<br />

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

<br />

---

<div align="center">

### ⭐ If you found this project helpful, please consider giving it a star!

**Made with 💚 by Team Hacktivators**

[**⬆ Back to top**](#-medi-fy)

</div>
