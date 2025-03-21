# Installing MySQL on Ubuntu

Follow these steps to install MySQL on an Ubuntu system:

1. **Update Package Index:**
    - Open a terminal.
    - Run the command:
      ```sh
      sudo apt update
      ```
      This updates the package index to ensure you get the latest version of MySQL.

2. **Install MySQL Server:**
    - Run the command:
      ```sh
      sudo apt install mysql-server
      ```
      This installs the MySQL server package on your system.

3. **Start MySQL Service:**
    - Run the command:
      ```sh
      sudo systemctl start mysql
      ```
      This starts the MySQL service.
    - Optionally, run:
      ```sh
      sudo systemctl enable mysql
      ```
      This enables MySQL to start automatically at boot.

4. **Verify MySQL Installation:**
    - Run the command:
      ```sh
      sudo systemctl status mysql
      ```
      This checks the status of the MySQL service. You should see a message indicating that MySQL is active and running.

5. **Secure MySQL Installation:**
    - Run the command:
      ```sh
      sudo mysql_secure_installation
      ```
      This script helps you improve the security of your MySQL installation. Follow the prompts to set the root password, remove anonymous users, disallow root login remotely, remove test databases, and reload privilege tables.

6. **Access MySQL:**
    - Run the command:
      ```sh
      sudo mysql
      ```
      This opens the MySQL shell as the root user. You can now start creating databases and users.

You have successfully installed MySQL on your Ubuntu system.

## Creating a MySQL User with a Password

To create a new MySQL user with the username `root` and password `Test@123`, follow these steps:

1. **Create a New User:**
    - In the MySQL shell, run the following command:
      ```sql
      ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'Test@123';
      ```
      This creates a new user `root` with the password `Test@123`.

2. **Grant Privileges to the User:**
    - Run the command:
      ```sql
      GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' WITH GRANT OPTION;
      ```
      This grants all privileges to the user `root` on all databases and tables.

3. **Flush Privileges:**
    - Run the command:
      ```sql
      FLUSH PRIVILEGES;
      ```
      This reloads the privilege tables to ensure that the changes take effect.

4. **Exit MySQL Shell:**
    - Run the command:
      ```sql
      EXIT;
      ```
      This exits the MySQL shell.

You have successfully created a MySQL user with the username `root` and password `Test@123`.


## Trivy Installation Steps

sudo apt-get install wget apt-transport-https gnupg lsb-release

wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -

echo deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main | sudo tee -a /etc/apt/sources.list.d/trivy.list

sudo apt-get update -y

sudo apt-get install trivy -y

## To install json 
sudo apt-get install jq -y

## trivy Commands

trivy image imagename

trivy fs --security-checks vuln --severity HIGH,CRITICAL Folder_name_OR_Path

trivy image --severity HIGH,CRITICAL image_name    

you can use --severity (LOW,MEDIUM,HIGH,CRITICAL) 

trivy image -f json -o results.json image_name

trivy repo repo-url

trivy k8s --report summary cluster


example
```bash
trivy fs --security-checks vuln --severity HIGH,CRITICAL Folder_name_OR_Path
trivy image --security-checks vuln --severity HIGH,CRITICAL -f table -o Image_Scan.html image_name
```