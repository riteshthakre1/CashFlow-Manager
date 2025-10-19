# 🏦  CashFlow Manager

A **complete, enterprise-grade banking management system** built with Java, JavaFX, and SQL. This application provides a professional, feature-rich GUI interface for managing all aspects of banking operations including customer management, account handling, money transfers, card management, loans, investments, employee management, and comprehensive reporting.

## 🚀 Complete Feature Set

### 💼 Core Banking Operations
- **💰 Account Balance Inquiry**: Real-time balance checking with detailed account information
- **💸 Money Transfer**: Secure transfer between accounts with transaction validation and history
- **👥 Customer Management**: Complete customer lifecycle management with personal information
- **📋 Transaction History**: Comprehensive logging and search of all banking transactions
- **💾 Data Persistence**: Robust SQLite database with automatic backup and recovery

### 💳 Advanced Banking Services
- **💳 Card Management**: Issue, manage, and track debit/credit cards with different networks
- **🏠 Loan Management**: Complete loan processing system with payment calculations
- **📈 Investment Portfolio**: Investment management with performance tracking
- **🏢 Branch Management**: Multi-office support with employee assignments
- **📊 Comprehensive Reporting**: Real-time analytics and financial reports

### 👔 Employee & Administration
- **👔 Employee Management**: Staff management with roles, departments, and permissions
- **🏢 Office Management**: Branch operations and manager assignments
- **📊 Performance Analytics**: Employee performance and branch statistics
- **🔐 Role-Based Access**: Different access levels for different user types

### 🎨 Modern User Interface
- **🎨 Modern GUI**: Beautiful, responsive JavaFX interface with professional styling
- **📱 Multi-Tab Interface**: Organized functionality across 9 specialized tabs
- **🎛️ Interactive Dashboard**: Real-time statistics and recent activity monitoring
- **⚡ Real-time Validation**: Instant input validation with visual feedback
- **🚨 Comprehensive Error Handling**: User-friendly error messages and alerts
- **🌙 Multiple Themes**: Light and dark theme support

### 🏗️ Technical Excellence
- **🏗️ MVC Architecture**: Clean separation of concerns with proper layering
- **🗄️ Advanced Database Design**: Comprehensive schema supporting all banking entities
- **🔧 Service Layer**: Well-structured business logic abstraction
- **📱 Responsive Design**: Adaptable layout for different screen sizes
- **🎯 FXML Support**: Declarative UI with programmatic fallback
- **🎨 Professional CSS**: Modern styling with animations and effects

## 📋 System Requirements

### Required Software
1. **Java Development Kit (JDK) 11 or higher**
   - Download: [Eclipse Temurin](https://adoptium.net/) or [Oracle JDK](https://www.oracle.com/java/technologies/downloads/)
   - Verify: `java -version`

2. **Apache Maven 3.6 or higher**
   - Download: [Apache Maven](https://maven.apache.org/download.cgi)
   - Verify: `mvn -version`

3. **JavaFX Runtime** (automatically managed via Maven)
   - Version 17.0.2 included in dependencies

### System Specifications
- **OS**: Windows 10/11, macOS 10.14+, or Linux
- **Memory**: Minimum 1GB RAM, 2GB+ recommended
- **Storage**: 200MB free disk space
- **Display**: 1024x768 minimum, 1400x900+ recommended

## 🛠️ Quick Start Guide

### 🚀 Method 1: One-Click Launch (Windows)
1. **Download/Clone** this repository
2. **Double-click** `run-banking-system.bat`
3. The launcher will automatically:
   - ✅ Verify Java and Maven installation
   - 📦 Download all dependencies
   - 🔨 Compile the entire project
   - 🚀 Launch the application with full GUI

### ⚡ Method 2: Command Line
```bash
# Clone and navigate
git clone <repository-url>
cd Bank

# Quick start
mvn clean javafx:run
```

### 📦 Method 3: Build Distribution
```bash
# Create executable JAR
mvn clean package

# Run standalone
java -jar target/Bank-1.0.0.jar
```

## 🎮 Application Features Guide

### 🏠 Dashboard Tab
- **📊 Real-time Statistics**: Customer count, account totals, transaction volume, total balance
- **📈 Recent Activities**: Latest transactions and system events
- **🎯 Quick Actions**: Sidebar with common operations
- **⚡ Live Updates**: Automatically refreshed data

### 👥 Customer Management Tab
- **➕ Add New Customers**: Complete registration with validation
- **📋 Customer Directory**: Searchable table of all customers
- **✏️ Customer Information**: Name, email, phone, address management
- **🔍 Quick Search**: Find customers instantly

### 🏦 Account Management Tab
- **💰 Account Overview**: All accounts with balances and types
- **🔍 Account Details**: Individual account information
- **📊 Account Statistics**: Performance and activity metrics
- **⚙️ Account Settings**: Type changes and configurations

### 💳 Card Management Tab
- **💳 Issue New Cards**: Debit, Credit, Prepaid cards
- **🌐 Multiple Networks**: Visa, MasterCard, American Express
- **📅 Expiry Tracking**: Automatic renewal notifications
- **🔒 Security Features**: CVV management and limits

### 🏠 Loan Management Tab
- **📋 Loan Applications**: Personal, Home, Car, Business, Education loans
- **💰 Payment Calculations**: Automatic payment schedules
- **📊 Loan Portfolio**: Outstanding balances and performance
- **📅 Payment Tracking**: History and upcoming payments

### 📈 Investment Management Tab
- **💼 Investment Portfolio**: Fixed deposits, stocks, bonds
- **📊 Performance Tracking**: Current values and gains/losses
- **💹 Investment Types**: Multiple investment instruments
- **📈 Growth Analytics**: ROI calculations and projections

### 📋 Transaction History Tab
- **🔍 Complete Transaction Log**: All system transactions
- **🔎 Advanced Search**: Filter by date, amount, type, accounts
- **📊 Transaction Analytics**: Volume and pattern analysis
- **📄 Export Options**: CSV and PDF export capabilities

### 👔 Employee Management Tab
- **👥 Staff Directory**: All bank employees with roles
- **🏢 Department Organization**: Organized by departments
- **💰 Salary Management**: Compensation tracking
- **📊 Performance Metrics**: Employee statistics

### 📊 Reports & Analytics Tab
- **📈 Financial Reports**: Comprehensive banking reports
- **📊 Custom Analytics**: Tailored business intelligence
- **📅 Periodic Reports**: Daily, weekly, monthly summaries
- **📄 Export Functions**: Professional report generation

## 🗄️ Complete Database Schema

### 👥 Customers Table
```sql
CREATE TABLE customers (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    first_name TEXT NOT NULL,
    last_name TEXT NOT NULL,
    email TEXT UNIQUE NOT NULL,
    phone TEXT,
    address TEXT,
    date_of_birth TEXT,
    ssn TEXT UNIQUE,
    created_date TEXT
);
```

### 🏦 Accounts Table
```sql
CREATE TABLE accounts (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    account_number TEXT UNIQUE NOT NULL,
    customer_id INTEGER,
    account_type TEXT NOT NULL,
    balance REAL DEFAULT 0.0,
    interest_rate REAL DEFAULT 0.0,
    minimum_balance REAL DEFAULT 0.0,
    status TEXT DEFAULT 'ACTIVE',
    created_date TEXT,
    FOREIGN KEY (customer_id) REFERENCES customers (id)
);
```

### 💳 Cards Table
```sql
CREATE TABLE cards (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    card_number TEXT UNIQUE NOT NULL,
    account_id INTEGER,
    card_type TEXT NOT NULL,
    network TEXT NOT NULL,
    holder_name TEXT NOT NULL,
    expiry_date TEXT,
    cvv TEXT,
    credit_limit REAL DEFAULT 0.0,
    status TEXT DEFAULT 'ACTIVE',
    issue_date TEXT,
    FOREIGN KEY (account_id) REFERENCES accounts (id)
);
```

### 🏠 Loans Table
```sql
CREATE TABLE loans (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    loan_number TEXT UNIQUE NOT NULL,
    customer_id INTEGER,
    loan_type TEXT NOT NULL,
    principal_amount REAL NOT NULL,
    interest_rate REAL NOT NULL,
    term_months INTEGER NOT NULL,
    monthly_payment REAL,
    outstanding_balance REAL,
    start_date TEXT,
    end_date TEXT,
    status TEXT DEFAULT 'ACTIVE',
    FOREIGN KEY (customer_id) REFERENCES customers (id)
);
```

### 📈 Investments Table
```sql
CREATE TABLE investments (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    investment_id TEXT UNIQUE NOT NULL,
    customer_id INTEGER,
    investment_type TEXT NOT NULL,
    amount REAL NOT NULL,
    current_value REAL,
    purchase_date TEXT,
    maturity_date TEXT,
    interest_rate REAL,
    status TEXT DEFAULT 'ACTIVE',
    FOREIGN KEY (customer_id) REFERENCES customers (id)
);
```

### 👔 Employees Table
```sql
CREATE TABLE employees (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    employee_id TEXT UNIQUE NOT NULL,
    first_name TEXT NOT NULL,
    last_name TEXT NOT NULL,
    email TEXT UNIQUE NOT NULL,
    role TEXT NOT NULL,
    salary REAL,
    department TEXT,
    manager_id INTEGER,
    hire_date TEXT,
    status TEXT DEFAULT 'ACTIVE'
);
```

### 🏢 Offices Table
```sql
CREATE TABLE offices (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    office_code TEXT UNIQUE NOT NULL,
    office_name TEXT NOT NULL,
    address TEXT,
    city TEXT,
    state TEXT,
    zip_code TEXT,
    phone TEXT,
    manager_id INTEGER,
    status TEXT DEFAULT 'ACTIVE',
    FOREIGN KEY (manager_id) REFERENCES employees (id)
);
```
