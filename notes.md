# Notes – LAMP E-Commerce Application Deployment

These are my personal notes taken during the KodeKloud LAMP stack lab.

---

## ✔ MariaDB Setup Notes

- MariaDB installation required enabling appstream/baseos repos.
- After starting the DB service, I logged into MariaDB without a password.
- Created `ecomdb` and `ecomuser` with full privileges for simplicity.
- `FLUSH PRIVILEGES` ensures cached permissions refresh.

---

## ✔ Apache + PHP Notes

- Installed `httpd`, `php`, and `php-mysqlnd` to allow PHP to connect to MariaDB.
- Enabled and verified Apache using systemctl.
- Apache serves files from `/var/www/html`.

---

## ✔ Application Deployment Notes

- The e-commerce code was cloned from a public GitHub repo.
- The database IP inside `index.php` pointed to `172.20.1.101`.
- Since DB and web server are on same VM, changed it to `localhost`.
- Used:
sudo sed -i 's/172.20.1.101/localhost/g' /var/www/html/index.php

markdown
Copy code
- This fixed the database connection issue.

---

## ✔ Troubleshooting Notes

- Incorrect filename (`index.html`) caused `sed` error.
- Verified correct file `index.php` existed.
- Running `sudo systemctl status httpd` helps confirm Apache issues.
- If application doesn't load, check:
- Firewall
- SELinux
- Apache logs (`/var/log/httpd/error_log`)

---

## ✔ Final Notes

- Successfully accessed website at port 80.
- The UI displayed the product list confirming database connectivity.
- This lab improved understanding of:
- LAMP stack
- Linux services
- PHP + MariaDB integration
- Git-based web deployment

