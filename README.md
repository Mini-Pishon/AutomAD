# AutomAD
Easy peasy AD setting up and user injection


# Cheap and Fast Windows Server Setup

This repository contains scripts to quickly and easily set up your Windows Server and Active Directory (AD). The scripts should be executed in the following order:

## 1. setting_up_srv.ps1:
- Prompts for:

    - hostname
    - IP address
    - Subnet prefix
    - Default gateway
    - DNS address

- Performs the following actions: 

    - Renames the server.
    - Configures IP settings (IP address, subnet prefix, default gateway).
    - Sets the DNS server.
    - Renames the network adapter.
    - Enables Remote Desktop and configures the firewall.
    - Prompts for a restart to apply changes.


## 2. add_features.ps1:
- Installs the following features:

    - Active Directory Domain Services (ADDS)
    - DNS
    - Remote Server Administration Tools (RSAT)

## 3. forest_config.ps1
- Prompts for: 

    - Domain Name (e.g., example.com)
    - Domain NetBios Name

- Performs the following actions:

    - Imports the ADDSDeployment module.
    - Configures the forest with the specified domain name and NetBios name.
    - Sets various forest configuration parameters such as database path, log    path, and sysvol path.
    - Installs DNS as part of the forest configuration.
    - Prevents automatic reboot upon completion.


# Injection

## AD_addusers.ps1

This PowerShell script automates the creation of Organizational Units (OUs) and users in Active Directory (AD) based on data from a CSV file. The script performs the following actions:

### 1. Prerequisites

- Ensure the Active Directory module is available on the system where the script is executed.
- Prepare a CSV file (users.csv) with user data, including columns for first_name, last_name, and password.

### 2. Usage

1. Place the users.csv file in the specified directory (C:\scripts\Ad_scripts\).
2. Ensure the script has the necessary permissions to create OUs and users in Active Directory.
3. Execute the script in a PowerShell environment with the Active Directory module available.

### 3. Script Overview

####  1. Input

- CSV File: The script reads user data from C:\scripts\Ad_scripts\users.csv. Ensure the file is in the correct format and accessible.

####  2. Actions Performed

- Import CSV Data:
    - Reads user data from the specified CSV file.

#### 3. Import Active Directory Module:

- Imports the Active Directory module to manage AD operations.

#### 4. Define Base OU Path:

Sets the base path for OUs as DC=dinoland,DC=lan.

#### 5. Create Organizational Units (OUs):

- Creates the main OU "CORE" under the base path.
- Creates the "HUMANS" OU under "CORE".
- Creates "USERS" and "ADMIN" OUs under "HUMANS".

#### 6. Process CSV Data to Create Users:

- Iterates through the CSV data to create users in AD.
- Determines the target OU based on the user index (first 200 users go to "USERS", others to "ADMIN").
- Checks for missing first name or last name and skips such entries.
- Creates users with the specified attributes (name, email, password) if they do not already exist in AD.

### 4. Error Handling

- The script includes error handling for OU and user creation, with warnings and a pause of 5 seconds for errors.

### 5. Output

- The script outputs the status of OU and user creation to the console, indicating success or any errors encountered.


