# Simple Guestbook Application
A guestbook application where visitors can leave messages

**Topics**: PHP, MySQL, AJAX, CSS, Guestbook, Web Development


## AMI LINUX 2023 - Requirements
```sh
sudo dnf upgrade -y
sudo dnf install -y httpd git php8.3 php8.3-fpm php8.3-pdo php8.3-mysqlnd mariadb105
sudo systemctl enable --now php-fpm httpd
```
```sh
cd ~
git clone https://github.com/mah-shamim/simple-guestbook-application.git
cd simple-guestbook-application
sudo mkdir -p /var/www/html/guestbook
sudo cp -r index.html *.php css js /var/www/html/guestbook/
```

### Installation Process

1. **Clone the Repository**:
   ```sh
   git clone https://github.com/yourusername/simple-guestbook-application.git
   cd simple-guestbook-application
   ```

2. **Database Setup**:
    - Create a new MySQL database.
    - Import the provided `guestbook.sql` file to set up the necessary table.
    - Update the database configuration in `config.php`.
    - Import the provided SQL file to set up the necessary tables.
     ```sh
     mysql -u yourusername -p todo_list < guestbook.sql
     mysql -h TU_ENDPOINT_RDS -P 3306 -u TU_USUARIO_RDS -p < guestbook.sql
     ```

4. **Configure the Database Connection:**
   - Open the `config.php` file and update the database credentials.
   - sudo nano /var/www/html/guestbook/config.php
     ```php
     <?php
     // config.php
     $servername = "localhost";
     $username = "yourusername";
     $password = "yourpassword";
     $dbname = "guestbook_db";
     ```
     ```sh
     sudo systemctl restart php-fpm
     sudo systemctl restart httpd
      ```

5. **Access the Application:r**
     ```sh
     http://EC2_PUBLIC_IP/guestbook/
     ```
**To save messages**, you still need to:

1. Configure the RDS endpoint, username, password, and database name in `/var/www/html/guestbook/config.php`.
2. Import `guestbook.sql` into RDS.
3. Allow inbound traffic on **TCP port 80 to EC2** from your IP address and on **TCP port 3306 to RDS** from the EC2 security group.


### File Structure

Here’s a basic file structure for your to-do list application:

```
simple-guestbook-application/
├── config.php
├── db.php
├── index.php
├── submit.php
├── fetch.php
├── css/
│   └── style.css
├── guestbook.sql
└── js/
    └── main.js
```
