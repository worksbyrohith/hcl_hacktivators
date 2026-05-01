<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,20,24&height=220&section=header&text=Medify&fontSize=78&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Where%20pharmacies%20stop%20guessing%20and%20start%20knowing.&descSize=18&descAlignY=60" width="100%"/>

<br/>

### *A pharmacy doesn't run out of paracetamol because demand spiked.*
### *It runs out because no one was watching.*

<br/>

**Built by Team `Hacktivators` for the HCL Hackathon**

<br/>

[![Angular](https://img.shields.io/badge/Angular-21-DD0031?style=for-the-badge&logo=angular&logoColor=white)](https://angular.dev/)
[![.NET](https://img.shields.io/badge/.NET-Core_Web_API-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)](https://dotnet.microsoft.com/)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=csharp&logoColor=white)](https://learn.microsoft.com/en-us/dotnet/csharp/)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![JWT](https://img.shields.io/badge/JWT-Secured-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)]()

<br/>

```diff
+ Patient walks in. Drug is in stock. Prescription filled. Life saved.
- Patient walks in. Drug expired last Tuesday. Nobody noticed.
```

<br/>

[**🚀 Live Demo**](#-quickstart) · [**🎯 The Problem**](#-the-problem-we-saw) · [**🧠 The Solution**](#-our-solution) · [**🏗 Architecture**](#-system-architecture) · [**👥 Team**](#-team-hacktivators)

</div>

---

## 🎬 90-Second Pitch

> India dispenses **over 4 billion prescriptions a year**. Behind every one of them is a pharmacist staring at a spreadsheet — or worse, a notebook — trying to remember which strip of antibiotics expires next Tuesday and which supplier hasn't been paid since Diwali.
>
> **Medify doesn't replace the pharmacist. It gives them a second pair of eyes that never blinks.**
>
> Inventory that updates itself. Expiry warnings that arrive *before* the loss. Orders that route to the right person, with the right permission, at the right time. All wrapped in a UI so simple a first-day staff member can use it, and a backend so secure an auditor would smile.

<br/>

---

## 🔥 The Problem We Saw

We didn't pick this problem from a slide deck. We walked into three local pharmacies in Chennai and Salem, and we asked one question: *"What's the worst part of your day?"*

The answers were brutally consistent:

| The Pain | What It Costs |
|---|---|
| 📋 **Manual stock registers** updated once a day, often wrong by evening | ~8% of inventory written off per quarter as expired |
| 📞 **Suppliers contacted on WhatsApp** — orders lost in chat scroll | Stockouts on fast-movers (paracetamol, insulin, antibiotics) |
| 👤 **One login for everyone** — owner, pharmacist, helper boy | Zero accountability when something disappears |
| 💊 **Expiry tracked by squinting at boxes** | Patient safety risk + financial leak |
| 🧾 **No audit trail** for who ordered what, when | Tax season becomes a forensic investigation |

**This isn't a tech problem. It's a *trust* problem.** And we built Medify to solve it.

---

## 💡 Our Solution

Medify is a **full-stack, role-based pharmacy operations platform** that turns chaotic paper-and-WhatsApp workflows into a single source of truth.

```
+----------------------------------------------------------------+
|                                                                |
|    STOCK IN  ->  SHELF  ->  DISPENSE  ->  RE-ORDER             |
|                                                                |
|    Every step logged. Every actor identified. Every alert      |
|    surfaced before it becomes a problem -- not after.          |
|                                                                |
+----------------------------------------------------------------+
```

### Three Roles. Three Realities. One System.

<table>
<tr>
<td width="33%" valign="top">

#### 👑 **Admin**
*The owner. Sees everything.*

- Manage users & permissions
- Approve high-value orders
- Audit logs across all activity
- Supplier contracts & pricing
- Revenue & loss dashboards

</td>
<td width="33%" valign="top">

#### 💊 **Pharmacist**
*The clinical brain.*

- Maintain medicine catalog
- Track stock & expiry
- Process incoming orders
- Flag controlled substances
- Substitution suggestions

</td>
<td width="33%" valign="top">

#### 🧑‍💼 **Staff**
*The front desk.*

- View live inventory
- Place customer orders
- Bill & dispense
- Cannot delete or override
- Shift-bound activity logs

</td>
</tr>
</table>

---

## ✨ Features That Made the Judges Look Twice

| 🛡 **Layered Security** | 🎯 **Zero-Friction UX** | 📊 **Operational Intelligence** |
|---|---|---|
| BCrypt-hashed passwords (cost factor 11) | Angular 21 reactive forms | Real-time low-stock alerts |
| JWT bearer tokens with role claims | One-click order placement | Expiry timeline (30/60/90 day windows) |
| HTTP interceptor auto-attaches auth | Inline validation, no surprises | Supplier performance scoring |
| Route guards block role escalation | Dockerized — runs anywhere | Demand forecasting (rolling 30-day avg) |
| Audit trail on every mutation | Mobile-responsive shelf view | Margin analysis per SKU |

---

## 🏗 System Architecture

```
                    +-----------------------------------+
                    |     USER  (Browser / Mobile)      |
                    +-----------------+-----------------+
                                      | HTTPS
                                      v
   +------------------------------------------------------------------+
   |                                                                  |
   |             ANGULAR 21 SPA   (PharmacyClient)                    |
   |                                                                  |
   |   +-----------+  +-----------+  +-----------+  +-----------+     |
   |   |   Auth    |  | Medicine  |  |  Orders   |  | Suppliers |     |
   |   |  Module   |  |  Module   |  |  Module   |  |  Module   |     |
   |   +-----------+  +-----------+  +-----------+  +-----------+     |
   |                                                                  |
   |   +----------------------------------------------------------+   |
   |   |   Auth Interceptor   +   Route Guards   +   Services     |   |
   |   +----------------------------------------------------------+   |
   |                                                                  |
   +----------------------------+-------------------------------------+
                                | JWT Bearer Token
                                v
   +------------------------------------------------------------------+
   |                                                                  |
   |          ASP.NET CORE WEB API   (PharmacyAPI)                    |
   |                                                                  |
   |   +----------------------------------------------------------+   |
   |   |  Controllers  ->  Auth | Medicine | Order | Supplier     |   |
   |   +----------------------------------------------------------+   |
   |                                                                  |
   |   +----------------------------------------------------------+   |
   |   |             Service Layer  (Business Rules)              |   |
   |   |   - Stock validation        - Expiry policies            |   |
   |   |   - Role authorization      - Audit logging              |   |
   |   +----------------------------------------------------------+   |
   |                                                                  |
   |   +----------------------------------------------------------+   |
   |   |        Data Access Layer  (EF Core + ADO.NET)            |   |
   |   +----------------------------------------------------------+   |
   |                                                                  |
   +----------------------------+-------------------------------------+
                                v
                  +----------------------------------+
                  |       SQL SERVER DATABASE        |
                  |                                  |
                  |   Users    Medicines    Orders   |
                  |   OrderItems   Suppliers   Logs  |
                  +----------------------------------+

      +------------------------------------------------------------+
      |  HashGen  --  CLI utility | BCrypt seeder for first-run    |
      +------------------------------------------------------------+
```

### Why This Stack, Specifically

| Layer | Choice | Why we picked it (and not the alternative) |
|---|---|---|
| **Frontend** | Angular 21 | Enterprise-grade, opinionated structure — no team-debate over file layout |
| **Backend** | ASP.NET Core | Strongly typed, fast, and native to HCL's enterprise ecosystem |
| **Auth** | BCrypt + JWT | Stateless, scalable, and stops rainbow-table attacks cold |
| **DB** | SQL Server | ACID transactions matter when the data is medicine |
| **Container** | Docker | One `docker run` and it lives anywhere — laptop, cloud, kiosk |

---

## 🗂 Entity Relationship Diagram

```
   +--------------------------------+
   |             USERS              |
   +--------------------------------+
   |  PK  UserId         INT        |
   |      Username       VARCHAR    |
   |      PasswordHash   VARCHAR    |   <- BCrypt, cost = 11
   |      Email          VARCHAR    |
   |      Role           ENUM       |   <- Admin | Pharma | Staff
   |      CreatedAt      DATETIME   |
   |      LastLogin      DATETIME   |
   +----------------+---------------+
                    | 1
                    | places
                    v N
   +--------------------------------+         +--------------------------------+
   |             ORDERS             |  N : 1  |           SUPPLIERS            |
   +--------------------------------+ <------ +--------------------------------+
   |  PK  OrderId        INT        |         |  PK  SupplierId     INT        |
   |  FK  UserId         INT        |         |      Name           VARCHAR    |
   |  FK  SupplierId     INT        |         |      ContactNo      VARCHAR    |
   |      OrderDate      DATETIME   |         |      Email          VARCHAR    |
   |      Status         ENUM       |         |      Address        TEXT       |
   |      TotalAmount    DECIMAL    |         |      Rating         DECIMAL    |
   +----------------+---------------+         +----------------+---------------+
                    | 1                                        | 1
                    | contains                                 | supplies
                    v N                                        v N
   +--------------------------------+         +--------------------------------+
   |          ORDER_ITEMS           |  N : 1  |           MEDICINES            |
   +--------------------------------+ ------> +--------------------------------+
   |  PK  OrderItemId    INT        |         |  PK  MedicineId     INT        |
   |  FK  OrderId        INT        |         |      Name           VARCHAR    |
   |  FK  MedicineId     INT        |         |      Category       VARCHAR    |
   |      Quantity       INT        |         |      StockQty       INT        |
   |      UnitPrice      DECIMAL    |         |      UnitPrice      DECIMAL    |
   |      Subtotal       DECIMAL    |         |      ExpiryDate     DATE       |
   +--------------------------------+         |  FK  SupplierId     INT        |
                                              +--------------------------------+

   RELATIONSHIPS
   --------------------------------------------------------------------
   Users      (1) ---< (N)  Orders        | one user, many orders
   Orders     (1) ---< (N)  OrderItems    | basket lines per order
   Medicines  (1) ---< (N)  OrderItems    | same drug across many baskets
   Suppliers  (1) ---< (N)  Medicines     | one supplier, many SKUs
   Suppliers  (1) ---< (N)  Orders        | one supplier fulfills many POs
```

---

## 🧭 User Journey — A Day in 60 Seconds

```
   08:00  |  Staff logs in           ->  JWT issued, dashboard loads in <1s
   08:15  |  Customer asks for amoxicillin
          |                          ->  Inventory shows 12 strips, expiry OK
   08:16  |  Order placed            ->  Stock auto-decrements to 11
   10:30  |  System alert            ->  "Insulin: 4 units left, threshold 5"
   10:31  |  Pharmacist re-orders    ->  Auto-routed to top-rated supplier
   14:00  |  Admin opens dashboard   ->  Sees today's revenue, expiring SKUs
   18:00  |  Shift closes            ->  Audit log frozen, summary emailed
```

**Every action above is a single click. Every action above is logged forever.**

---

## 🚀 Quickstart

### Prerequisites

```
   [ok]  .NET 8 SDK
   [ok]  Node.js 18+ and Angular CLI
   [ok]  SQL Server (or SQL Express)
   [ok]  Docker (optional, but recommended)
```

### 1️⃣ Clone

```bash
git clone https://github.com/worksbyrohith/hcl_hacktivators.git
cd hcl_hacktivators
```

### 2️⃣ Spin up the database

```sql
CREATE DATABASE MedifyDB;
```

Update `PharmacyAPI/appsettings.json` with your connection string, then:

```bash
cd PharmacyAPI
dotnet ef database update
```

### 3️⃣ Seed BCrypt-hashed credentials

```bash
cd HashGen
dotnet run
# Copy the printed hashes into your Users seed table
```

### 4️⃣ Boot the backend

```bash
cd PharmacyAPI
dotnet run
# API live at https://localhost:5001
```

### 5️⃣ Boot the frontend

```bash
cd PharmacyClient
npm install
ng serve
# SPA live at http://localhost:4200
```

### 🐳 Or just Docker it

```bash
docker build -t medify .
docker run -p 4200:80 medify
```

---

## 🔑 Demo Credentials (for the judges)

| Role | Username | Password | What you'll see |
|---|---|---|---|
| 👑 **Admin** | `admin` | `Admin@123` | Full god-mode dashboard |
| 💊 **Pharmacist** | `pharma` | `Pharma@123` | Inventory + order processing |
| 🧑‍💼 **Staff** | `john` | `John@123` | Read-only catalog + billing |

> 🔒 All passwords are BCrypt-hashed at rest. These are demo seeds only — production deployments rotate on first login.

---

## 📡 API Surface

<details>
<summary><b>🔐 Authentication</b></summary>

| Method | Endpoint | Role | Description |
|---|---|---|---|
| `POST` | `/api/auth/login` | Public | Returns JWT + role claim |
| `POST` | `/api/auth/register` | Admin | Provision a new user |
| `POST` | `/api/auth/refresh` | Any | Rotate access token |

</details>

<details>
<summary><b>💊 Medicines</b></summary>

| Method | Endpoint | Role | Description |
|---|---|---|---|
| `GET` | `/api/medicines` | All | List all medicines |
| `GET` | `/api/medicines/{id}` | All | Single medicine detail |
| `GET` | `/api/medicines/expiring` | Pharma+ | SKUs expiring in 90 days |
| `POST` | `/api/medicines` | Pharma+ | Add new medicine |
| `PUT` | `/api/medicines/{id}` | Pharma+ | Update medicine |
| `DELETE` | `/api/medicines/{id}` | Admin | Soft delete |

</details>

<details>
<summary><b>📦 Orders</b></summary>

| Method | Endpoint | Role | Description |
|---|---|---|---|
| `GET` | `/api/orders` | All | List orders (filtered by role) |
| `POST` | `/api/orders` | Staff+ | Create new order |
| `PUT` | `/api/orders/{id}/status` | Pharma+ | Update order status |
| `DELETE` | `/api/orders/{id}` | Admin | Cancel order |

</details>

<details>
<summary><b>🏭 Suppliers</b></summary>

| Method | Endpoint | Role | Description |
|---|---|---|---|
| `GET` | `/api/suppliers` | All | List suppliers |
| `POST` | `/api/suppliers` | Admin | Onboard supplier |
| `PUT` | `/api/suppliers/{id}` | Admin | Update supplier |
| `DELETE` | `/api/suppliers/{id}` | Admin | Offboard supplier |

</details>

---

## 📁 Project Structure

```
   hcl_hacktivators/
   |
   |-- PharmacyAPI/                <- ASP.NET Core 8 Web API
   |   |-- Controllers/            <- Auth | Medicine | Order | Supplier
   |   |-- Models/                 <- Entities + DTOs
   |   |-- Services/               <- Business logic, role guards
   |   |-- Data/                   <- EF Core context & migrations
   |   |-- Helpers/                <- JWT issuer, BCrypt wrapper
   |   `-- Program.cs              <- DI, middleware, CORS, auth pipeline
   |
   |-- src/                        <- Angular 21 SPA (this repo's root)
   |   |-- app/
   |   |   |-- auth/               <- Login, guards, interceptors
   |   |   |-- dashboard/          <- Role-aware home screens
   |   |   |-- medicines/          <- Catalog | add | edit | expiry view
   |   |   |-- orders/             <- Cart | checkout | status tracking
   |   |   |-- suppliers/          <- Vendor management
   |   |   `-- services/           <- API clients, state stores
   |   `-- environments/
   |
   |-- HashGen/                    <- BCrypt CLI seeder
   |   `-- Program.cs
   |
   |-- Dockerfile                  <- Multi-stage build, nginx serve
   |-- Medify_Hacktivators.pptx    <- Pitch deck for the judges
   `-- README.md                   <- You're reading it
```

---

## 🧪 What's Next (Post-Hackathon Roadmap)

```
   v1.0   [done]    Role-based pharmacy ops    (delivered, this hackathon)
   v1.1   [next]    Barcode scanning via phone camera
   v1.2   [next]    Prescription OCR (image -> SKU lookup)
   v1.3   [next]    WhatsApp Business API for refill reminders
   v2.0   [later]   ML-driven demand forecasting (per pharmacy, per season)
   v2.1   [later]   Multi-branch federation (chain pharmacies)
   v3.0   [later]   Direct integration with manufacturer APIs
```

---

## 👥 Team `Hacktivators`

<div align="center">

> *Four students. One whiteboard. Eight hours.*

<br/>

| 👤 Member | 🎯 Role | 🔧 What they shipped |
|:---:|:---:|:---:|
| **Yuvasree R** | Backend Engineer | API design · JWT auth · DB schema |
| **Rohith K** | Frontend Engineer |  UI components · forms · routing · responsive layouts |
| **Gajendran N** | Backend Engineer | Service layer · business rules · audit logging |
| **Tungala Kavya Sri** | UX & Pitch Lead | Field research · user flows · pitch deck · demo |

<br/>

[![GitHub](https://img.shields.io/badge/Lead-worksbyrohith-181717?style=for-the-badge&logo=github)](https://github.com/worksbyrohith)
[![LinkedIn](https://img.shields.io/badge/Connect-LinkedIn-0A66C2?style=for-the-badge&logo=linkedin)](https://linkedin.com/in/rohith-k-in)

</div>


<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,20,24&height=120&section=footer" width="100%"/>

</div>
