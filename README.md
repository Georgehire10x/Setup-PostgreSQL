Here’s a detailed description of each command, formatted so you can add it to your repository’s README file.

---

## **PostgreSQL Installation and Setup on Ubuntu**

This guide explains how to install PostgreSQL on Ubuntu, start the PostgreSQL server, create a new database and user, and check server status.

---

### **1. Install PostgreSQL on Ubuntu**
Run the following commands to install PostgreSQL:

```sh
sudo apt update
```
- This updates the list of available packages from Ubuntu’s package repository.

```sh
sudo apt install postgresql postgresql-contrib
```
- This installs PostgreSQL along with additional contributed modules that extend its functionality.

---

### **2. Start and Enable PostgreSQL Service**
To check if PostgreSQL is running:

```sh
sudo systemctl status postgresql
```
- Displays the status of the PostgreSQL service (running, stopped, or failed).

To start PostgreSQL manually:

```sh
sudo systemctl start postgresql
```
- Starts the PostgreSQL database server if it is not already running.

To enable PostgreSQL to start automatically on system boot:

```sh
sudo systemctl enable postgresql
```
- Ensures that PostgreSQL starts every time the server boots up.

---

### **3. Switch to the PostgreSQL User**
```sh
sudo -i -u postgres
```
- PostgreSQL creates a default system user called `postgres`.  
- This command switches to that user to manage PostgreSQL.

Now, to access the PostgreSQL interactive shell, run:

```sh
psql
```
- This opens the PostgreSQL command-line interface, where you can execute SQL commands.

---

### **4. Create a New Database**
Once inside the PostgreSQL shell, create a new database:

```sql
CREATE DATABASE mydatabase;
```
- This creates a new PostgreSQL database named `mydatabase`.

To verify that the database was created, list all databases:

```sql
\l
```
- Displays all available databases.

---

### **5. Create a New User and Grant Permissions**
To create a new user:

```sql
CREATE USER myuser WITH ENCRYPTED PASSWORD 'mypassword';
```
- Creates a new PostgreSQL user named `myuser` with the specified password.

Grant all privileges on the newly created database to the user:

```sql
GRANT ALL PRIVILEGES ON DATABASE mydatabase TO myuser;
```
- Gives the user `myuser` full access to the `mydatabase`.

---

### **6. Connect to the PostgreSQL Database**
Exit the PostgreSQL shell:

```sh
\q
```
- Quits the PostgreSQL interactive shell.

Now, connect to the database using the new user:

```sh
psql -U myuser -d mydatabase -h localhost -W
```
- `-U myuser` → Specifies the PostgreSQL username.
- `-d mydatabase` → Specifies the database to connect to.
- `-h localhost` → Connects to the PostgreSQL server running on the local machine.
- `-W` → Prompts for the password.

Enter the password when prompted.

---

### **7. Check Active Connections and Server Status**
To check whether the PostgreSQL server is running:

```sh
sudo systemctl status postgresql
```
- Shows the current status of the PostgreSQL service.

To see active connections to the database:

```sql
SELECT * FROM pg_stat_activity;
```
- Lists all currently active database connections.

---

This guide provides all necessary steps to install, configure, and manage a PostgreSQL database on Ubuntu. 🚀 Let me know if you need any modifications!
