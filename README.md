
# LAMP Stack E-Commerce App Deployment (KodeKloud Lab)

This repository documents my hands-on deployment of a **PHP-based E-Commerce web application** on a **LAMP stack** (Linux, Apache, MariaDB, PHP) using a CentOS-based virtual server provided by KodeKloud.

The objective of this lab was to set up a complete web application environment by installing and configuring:
- Apache Web Server  
- PHP & required extensions  
- MariaDB Database Server  
- Application code deployment using Git  
- Database connectivity setup  
- Troubleshooting & verification  

This repository contains:
- Commands used during the deployment  
- Personal notes & learnings  
- Screenshots of the working setup  
- Final application output  

---

## 🏗 **Architecture Overview**

```

Linux Server (CentOS Stream)
│
├── Apache (httpd)
│        └── Serves PHP application
│
├── PHP 8.x
│        └── Processes backend logic
│
└── MariaDB 10.x
└── Stores product data for the app

```

---

## 📂 **Repository Structure**

```

lamp-ecommerce-lab/
│── README.md
│── commands-used.txt
│── notes.md
│── screenshots/
│     ├── Screenshot_2025-11-25_143652.png
│     ├── Screenshot_2025-11-25_144428.png
│     ├── Screenshot_2025-11-25_144725.png
│     ├── Screenshot_2025-11-25_145252.png
│     ├── Screenshot_2025-11-25_145557.png
│     └── Screenshot_2025-11-25_145625.png

````

---

## 🚀 **Steps Performed in the Lab**

### **1. Installed MariaDB Server**
```bash
sudo yum install -y mariadb-server
sudo systemctl start mariadb
sudo systemctl enable mariadb
````

### **2. Configured Database**

```sql
CREATE DATABASE ecomdb;
CREATE USER 'ecomuser'@'localhost' IDENTIFIED BY 'ecompassword';
GRANT ALL PRIVILEGES ON *.* TO 'ecomuser'@'localhost';
FLUSH PRIVILEGES;
```

---

### **3. Installed Apache, PHP & Extensions**

```bash
sudo yum install -y httpd php php-mysqlnd
sudo systemctl start httpd
sudo systemctl enable httpd
```

---

### **4. Deployed the Application Code**

```bash
sudo git clone https://github.com/kodekloudhub/learning-app-ecommerce.git /var/www/html
```

---

### **5. Updated Database Connection in `index.php`**

The application was originally configured to use an external DB IP (`172.20.1.101`).
Since web and DB run on the same server, the IP was changed to `localhost`:

```bash
sudo sed -i 's/172.20.1.101/localhost/g' /var/www/html/index.php
```

---

### **6. Restarted Apache**

```bash
sudo systemctl restart httpd
```

---

## 🌐 **Final Output**

After setup, accessing the application in the browser (port 80) displayed:

* Home page
* Product listings
* Working UI rendered by PHP
* Successful DB connection

Screenshot of the final running app is included in `/screenshots`.

---

## 📸 **Screenshots**

All screenshots of installation, configuration, and final UI are located in the **screenshots** folder.

---

## 📘 **Learnings & Outcomes**

Through this lab, I gained practical experience in:

✔ Installing & configuring a full LAMP stack
✔ Managing Linux services using `systemctl`
✔ Database creation & user privilege management
✔ PHP-to-MariaDB connectivity
✔ Deploying code using Git
✔ Editing server configuration files
✔ Using tools like `sed`, `vi`, and `/var/www` structure
✔ Understanding how web servers serve dynamic PHP content

This project strengthens my foundation in **Linux administration**, **server setup**, and **DevOps fundamentals**.



## 🏁 **Conclusion**

This hands-on implementation provided real-world exposure to setting up a complete web application environment using the LAMP stack.
It demonstrates practical skills relevant for **Cloud**, **DevOps**, and **System Administration** roles.

