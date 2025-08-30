# Atm-Simulator

An intuitive and fully functional **ATM Simulator** built with **Java Swing**. This project replicates the core banking functionalities of an Automated Teller Machine, including user authentication, balance enquiry, deposit, withdrawal, PIN change, and more. Designed with a step-by-step sign-up flow and image-enhanced GUI for an engaging experience.


## 🛠️ Features

- User Signup and Login (3-step form)
- Deposit and Withdraw money
- Fast cash withdrawal with fixed amounts
- Balance enquiry
- View mini statement (transaction history)
- PIN change functionality


## 📁 Project Structure

ATM-Simulator/

├── src/

│ ├── javacodes/

│ │ ├── Signup.java

│ │ ├── Signp2.java

│ │ ├── Signup3.java

│ │ ├── Login.java

│ │ ├── Deposit.java

│ │ ├── Withdrawal.java

│ │ ├── FastCash.java

│ │ ├── BalanceEnquiry.java

│ │ ├── MiniStatement.java

│ │ ├── PinChange.java

│ │ └── Transaction.java

│ └── images/

│ | ├── atmdashboard.jpg

│ | ├── atm.jpg

│ | └── logo.jpg

└── README.md



## 🛠️ Technologies Used

* **Java 8 or higher**
* **Java Swing** – for designing the graphical user interface (GUI)
* **AWT (Abstract Window Toolkit)** – for layout managers and event handling
* **JDBC (Java Database Connectivity)** – to connect Java with MySQL database
* **MySQL** – for storing user and transaction data
* **JCalendar Library** – used for date picking in forms
* **Eclipse IDE** – preferred development environment (can use IntelliJ or VS Code with Java extensions)



### ✅ Prerequisites

Make sure the following tools and files are set up before running the project:

* Java JDK 8 or above installed
* Eclipse IDE or compatible Java IDE (like IntelliJ or VS Code)
* MySQL Server installed
* MySQL Connector JAR (mysql-connector-j-9.1.0.jar) added to the project's build path
* JCalendar JAR (jcalendar.jar) added to the project’s build path
* Database named **bank management system** created in MySQL (with the required tables)



## How to Run the Project

1. **Open Eclipse IDE**

2. **Import Project:**

   * Go to `File → Import → Existing Projects into Workspace`
   * Select the folder where the project (`ATM-Simulator`) is located
3. **Configure Build Path:**

   * Right-click on the project → `Build Path → Configure Build Path`
   * Add External JARs:

     * `mysql-connector-j-9.1.0.jar`
     * `jcalendar-1.3.3.jar`


 4. **Setup Database**

    To store user credentials and transaction history, this project connects to a MySQL database using JDBC and follows a multi-step signup       process.

## 🔹 Step-by-Step Instructions:

    1. **Open MySQL Command Line Client**  or any GUI like MySQL Workbench or phpMyAdmin.

    2. **Create a new database:**

       ``` 
       CREATE DATABASE `bank management system`;
       USE `bank management system`;
       ```
    
    3. **Create the necessary tables:**
    
       ```
       -- Step 1: User account creation (Signup.java)
       CREATE TABLE signup (
           form_no VARCHAR(20) PRIMARY KEY,
           name VARCHAR(100),
           fname VARCHAR(100),
           dob DATE,
           gender VARCHAR(10),
           email VARCHAR(100),
           marital_status VARCHAR(20),
           address VARCHAR(255),
           city VARCHAR(100),
           state VARCHAR(100),
           pin_code VARCHAR(10)
       );
    
       -- Step 2: Additional details (Signup2.java)
       CREATE TABLE signup2 (
           form_no VARCHAR(20),
           religion VARCHAR(50),
           category VARCHAR(50),
           income VARCHAR(50),
           education VARCHAR(100),
           occupation VARCHAR(50),
           pan_no VARCHAR(20),
           aadhar_no VARCHAR(20),
           senior_citizen VARCHAR(5),
           existing_account VARCHAR(5),
           FOREIGN KEY (form_no) REFERENCES signup(form_no)
       );
    
       -- Step 3: Account creation (Signup3.java)
       CREATE TABLE signup3 (
           form_no VARCHAR(20),
           account_type VARCHAR(50),
           card_no VARCHAR(20),
           pin VARCHAR(10),
           services TEXT,
           FOREIGN KEY (form_no) REFERENCES signup(form_no)
       );
    
       -- Login credentials (Login.java)
       CREATE TABLE login (
           card_no VARCHAR(20) PRIMARY KEY,
           pin VARCHAR(10)
       );
    
       -- Transactions
       CREATE TABLE transactions (
           transaction_id INT AUTO_INCREMENT PRIMARY KEY,
           card_no VARCHAR(20),
           type VARCHAR(20), -- 'Deposit', 'Withdrawal', 'Balance Check'
           amount DECIMAL(10,2),
           date_time DATETIME DEFAULT CURRENT_TIMESTAMP,
           FOREIGN KEY (card_no) REFERENCES login(card_no)
       );
       ```
    
    4. **Configure JDBC Connection in Java Code:**
    
       Update the database connection string in your Java files:
    
       ```
       String url = "jdbc:mysql://localhost:3306/bank management system";
       String user = "root";
       String password = "your_mysql_password";
       ```
    
       > Replace `"your_mysql_password"` with your actual MySQL password.
    
    5. **Add JDBC Driver to Your Project:**
    
       * Download the MySQL JDBC driver `.jar` file 
       * In Eclipse:
         Right-click on your project → **Build Path** → **Configure Build Path** → **Libraries** → **Add External JARs** → Select the                  downloaded `.jar`.
  
5. **Run the Project:**

   * Start with the file: `Signup.java` (for new users) or `Login.java` (if credentials exist)
   * You can also test transaction screens like `Deposit.java`, `Withdrawl.java`, `BalanceEnquiry.java`, etc.
6. **Use the GUI:**

   * Perform banking operations via the ATM-style interface.



## 📚 Functional Flow

    A[Signup Page 1] --> B[Signup Page 2];
    B --> C[Signup Page 3];
    C --> D[Login Page];
    D --> E[Transaction Menu];
    E --> F[Deposit];
    E --> G[Withdraw];
    E --> H[Fast Cash];
    E --> I[PIN Change];
    E --> J[Balance Enquiry];
    E --> K[Mini Statement];
