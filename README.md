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
graph TD
    SE1[Stock Exchange Server 1<br/>se1_server.py<br/>Stocks 1-12] 
    SE2[Stock Exchange Server 2<br/>se2_server.py<br/>Stocks 13-24]
    
    KT1[Kafka Topic<br/>"StockExchange"]
    
    INV1[Investor 1<br/>inv1.py<br/>P11 | P12]
    INV2[Investor 2<br/>inv2.py<br/>P21 | P22]
    INV3[Investor 3<br/>inv3.py<br/>P31 | P32]
    
    KT2[Kafka Topic<br/>"portfolios"]
    
    DB[MySQL Database<br/>"InvestorsDB"]
    APP1[Kafka-DB Bridge<br/>app1.py]
    APP2[Spark Analytics<br/>app2.py]
    
    SE1 --> KT1
    SE2 --> KT1
    
    KT1 --> INV1
    KT1 --> INV2
    KT1 --> INV3
    
    INV1 --> KT2
    INV2 --> KT2
    INV3 --> KT2
    
    KT2 --> APP1
    APP1 --> DB
    DB --> APP2
    
    style SE1 fill:#e1f5fe
    style SE2 fill:#e1f5fe
    style KT1 fill:#fff3e0
    style KT2 fill:#fff3e0
    style INV1 fill:#e8f5e8
    style INV2 fill:#e8f5e8
    style INV3 fill:#e8f5e8
    style DB fill:#fce4ec
    style APP1 fill:#f3e5f5
    style APP2 fill:#f3e5f5

## 📁 Project Structure

big-data-financial-network/
├── src/
│   ├── servers/
│   │   ├── se1_server.py          # Stock Exchange Server 1
│   │   └── se2_server.py          # Stock Exchange Server 2
│   ├── investors/
│   │   ├── inv1.py                # Institutional Investor 1
│   │   ├── inv2.py                # Institutional Investor 2
│   │   └── inv3.py                # Institutional Investor 3
│   ├── database/
│   │   └── investorsDB.py         # MySQL Database Setup
│   └── applications/
│       ├── app1.py                # Kafka to Database Bridge
│       └── app2.py                # Spark Analytics Engine
├── data/
│   └── output/                    # Generated statistics files
├── README.md                      # This file
├── requirements.txt               # Python dependencies
├── Team.txt                       # Team contribution details
└── .gitignore                     # Git ignore rules


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

Run the system

Start Kafka and MySQL services
Initialize database: python src/database/investorsDB.py
Start servers: python src/servers/se1_server.py and python src/servers/se2_server.py
Start investors: python src/investors/inv1.py, python src/investors/inv2.py, python src/investors/inv3.py
Start bridge: python src/applications/app1.py
Run analytics: python src/applications/app2.py

Investor 1 (inv1)

P11: IBM(1300), AAPL(2200), FB(1900), AMZN(2500), GOOG(1900), AVGO(2400)
P12: VZ(2900), INTC(2600), AMD(2100), MSFT(1200), DELL(2700), ORCL(1200)

Investor 2 (inv2)

P21: HPQ(1600), CSCO(1700), ZM(1900), QCOM(2100), ADBE(2800), VZ(1700)
P22: TXN(1400), CRM(2600), AVGO(1700), NVDA(1800), MSTR(2600), EBAY(1800)

Investor 3 (inv3)

P31: HPQ(2200), ZM(1800), DELL(2400), NVDA(1200), IBM(1900), INTC(1600)
P32: VZ(1800), AVGO(2900), NVDA(1600), AAPL(2200), DELL(2500), ORCL(2000)

📊 Features

Real-time Data: Stock price simulation from 2000-01-01
Portfolio Management: Live evaluation and performance tracking
Analytics: Historical analysis, yearly breakdowns, statistical insights
Database Integration: MySQL storage with comprehensive schema

📄 License
This project is created for academic purposes as part of the Big Data Architectures course, Winter 2025.
