# Data-Warehouse-API-setup-Manual
## A step-by-step guide on how to set up the DWAPI in health facilities

## 1. Update the software repository

```
sudo apt update
```

## 2. Download dependencies

```
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
```

The above command does the following:

* Gives the package manager permission to transfer files and data over https.

* Allows the system to check security certificates.

* Installs curl, a a tool for transferring data.

* Adds scripts for managing software.

## 3. Add Docker's GPG Key

### Next, add the GPG key to ensure the authenticity of the software package.

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

## 4. Installing the Docker Repository

### Now install the Docker repository using the command:

```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

## 5. Installing the Latest Docker

### Start by updating the repository again

```
sudo apt update
```

### Now you can install the latest Docker version with:

```
sudo apt-get install docker-ce
```

## 6. Verifying Docker Installation.

### To confirm the installation check the version of Docker:

```
docker --version
```

## 7. Enable Docker Service

### To start the Docker service run the following command:

```
sudo systemctl start docker
```

### Enable Docker to run at startup with:

```
sudo systemctl enable docker
```

# DWAPI setup

## a) New installation

### 1. Install DWAPI

```
sudo docker run --name dwapi -p 5757:5757 -p 5753:5753 -d --restart unless-stopped kenyahmis/dwapi:latest
```

## MySQL setup

### 2. Enter mysql

```
mysql -u[username] -p[password]
```
### NOTE: replace the username and password to match your own MySQL credentials. Remove the brackets as well

### 3. Create a DWAPI database user for mysql

```
create database dwapi;
```

### 4. Assign privileges to the DWAPI database user for MySQL

```
GRANT ALL PRIVILEGES ON *.* TO 'dwapi'@'%' IDENTIFIED BY 'dwapi' WITH GRANT OPTION;
```

```
FLUSH PRIVILEGES;
```
# Using DWAPI

## 1. Start DWAPI

### On your browser, open dwapi on [https://localhost:5753](https://localhost:5753)

## 2. Dashboard - Dwapi database connection

### a) database provider-MySQL

### b) Server:172.17.0.1

### c) port:3306

### d) user:dwapi

### e) password:dwapi

### f) verify server -ok

### g) verify database-ok

### h) save.

## 3. Restart DWAPI

```
sudo docker restart dwapi
```

### Refresh browser until dwapi loads.

## 4. Configurations

### a) EMR Settings

### KenyaEMR-On the drop down make KenyaEMR Default.

### b) KenyaEMR Protocols

### Under the action column, look for Host and make it  "172.17.0.1" 

### verify 

### should give you ok 

### Save

## 5. Docket

### Load and send(all) the indicators(care and treatment,PKV services HIV Testing service etc)

## Congrats, you are done !!!






