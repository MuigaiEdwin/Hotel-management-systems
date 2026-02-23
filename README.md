# 🏨 NEGAD GRILL - Hotel Management System

![AWS EC2](https://img.shields.io/badge/Hosted%20on-AWS%20EC2-orange?logo=amazon-aws)
![PHP](https://img.shields.io/badge/Backend-PHP-blue?logo=php)
![MySQL](https://img.shields.io/badge/Database-MariaDB-blue?logo=mariadb)
![HTML CSS JS](https://img.shields.io/badge/Frontend-HTML%20%7C%20CSS%20%7C%20JS-green)

A full-stack web-based hotel dining management system that streamlines the dining experience from table booking to payment processing — deployed live on AWS EC2.

🌐 **Live Demo:** http://13.49.68.168/hotel/homepage/display.html

---

## 📝 Project Overview

NEGAD GRILL is a comprehensive restaurant management solution that handles the complete dining workflow — from customer registration and table reservations to kitchen order management and payment processing.

---

## 🔧 Features

| Feature | Description |
|---|---|
| 🔐 Authentication | User registration & secure login |
| 📞 Table Booking | Customers can browse and reserve tables online |
| 🍽️ Order Management | Interactive menu with real-time order submission |
| 🍲 Kitchen Dashboard | Chefs receive and manage incoming orders |
| 🤖 Waiter Interface | Waiters track order preparation and table service |
| 💳 Payment Processing | Card and M-Pesa payment support with digital receipts |
| 📊 Admin Dashboard | Full overview of tables, orders, customers and stats |
| 📈 Reports & Analytics | Daily sales, peak hours, and profit/loss reports |

---

## 🎨 Technology Stack

### Frontend
- HTML5
- CSS3
- JavaScript (Vanilla)

### Backend
- PHP

### Database
- MariaDB / MySQL

### Hosting
- AWS EC2 (Amazon Linux 2023)
- Apache HTTP Server

---

## 🗄️ Database Schema

```sql
-- User Authentication
registration (id, firstName, lastName, gender, email, password, number)

-- Table Management
restaurant_tables (table_id, table_number, table_name, capacity, status, last_updated)

-- Customer Records
customers (customer_id, first_name, last_name, phone_number, created_at)

-- Orders
orders (order_id, table_number, total_amount, payment_status, created_at)
order_items (id, order_id, item_id, item_name, quantity, price, total)
menu_items (item_id, name, price)

-- Payments
payments (payment_id, order_id, payment_method, amount, transaction_id, payment_date)
```

---

## ⚡ Setup Instructions

### Local Setup (XAMPP)

1. Install [XAMPP](https://www.apachefriends.org/)
2. Clone the repository:
```bash
git clone https://github.com/MuigaiEdwin/Hotel-management-systems.git
```
3. Move project to `htdocs/`:
```bash
mv Hotel-management-systems/ /xampp/htdocs/hotel/
```
4. Start Apache and MySQL in XAMPP
5. Import database via phpMyAdmin
6. Update `connect.php` with your credentials
7. Visit: `http://localhost/hotel/Login.html`

---

### AWS EC2 Deployment

1. **Launch EC2 Instance**
   - OS: Amazon Linux 2023
   - Instance Type: t3.micro (Free Tier)
   - Open ports: 22, 80, 443

2. **Connect via SSH**
```bash
ssh -i your-key.pem ec2-user@YOUR_EC2_IP
```

3. **Install Stack**
```bash
sudo dnf update -y
sudo dnf install httpd php php-mysqli mariadb105-server -y
sudo systemctl start httpd mariadb
sudo systemctl enable httpd mariadb
```

4. **Secure MySQL**
```bash
sudo mysql_secure_installation
```

5. **Create Database**
```sql
CREATE DATABASE test;
CREATE USER 'hoteluser'@'localhost' IDENTIFIED BY 'yourpassword';
GRANT ALL PRIVILEGES ON test.* TO 'hoteluser'@'localhost';
```

6. **Upload Files**
```bash
scp -i your-key.pem -r ./hotel/* ec2-user@YOUR_EC2_IP:/tmp/hotel/
sudo mv /tmp/hotel /var/www/html/hotel
sudo chown -R apache:apache /var/www/html/hotel
sudo chcon -R -t httpd_sys_rw_content_t /var/www/html/hotel/
```

7. **Update connect.php** with your DB credentials

8. Visit: `http://YOUR_EC2_IP/hotel/Login.html`

---

## 📁 Project Structure

```
hotel/
├── Login.html              # Entry point
├── register.html           # User registration
├── connect.php             # Registration DB handler
├── logincheckup.php        # Login authentication
├── dashboard.html          # Admin dashboard
├── DETAILSENTRY.html       # Table booking form
├── kitchen_dashboard.html  # Kitchen order view
├── order_history.html      # Order history
├── homepage/               # Public landing page
├── Menu/                   # Menu & order processing
├── Tables/                 # Table reservation UI
├── photos/                 # Food images
└── reports.html            # Sales reports
```

---

## 🛡️ Admin Credentials (Demo)

Register at `/hotel/register.html` to create your admin account.

---

## 💡 Future Enhancements

- [ ] Mobile responsive design
- [ ] Real M-Pesa API integration (Daraja)
- [ ] SMS notifications via Africa's Talking
- [ ] Advanced analytics dashboard
- [ ] Docker containerization
- [ ] CI/CD pipeline with GitHub Actions

---

## 👨‍💻 Developer

**Edwin Muigai ($cripted)**
- 🌐 Portfolio: [muigaiedwin-portfolio.s3-website.eu-north-1.amazonaws.com](http://muigaiedwin-portfolio.s3-website.eu-north-1.amazonaws.com)
- 💼 LinkedIn: [linkedin.com/in/muigaiedwin](https://linkedin.com/in/muigaiedwin)
- 🐙 GitHub: [github.com/MuigaiEdwin](https://github.com/MuigaiEdwin)

---

## 📄 License

This project is for educational purposes. Original system by [elly-coder](https://github.com/elly-coder), deployed and enhanced by Edwin Muigai.