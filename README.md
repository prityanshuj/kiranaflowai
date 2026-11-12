<p align="center">
  <img src="east-river-bridge-sunrise.gif" alt="KiranaFlow AI Hero Banner" width="100%">
</p>

<div align="center">

# 🛒 KiranaFlow AI
### Smart Kirana Expiry, Wastage & Inventory Intelligence

<p align="center">
  <img src="https://img.shields.io/badge/TECH4BHARAT-GAVS%20HACKATHON-059669?style=for-the-badge&logo=target&logoColor=white" alt="Tech4Bharat GAVS Hackathon" />
  <img src="https://img.shields.io/badge/PLATFORM-HackCulture-10b981?style=for-the-badge" alt="Platform HackCulture" />
  <img src="https://img.shields.io/badge/THEME-Rural%20FMCG%20%26%20Logistics-070d18?style=for-the-badge&logo=shield&logoColor=10b981" alt="Rural FMCG & Logistics" />
  <img src="https://img.shields.io/badge/PS%205.1-Kirana%20Dead%20Stock%20%26%20Expiry-0284c7?style=for-the-badge" alt="Problem Statement 5.1" />
  <img src="https://img.shields.io/badge/TEAM-FIX%20FELLAS-f97316?style=for-the-badge&logo=users&logoColor=white" alt="Team FIX FELLAS" />
</p>

<p align="center">
  <b>Eliminating dead stock, silent shelf expiration, and stockouts of fast-moving goods through automated FIFO deduction, optical barcode scanning, and velocity-based expiry alerts.</b>
</p>

[Explore Features](#-core-features) • [Architecture](#-architecture--tech-stack) • [Jammu Pilot Dataset](#-jammu-pilot-dataset) • [Meet the Team](#-team-fix-fellas)

</div>

---

## 📌 Executive Summary

**Problem Statement 5.1 — Rural FMCG & Logistics:** *Kiranas tie up cash in dead stock while running out of what sells.* Traditional stores rely on memory to track inventory, causing working capital to get trapped in slow-moving, expiring goods while high-demand essentials run out unexpectedly[cite: 12].

**KiranaFlow AI** replaces guesswork with an offline-first, bilingual retail decision engine:
- 📦 **Batch-Level Stock Memory:** Tracks EAN-13 barcodes, suppliers, exact shelf locations, and batch expiry dates[cite: 1].
- 🧾 **Fast POS with FIFO Deduction:** Automatically deducts stock from the oldest expiring batch first while blocking expired items from checkout.
- ⚠️ **Dual-Check Alert Radar:** Flags both missing expiry dates (staff completeness audit) and batches expiring within 7 days.
- 📊 **Velocity & Expiry Risk Engine:** Separates fast movers from slow movers (`Units / Day`) and calculates Days of Stock Left to prevent dead capital and stockouts.

---

## 🚀 Core Features

### 1. 📦 Granular Batch Ledger & Completeness Check
- **Batch-Wise Tracking:** Stores Product Name, Barcode, Supplier, Batch Code, Cost/MRP, Quantity, and Exact Rack Location (e.g., *Dairy Chiller A*, *Aisle 2 Top*)[cite: 1].
- **Completeness Reminder:** Automatically detects batches entered without an expiry date and nudges staff to update them before checkout.
- **Real-World Wastage Log:** Expired batches (`≤ 0 days`) are pulled from shelves via a 1-click **"Discard / Write-Off"** action to track exact wastage loss (`₹`).

### 2. ⚡ Fast POS & Optical Barcode Scanner
- **Multi-Mode Scanning:** Supports live mobile camera laser viewfinder (`getUserMedia`), USB/Bluetooth barcode guns, and 1-tap quick counter tiles.
- **Strict Expired Item Lockdown:** Automatically prevents expired batches from being billed at the POS counter.
- **Acoustic Checkout Feedback:** Browser-native Web Audio API synthesizes realistic barcode scan beeps and cash register chimes.

### 3. 📈 Sales Velocity & Expiry Risk Matrix
- **Fast vs. Slow Movers:** Ranks products by daily sales velocity (`Units / Day`) to identify high-turnover staples vs. stagnant stock.
- **Days of Stock Left (DOSL):** Calculates exact inventory runway (`Current Quantity ÷ Daily Sales Rate`).
- **Actionable Risk Alerts:** Flags slow-moving items where stock days exceed days until expiry, prompting staff to **Move to Front Shelf (FIFO)** and pause reorders.

### 4. 🌐 Bilingual & Two-Way Responsive UI
- **Instant EN / हिन्दी Toggle:** Animated sliding language pill translates the entire interface between English and Hindi for counter staff ease.
- **Two-Way Device Optimization:** Features a floating Dynamic Island topbar with master tables on desktop, and a compact topbar + thumb-friendly bottom dock on mobile.

---

## 🛠 Architecture & Tech Stack

```
┌────────────────────────────────────────────────────────┐
│                   KiranaFlow AI Client                 │
├─────────────────────┬───────────────────┬──────────────┤
│    Presentation     │   Optical & Audio │  Persistence │
│  Glassmorphic CSS3  │  MediaDevices API │ LocalStorage │
│  Bento Grid Layout  │  Wedge Gun Hook   │  FIFO Engine │
│  EN / हिन्दी Toggle  │   Web Audio API   │ Risk Matrix  │
└─────────────────────┴───────────────────┴──────────────┘
```

| Layer | Technologies |
| :--- | :--- |
| **Frontend Core** | Semantic HTML5, Modern CSS3 (Obsidian & Emerald Glassmorphism), Vanilla JS (ES6+) |
| **Optical Scanner** | HTML5 `navigator.mediaDevices.getUserMedia` Laser Viewfinder, Keyboard Wedge Listener |
| **Audio Telemetry** | Web Audio API (POS Barcode Beep & Cash Register Chime Synthesizer) |
| **Decision Engine** | FIFO Batch Deduction Algorithm, Sales Velocity & DOSL Expiry Risk Calculator |
| **Storage & Offline** | Zero-Latency Client `LocalStorage` (Works seamlessly during internet drops) |

---

## 📍 Jammu Pilot Dataset

The prototype comes pre-seeded with realistic Indian FMCG batches across a pilot Kirana store in Jammu:

| Product Name | Barcode | Category | Rack Location | Expiry Status |
| :--- | :--- | :--- | :--- | :--- |
| **Amul Taaza Toned Milk (1L)** | `8901262010016` | Dairy | Dairy Chiller A | Fast Mover (3 Days Left) |
| **Britannia Brown Bread (400g)** | `8901063012042` | Bakery | Rack 01 Front | Critical (2 Days Left) |
| **Nestlé Maggi Noodles (70g)** | `8901058851245` | Instant Food | Aisle 02 Mid | Healthy Stock |
| **Tata Iodized Salt (1kg)** | `8901719110016` | Staples | Aisle 03 Bottom | Fast Mover |
| **Aashirvaad Shudh Chakki Atta (5kg)**| `8901725121105` | Staples | Floor Stack B | Healthy Stock |
| **Parle-G Gold Biscuits (250g)** | `8901719125416` | Snacks | Rack 02 Top | Missing Expiry (Audit Flag) |
| **Mother Dairy Paneer (200g)** | `8901648020112` | Dairy | Dairy Chiller B | Expired (Locked from POS) |

---

## 👥 Team FIX FELLAS

<table align="center">
  <tr>
    <td align="center" width="25%">
      <a href="https://github.com/prityansjuj">
        <img src="https://ui-avatars.com/api/?name=Prityanshu+Jasrotia&background=0284c7&color=fff&size=100&bold=true" width="100px;" alt="Prityanshu Jasrotia"/><br />
        <sub><b>Prityanshu Jasrotia</b></sub>
      </a><br />
      <small>Lead Architecture & Full-Stack Systems</small><br />
      <a href="https://github.com/prityansjuj"><code>@prityansjuj</code></a>
    </td>
    <td align="center" width="25%">
      <a href="https://github.com/vrindagupta19">
        <img src="https://ui-avatars.com/api/?name=Vrinda+Gupta&background=10b981&color=fff&size=100&bold=true" width="100px;" alt="Vrinda Gupta"/><br />
        <sub><b>Vrinda Gupta</b></sub>
      </a><br />
      <small>Head of Research & Development</small><br />
      <a href="https://github.com/vrindagupta19"><code>@vrindagupta19</code></a>
    </td>
    <td align="center" width="25%">
      <a href="https://github.com/ishmeetsingh15">
        <img src="https://ui-avatars.com/api/?name=Ishmeet+Singh&background=070d18&color=fff&size=100&bold=true" width="100px;" alt="Ishmeet Singh"/><br />
        <sub><b>Ishmeet Singh</b></sub>
      </a><br />
      <small>Product Logic & Retail Workflow Strategy</small><br />
      <a href="https://github.com/ishmeetsingh15"><code>@ishmeetsingh15</code></a>
    </td>
    <td align="center" width="25%">
      <a href="https://github.com/aakritisharma5916-eng">
        <img src="https://ui-avatars.com/api/?name=Akriti+Sharma&background=f97316&color=fff&size=100&bold=true" width="100px;" alt="Akriti Sharma"/><br />
        <sub><b>Akriti Sharma</b></sub>
      </a><br />
      <small>UI/UX Design & Presentation Lead</small><br />
      <a href="https://github.com/aakritisharma5916-eng"><code>@aakritisharma5916-eng</code></a>
    </td>
  </tr>
</table>

---

## 🚦 Roadmap

- [x] **Phase 1: Working Prototype** — FIFO POS billing, optical barcode scanner, bilingual EN/Hindi switcher, expiry risk matrix, and responsive mobile dock.
- [ ] **Phase 2: Jammu Store Pilot** — 30-day live deployment at a local Kirana store to benchmark shelf wastage reduction and stock turnover.
- [ ] **Phase 3: Smart Forecasting & Alerts** — Automated demand forecasting from historical sales, thermal receipt printing, and WhatsApp low-stock alerts.

---

<p align="center">
  <sub>Developed by <b>Team FIX FELLAS</b> for <b>Tech4Bharat - GAVS Hackathon</b> on <b>HackCulture</b> (Rural FMCG & Logistics — PS 5.1).</sub>
</p>
