# Big Data Architectures - Financial Investment Network
## Winter 2025 Term Project

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org)
[![Kafka](https://img.shields.io/badge/Apache%20Kafka-2.8+-orange.svg)](https://kafka.apache.org)
[![Spark](https://img.shields.io/badge/Apache%20Spark-3.0+-red.svg)](https://spark.apache.org)
[![MySQL](https://img.shields.io/badge/MySQL-8.0+-blue.svg)](https://www.mysql.com)

A distributed financial data processing system that simulates stock exchanges, institutional investors, and portfolio analytics using Kafka, Spark, and MySQL.

## 📋 Project Overview

This project implements a network of financial and investment services consisting of:
- **2 Stock Exchange Servers** - Simulate trading of 24 stocks with daily price emissions
- **3 Institutional Investors** - Manage 6 portfolios with real-time evaluation
- **Database Management** - MySQL storage for investor and portfolio data
- **Analytics Engine** - Spark-based statistical analysis and reporting

## 🏗️ System Architecture
┌─────────────────────┐    ┌─────────────────────┐
│  Stock Exchange 1   │    │  Stock Exchange 2   │
│   (se1_server.py)   │    │   (se2_server.py)   │
│   📈 Stocks 1-12    │    │   📈 Stocks 13-24   │
└──────────┬──────────┘    └──────────┬──────────┘
│                          │
└────────┬───────────────────┘
▼
┌───────────────────┐
│   Kafka Topic:    │
│  "StockExchange"  │
│   📡 Real-time    │
└─────────┬─────────┘
│
┌─────────────┼─────────────┐
▼             ▼             ▼
┌──────────────┐ ┌──────────────┐ ┌──────────────┐
│ Investor 1   │ │ Investor 2   │ │ Investor 3   │
│  (inv1.py)   │ │  (inv2.py)   │ │  (inv3.py)   │
│ 💼 P11 | P12 │ │ 💼 P21 | P22 │ │ 💼 P31 | P32 │
└──────┬───────┘ └──────┬───────┘ └──────┬───────┘
│                │                │
└────────────────┼────────────────┘
▼
┌───────────────────┐
│   Kafka Topic:    │
│   "portfolios"    │
│  💹 Evaluations   │
└─────────┬─────────┘
▼
┌───────────────┐
│  Kafka-DB     │
│  Bridge       │
│  (app1.py)    │
└───────┬───────┘
▼
┌─────────────────────┐
│    MySQL Database   │
│    "InvestorsDB"    │
│  🗄️ Persistent Data │
└─────────┬───────────┘
▼
┌─────────────────────┐
│  Spark Analytics    │
│     (app2.py)       │
│  📊 Statistical     │
│     Analysis        │
└─────────────────────┘

## 📁 Project Structure
big-data-financial-network/
├── 📄 README.md                      # Project documentation
├── 📄 .gitignore                     # Git ignore rules
├── 📄 requirements.txt               # Python dependencies
├── 📄 Team.txt                       # Team contributions
├── 📁 src/                           # Source code
│   ├── 📁 servers/
│   │   ├── 🐍 se1_server.py         # Stock Exchange Server 1
│   │   └── 🐍 se2_server.py         # Stock Exchange Server 2
│   ├── 📁 investors/
│   │   ├── 🐍 inv1.py               # Institutional Investor 1
│   │   ├── 🐍 inv2.py               # Institutional Investor 2
│   │   └── 🐍 inv3.py               # Institutional Investor 3
│   ├── 📁 database/
│   │   └── 🐍 investorsDB.py        # MySQL Database Setup
│   └── 📁 applications/
│       ├── 🐍 app1.py               # Kafka to Database Bridge
│       └── 🐍 app2.py               # Spark Analytics Engine
└── 📁 data/
└── 📁 output/                    # Generated statistics files

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- Apache Kafka 2.8+
- Apache Spark 3.0+
- MySQL 8.0+

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/big-data-financial-network.git
   cd big-data-financial-network

Install dependencies
bashpip install -r requirements.txt

Run the system
bash# Initialize database
python src/database/investorsDB.py

# Start stock exchange servers
python src/servers/se1_server.py &
python src/servers/se2_server.py &

# Start institutional investors
python src/investors/inv1.py &
python src/investors/inv2.py &
python src/investors/inv3.py &

# Start Kafka-Database bridge
python src/applications/app1.py &

# Run analytics
python src/applications/app2.py


💼 Portfolio Configuration
InvestorPortfolioHoldingsInv1P11IBM(1300), AAPL(2200), FB(1900), AMZN(2500), GOOG(1900), AVGO(2400)P12VZ(2900), INTC(2600), AMD(2100), MSFT(1200), DELL(2700), ORCL(1200)Inv2P21HPQ(1600), CSCO(1700), ZM(1900), QCOM(2100), ADBE(2800), VZ(1700)P22TXN(1400), CRM(2600), AVGO(1700), NVDA(1800), MSTR(2600), EBAY(1800)Inv3P31HPQ(2200), ZM(1800), DELL(2400), NVDA(1200), IBM(1900), INTC(1600)P32VZ(1800), AVGO(2900), NVDA(1600), AAPL(2200), DELL(2500), ORCL(2000)
📊 Key Features

Real-time Data Processing: Stock price simulation with Kafka streaming
Portfolio Management: Live evaluation and performance tracking
Analytics Engine: Spark-based statistical analysis
Database Integration: MySQL storage with comprehensive schema