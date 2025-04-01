# AutomAD
Easy peasy AD setting up and user injection


# Cheap and Fast Windows Server Setup

This repository contains scripts to quickly and easily set up your Windows Server and Active Directory (AD). The scripts should be executed in the following order:

1. setting_up_srv.ps1:

    - Renames the server.
    - Configures IP settings (IP address, subnet prefix, default gateway).
    - Sets the DNS server.
    - Renames the network adapter.
    - Enables Remote Desktop and configures the firewall.
    - Prompts for a restart to apply changes.
    - add_features.ps1:

2. Installs the following features:
    - Active Directory Domain Services (ADDS)
    - DNS
    - Remote Server Administration Tools (RSAT)
    - Forest_config.ps1:

3. Configures the Active Directory forest.
    - Prompts for:
    - Domain Name (e.g., example.com)
    - Domain NetBios Name