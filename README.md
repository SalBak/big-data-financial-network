# Big Data Architectures - Financial Investment Network
## Summer 2025 Project

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

### Data Flow Overview

**📊 Stock Data Generation**
- `se1_server.py` → Generates prices for stocks 1-12
- `se2_server.py` → Generates prices for stocks 13-24
- Both servers publish to Kafka topic `"StockExchange"`

**💼 Portfolio Processing**
- `inv1.py` → Manages portfolios P11 & P12
- `inv2.py` → Manages portfolios P21 & P22  
- `inv3.py` → Manages portfolios P31 & P32
- All investors consume from `"StockExchange"` and publish to `"portfolios"`

**🗄️ Data Storage & Analytics**
- `app1.py` → Bridges Kafka to MySQL database
- `investorsDB.py` → Sets up MySQL database schema
- `app2.py` → Performs Spark analytics on stored data

### Component Interaction

1. **Stock Exchanges** emit daily prices → **Kafka Topic "StockExchange"**
2. **Institutional Investors** consume prices → Calculate portfolio values → **Kafka Topic "portfolios"**
3. **Database Bridge** consumes evaluations → **MySQL Database "InvestorsDB"**
4. **Analytics Engine** queries database → **Generate statistical reports**
