<p align="center">
  <img src="_system/logo.png" alt="VentureBill Logo" width="280">
</p>

<h1 align="center">VentureBill</h1>

<p align="center">
  <strong>Complete Business Billing, GST, Inventory & Financial Management Platform</strong>
</p>

<p align="center">
  <a href="https://github.com/client1307/VentureBill/releases"><img src="https://img.shields.io/badge/version-1.0.0-blue.svg" alt="Version 1.0.0"></a>
  <a href="https://github.com/client1307/VentureBill/blob/main/_system/LICENSE"><img src="https://img.shields.io/badge/license-MIT-green.svg" alt="License: MIT"></a>
  <a href="#"><img src="https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux%20%7C%20PWA-orange.svg" alt="Platforms"></a>
  <a href="#"><img src="https://img.shields.io/badge/offline-first-success.svg" alt="Offline First"></a>
</p>

---

## 📌 Overview

**VentureBill** is a modern, offline-first commercial billing and business management platform designed specifically for Indian businesses. Built for retail shops, wholesalers, distributors, manufacturers, service providers, and growing enterprises, VentureBill gives you complete control over your invoicing, tax compliance, stock, and finances without requiring an active internet connection.

Your business data stays **100% on your device** with zero subscription lock-in.

---

## ✨ Key Features

### 🧾 Invoicing & Sales Documents
- **Complete GST Document Suite**: Tax Invoices, Proforma Invoices, Credit Notes, Debit Notes, Delivery Challans, and Bills of Supply.
- **Dynamic Tax Splitting**: Automatic CGST, SGST, IGST, and UTGST calculations based on Place of Supply.
- **Multi-Currency Support**: 22 global currencies with live or custom exchange rates for international trade and export invoices (LUT / SEZ).
- **Flexible Discounting & Round-Off**: Item-level, invoice-level percentage, or flat discounts with automatic round-off.
- **Custom Print & PDF Engine**: Thermal (2-inch / 3-inch POS) receipt printing and professional A4/A5 PDF invoices with custom terms, signatures, and UPI QR codes for instant payments.

### 📦 Inventory & Warehouse Management
- Real-time stock tracking with low-stock alerts.
- Product cataloging with HSN/SAC codes, barcodes, custom units (UQC), and tax rates.
- Multi-location stock and batch-level tracking.
- Cost of Goods Sold (COGS) and inventory valuation.

### 🏛️ GST & Statutory Compliance
- **GSTR-1 & GSTR-3B JSON Exports**: Direct offline generation ready for one-click upload to the GST Portal.
- **GSTR-2B Reconciliation**: Match purchase invoices against GSTR-2B automatically to prevent lost Input Tax Credit (ITC).
- **e-Way Bill & e-Invoicing**: Generate compliant JSON payloads for transport and government portals.
- **TDS / TCS Tracking**: Form 26Q & 27EQ statutory tracking (under Sections 194Q and 206C).

### 💰 Accounts, Cash Book & Expenses
- Built-in Cash Book & Bank Books for daily ledger transactions.
- Expense tracking by categories and cost centers.
- Customer & supplier party outstanding statements and age analysis.
- Profit & Loss (P&L) statements and financial summary reports.

### 🛡️ Privacy, Security & Offline-First
- **Offline Reliability**: Create invoices, print receipts, and manage stock completely offline.
- **Data Sovereignty**: All your financial and client data is stored locally on your machine.
- **Granular Backups**: One-click local backup and restore to safeguard against hardware failure.

---

## 🚀 Quick Start & Installation

### Windows
1. Double-click **`VentureBill - WINDOWS.hta`** in the root folder.
2. The launcher will verify your environment, install necessary prerequisites if needed, and start the application.
3. Access VentureBill directly in your browser or desktop window at `http://localhost:47371`.

### macOS
1. Open Terminal and navigate to the project directory:
   ```bash
   chmod +x "VentureBill - MAC.command"
   ./"VentureBill - MAC.command"
   ```

### Linux
1. Run the Linux launcher:
   ```bash
   chmod +x "VentureBill - LINUX.sh"
   ./"VentureBill - LINUX.sh"
   ```

---

## 🛠️ Developer Setup & Architecture

VentureBill is built on a modular Node.js backend with an offline PWA frontend.

### Prerequisites
- [Node.js](https://nodejs.org/) (version 18.0.0 or higher)
- npm or pnpm

### Running Locally

```bash
# Navigate to the system core
cd _system

# Install dependencies
npm install

# Start the application server
npm run server
```

The application will start and serve from:
```
http://localhost:47371
```

---

## 📁 Repository Structure

```text
├── VentureBill - WINDOWS.hta     # Windows Desktop Launcher
├── VentureBill - MAC.command     # macOS Terminal Launcher
├── VentureBill - LINUX.sh        # Linux Shell Launcher
├── VentureBill — Blueprint.md    # Product Architecture & Development Blueprint
├── README.md                     # Project documentation
├── .gitignore                    # Git ignore configuration
└── _system/
    ├── app-icon.ico              # VentureBill application icon
    ├── logo.png                  # VentureBill official brand logo
    ├── server.js                 # Core backend API & local database server
    ├── package.json              # Project dependencies and scripts
    ├── LICENSE                   # Licensing terms
    ├── dist/                     # Optimized production frontend build
    ├── src/                      # Business logic, utilities, and services
    └── scripts/                  # Build, packaging, and asset scripts
```

---

## 📜 License & Attribution

This project is licensed under the **MIT License**.

- **Copyright (c) 2026 Ankit ([ankitmali5521@gmail.com](mailto:ankitmali5521@gmail.com)) — VentureBill**
- *Portions Copyright (c) 2026 DiceCodes*

See the full details in [_system/LICENSE](file:///d:/Free-GST-Billing/_system/LICENSE).

