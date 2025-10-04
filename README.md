# Database Table Operations Lab

### **Overview**
This hands-on AWS lab demonstrates how to use **MySQL database commands** to create, view, modify, and delete databases and tables.  
The lab runs in an **Amazon EC2 Command Host** instance configured to connect to a **MySQL RDS instance**.

---

### **Learning Objectives**
After completing this lab, I was able to:
- Use the **CREATE** statement to create databases and tables  
- Use the **SHOW** statement to view databases and tables  
- Use the **ALTER** statement to modify a table schema  
- Use the **DROP** statement to delete databases and tables  


---

### **Architecture**
<img width="600" height="600" alt="9fb1ace7-a9a0-4f9d-9487-23672e47b92a" src="https://github.com/user-attachments/assets/531b4b8c-4c3b-4560-a9fb-6a8a59074f00" />

## **Architecture Summary:**
- A **Command Host (EC2 instance)** is provisioned with MySQL client tools.  
- A **MySQL Database Instance** hosts the `world` database.  
- The lab user connects through **Session Manager** to execute SQL commands directly from the terminal.  

---

### **Commands and Steps**

```bash
sudo su
cd /home/ec2-user/
mysql -u root --password='re:St@rt!9'
# Step 1: Connect to the MySQL database
sudo su
cd /home/ec2-user/
mysql -u root --password='re:St@rt!9'

# Step 2: View existing databases
SHOW DATABASES;

# Step 3: Create a new database and verify
CREATE DATABASE world;
SHOW DATABASES;

# Step 4: Create the "country" table
CREATE TABLE world.country (
  Code CHAR(3) NOT NULL,
  Name CHAR(52) NOT NULL,
  Conitinent ENUM('Asia','Europe','North America','Africa','Oceania','Antarctica','South America') NOT NULL,
  Region CHAR(26) NOT NULL,
  Population INT(11) NOT NULL,
  PRIMARY KEY (Code)
);

# Step 5: Verify table creation
USE world;
SHOW TABLES;
SHOW COLUMNS FROM world.country;

# Step 6: Correct the column name
ALTER TABLE world.country RENAME COLUMN Conitinent TO Continent;
SHOW COLUMNS FROM world.country;

# Step 7: Challenge – Create another table
CREATE TABLE world.city (
  Name CHAR(35),
  Region CHAR(26)
);

# Step 8: Delete tables and database
DROP TABLE world.city;
DROP TABLE world.country;
DROP DATABASE world;
```
---
### **Screenshoot**
**01_show_databases.png**  
<img width="737" height="500" alt="Screenshot 2025-10-03 125846" src="https://github.com/user-attachments/assets/614eb1a3-7dc9-497e-98dc-a48b6a901c7b" />

**02_create_database.png**

<img width="428" height="251" alt="Screenshot 2025-10-04 055507" src="https://github.com/user-attachments/assets/3b587861-3f24-4e02-addd-2e78e4b04a7a" />

**03_create_table.png** 
<img width="1302" height="366" alt="Screenshot 2025-10-04 055531" src="https://github.com/user-attachments/assets/fed24073-7e97-419c-8b54-a943154ee0a2" />


**04_show_columns.png**
<img width="1392" height="410" alt="Screenshot 2025-10-04 055606" src="https://github.com/user-attachments/assets/446b2b29-c006-4500-a280-4c0b33edb8f1" />


**05_alter_table.png** 
<img width="1409" height="480" alt="Screenshot 2025-10-04 055633" src="https://github.com/user-attachments/assets/00709fc3-4f36-4ece-bed5-58b489c75f3a" />


**06_drop_table.png** 
<img width="1006" height="147" alt="Screenshot 2025-10-04 055702" src="https://github.com/user-attachments/assets/de434262-cbf7-47ef-9d9e-ee982ef64b2a" />


**07_drop_database.png**  
<img width="1092" height="237" alt="Screenshot 2025-10-04 055735" src="https://github.com/user-attachments/assets/3fac8267-af2f-4073-935b-7a11e7a56ab7" />

---

## **Tools Used**
Amazon EC2 (Command Host)

Amazon RDS (MySQL)

AWS Systems Manager Session Manager

MySQL Command Line Interface

---
### **Key Takeaways**
Practiced essential SQL DDL commands

Understood AWS database workflow (EC2 → RDS → MySQL)

Learned how to manage databases securely in the cloud

---
### **Author**
Amarachi Emeziem

Cloud Security & IT Support Specialist | AWS & Azure Certified

LinkedIn  • GitHub
