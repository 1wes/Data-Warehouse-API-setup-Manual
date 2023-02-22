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


