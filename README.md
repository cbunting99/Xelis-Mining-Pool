# Xelis Mining Pool

## Overview
Welcome to the **XelisHashV2 Mining Pool**, a commercial-grade mining pool with advanced features designed for the Xelis blockchain. This pool supports the XelisHashV2 algorithm and offers robust functionality for both miners and administrators, including various payout options, dynamic difficulty adjustment, and real-time monitoring.

---

## Features

### **Core Functionality**
1. **Mining Protocol**
   - Fully supports **XelisHashV2**.
   - Handles mining requests (jobs) and receives submitted shares from miners.
   - Implements multiple payout systems, including:
     - **FPPS (Full Pay-Per-Share)**.
     - **PPS (Pay-Per-Share)**.
     - **PPLNS (Pay-Per-Last-N-Shares)**.
     - **Solo mining payouts** for independent miners.

2. **Backend (Flask)**
   - Provides API endpoints for:
     - **Pool Stats:** Total hashrate, active workers, and total submitted shares.
     - **Worker Stats:** Individual miner hashrate, shares submitted, and payout details.
     - **Payout Processing:** Automates payouts based on the selected payout system.
   - Database-driven logic (SQLite for now) for share tracking, payouts, and worker management.

3. **Frontend (React)**
   - Dashboard displaying:
     - **Pool Statistics:** Real-time total hashrate, worker count, and block statuses.
     - **Worker Statistics:** Individual worker performance (shares, last activity).
     - **Payout Records:** History of payouts for transparency.

---

### **Implemented Features**

#### **1. Secure Communication**
   - **SSL/TLS Encryption**: Ensures secure communication between miners and the pool using Flask's `ssl_context`.

#### **2. Dynamic Difficulty Adjustment**
   - Automatically adjusts the mining difficulty for each worker based on their hashrate, ensuring an optimal number of shares submitted over time.

#### **3. Multiple Payout Systems**
   - Pool owners can configure the desired payout system via the config file. Available options:
     - **FPPS:** Miners are paid for each valid share submitted, factoring in pool rewards.
     - **PPS:** Simple pay-per-share model without considering pool luck or block rewards.
     - **PPLNS:** Rewards miners based on their contribution to the last `N` shares.
     - **Solo:** Entire block reward is given to the miner who solves the block.

#### **4. Advanced Share Management**
   - **Validation for Duplicate and Invalid Shares:** Ensures shares are unique and meet the target difficulty.
   - **Real-Time Tracking:** Tracks shares with timestamps for performance monitoring.
   - **Rejection Feedback:** Logs invalid or duplicate shares with specific reasons for rejection.

#### **5. Database-Driven Architecture**
   - **SQLite** database to store:
     - Worker data (IDs, shares submitted, last seen time).
     - Payout records (amount, worker ID, timestamp).
     - Valid and rejected shares.
   - Easily migratable to more robust databases like MySQL or PostgreSQL for production.

#### **6. Monitoring and Metrics**
   - Integration with **Prometheus** for real-time monitoring of system metrics, including:
     - Pool hashrate.
     - Backend API performance.
     - Worker activity.

#### **7. Security Features**
   - Worker authentication with unique tokens.
   - **Rate limiting** to prevent abuse or malicious activity (e.g., excessive API calls).

#### **8. Logging and Transparency**
   - Logs worker activity (shares submitted, accepted, or rejected).
   - Tracks payouts for audit purposes.

#### **9. User-Friendly Dashboard**
   - A React-based dashboard with components for:
     - **Pool Stats:** High-level overview of the pool's performance.
     - **Worker Stats:** Per-worker breakdown of shares, hashrate, and payouts.
     - **Payout History:** Transparent record of payouts made by the pool.

---

## Planned and In-Progress Features

### **1. Enhanced User and Worker Management**
   - **User Registration:** Add user accounts for better tracking of multiple workers.
   - **Worker Groups:** Allow grouping of workers under a single account for ease of management.

### **2. Advanced Pool Features**
   - **Referral Program:** Reward miners for bringing new workers to the pool.
   - **Bonus Payouts:** Periodic bonus rewards for top-performing miners.

### **3. Commercial Features**
   - **Customizable Fees:** Allow the pool owner to configure different fees for miners based on their hashrate or loyalty.
   - **Alerts and Notifications:** Notify miners about payouts, activity, or performance drops via email or SMS.

### **4. High Availability**
   - **Load Balancing:** Distribute worker connections across multiple servers.
   - **Failover:** Automatically reroute miners to backup servers in case of downtime.

---

## Additional Features To Be Added

1. **Mobile-Friendly Dashboard**
   - Responsive design for miners to monitor their stats on mobile devices.

2. **Advanced Analytics**
   - Charts for hashrate trends, share submissions, and payout history over time.

3. **Multi-Currency Support**
   - Support mining and payouts in multiple cryptocurrencies, making the pool more versatile.

4. **Payment Gateway Integration**
   - Allow miners to receive payments directly to wallets or via payment gateways (e.g., PayPal or Stripe).

5. **Admin Panel**
   - Backend dashboard for the pool owner to:
     - Monitor pool health.
     - Approve payouts manually (if needed).
     - Manage users and workers.

---

## Project Roadmap

| **Feature**                     | **Status**        |
|----------------------------------|-------------------|
| XelisHashV2 Stratum Protocol     | ✅ Implemented    |
| FPPS, PPS, PPLNS, Solo Payouts   | ✅ Implemented    |
| Secure Communication (SSL)       | ✅ Implemented    |
| Dynamic Difficulty Adjustment    | ✅ Implemented    |
| React Dashboard                  | ✅ Basic Version  |
| Monitoring with Prometheus       | ✅ Implemented    |
| Worker Authentication            | ✅ Implemented    |
| Database (SQLite)                | ✅ Implemented    |
| Advanced Share Validation        | ✅ Implemented    |
| User Registration/Accounts       | 🔄 In Progress    |
| Referral Program                 | 🔄 Planned        |
| Bonus Payouts                    | 🔄 Planned        |
| Mobile-Friendly Dashboard        | 🔄 Planned        |
| Admin Panel                      | 🔄 Planned        |
| High Availability (Failover)     | 🔄 Planned        |

---

## Getting Started

### **1. Backend Setup**
1. Install Python 3.8+.
2. Create a virtual environment and activate it:
   ```bash
   python -m venv env
   source env/bin/activate  # Linux/Mac
   env\Scripts\activate     # Windows
   ```
3. Install dependencies:
   ```bash
   pip install -r backend/requirements.txt
   ```
4. Run the backend server:
   ```bash
   python api.py
   ```

### **2. Frontend Setup**
1. Install Node.js and npm ([download here](https://nodejs.org)).
2. Navigate to the `dashboard/` folder and install dependencies:
   ```bash
   cd dashboard
   npm install
   ```
3. Start the React frontend:
   ```bash
   npm start
   ```

### **3. Database Initialization**
Run the database initialization script (included in `database.py`) to set up the SQLite database.

---

## Contributing
Contributions are welcome! Please submit a pull request or open an issue for feature suggestions or bug fixes.

---

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

