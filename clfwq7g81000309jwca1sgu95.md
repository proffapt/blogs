---
title: "Setup OpenVPN Server on Azure"
seoTitle: "How to host OpenVPN server on Microsoft Azure?"
seoDescription: "Elaborated step by step guide to setup OpenVPN server on Microsoft Azure via student offer. Setup and connect to your own self-hosted vpn to bypass blocking"
datePublished: Mon Mar 06 2023 08:23:22 GMT+0000 (Coordinated Universal Time)
cuid: clfwq7g81000309jwca1sgu95
slug: openvpn-server-on-azure
canonical: https://gist.github.com/proffapt/15cacf6c0abdd5509e5c1b7d2c7a49ce
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1714185485394/1698d45d-3015-4f7c-bb5a-33c8d10e2e7f.png
tags: azure, vpn, openvpn, iitkgp, openvpn-on-azure

---

### Step 1: Get Microsoft Azure

* Get the [GitHub Student Developer Pack](https://docs.github.com/en/education/explore-the-benefits-of-teaching-and-learning-with-github-education/github-global-campus-for-students/apply-to-github-global-campus-as-a-student#applying-to-github-global-campus).
    
* Now navigate to the benefits page and apply a filter for `cloud` or just [click here](https://education.github.com/pack/offers?sort=popularity&tag=Cloud). Follow the steps to sign up for Azure, and you will receive **$100 credits**.
    

> **Note**  
> Although, we could have done it [directly using Institute ID on Microsoft Azure](https://signup.azure.com/studentverification?offerType=1&correlationId=bd79ce7e43aa48319516e398c31f47bd). But the afore-mentioned method exposes you to various other possibilities which you might have not even thought of. We chose Microsoft Azure here, if you want you can also choose DigitalOcean or any other cloud platform of your preference.

### Step 2: Create an EC2 instance

* Goto [Azure portal](https://portal.azure.com/#home)
    
* Click on the `hamburger` menu &gt; `Create a resource` &gt; `Compute` &gt; `Ubuntu Server 22.04 LTS`. Fill in the necessary details in the `Basics` section.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680271650791/addfaf4e-622d-4c7b-9f6c-f177769afa38.png align="center")
    
    * Create a new `Resource Group` & give your virtual machine a name.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680271728857/7c797005-c5b5-4766-a1b6-f67938b6bfcd.png align="center")
        
    * Now about **region** & **disk size**.  
        **First, select the cheapest size and then select the region from the available options**. A standard `B1` size is going to be good enough and will last around 11 months using free credits. Now choose the closest region where the said size is available, which in our case will be `South-East Asia`. A bigger (aka more costly) size would probably be available in Indian regions. Follow the steps shown in the images below.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680271871813/c2cb268d-0d8d-4406-9bf9-5c6332802bcb.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680271936925/f04ad0da-3903-4f00-af64-72840d1c0dd3.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680271954074/3270ffe0-0096-48d2-b43b-fd7567ece04b.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680272002561/dd234d95-d124-4e67-85ae-1c7c2cc9f8bf.png align="center")
        
* Select `Password` as the Authentication Method and fill in the required fields.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680273763667/36c8d632-affb-4c16-8f63-f6f8552a3e42.png align="center")
    
    > **Note**  
    > Though using a password as the authentication method is easy to follow, it is equally less secure. It is recommended to use `ssh` as the authentication method. It is indeed tougher, to follow the ssh path that's why it is not mentioned in this blog post, you can refer to my gist for the [Steps to set up the server via SSH public keys](https://gist.github.com/proffapt/15cacf6c0abdd5509e5c1b7d2c7a49ce).
    
* Choose **HTTPS(443)** in `Select inbound ports`.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680273727043/478431f4-c04d-42e0-92d3-1d0e93bcc768.png align="center")
    
* Leave the rest of the settings as default in other sections and click `Review+Create`.
    
* Now, wait for the VM to be deployed. Once the VM is deployed
    
    * Click `Goto Resource`.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680272216678/dcd76058-1150-4a76-94ff-c688f396f4da.png align="center")
        
    * Click `Configure` the *DNS* option under `Networking`.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680272244269/fa996e42-d53e-40a4-bff4-e51267b945ca.png align="center")
        
    * Type in any DNS name like your username in the `DNS name label` field and press `Save`.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680272299737/75b9b2e5-d053-4bb2-8739-b0652fcb7fdc.png align="center")
        

### Step 3: SSH into the Remote Server

> **<mark>Warning</mark>**  
> For this step, you will need to switch to a network other than that of campus as **PORT 22(default port for SSH) IS BLOCKED ON THE CAMPUS NETWORK.**

SSH steps are drastically different for a Windows client & a Linux/MacOS (`*nix`) client.  
Refer to the following section to read about the steps for the client of your interest.

#### SSHing via a Windows machine

* To make sure your PC has `SSH` client and server both installed, run the following command on [Command Prompt](https://www.makeuseof.com/tag/a-beginners-guide-to-the-windows-command-line/) as **Administrator**.
    
    ```ps
    Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
    Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
    ```
    
    * Windows also has [Powershell](https://en.wikipedia.org/wiki/PowerShell) and the new [Windows Terminal](https://en.wikipedia.org/wiki/Windows_Terminal) which combines all the different [shell environments](https://en.wikipedia.org/wiki/Shell_(computing)). So, you can choose one from these as well, but it doesn't matter in this context.
        
* Now `ssh` into the remote server
    
    ```ps
    ssh user@host_address
    ```
    
    > <mark>Explaining the command</mark>  
    > **user**: Name of the user given while creating the virtual machine.
    > 
    > **host\_address**: Public IP address of the machine.
    

#### SSHing via a Linux or MacOS machine

* Execute the following command, then enter your password in the prompt.
    
    ```sh
    ssh user@host_address
    ```
    
    > <mark>Explaining the command</mark>
    > 
    > **user**: Name of the user given while creating the virtual machine.
    > 
    > **host\_address**: Public IP address of the machine.
    

### Step 4: Setup OpenVPN Access Server

After we have ssh'ed into the machine, we have to set up the OpenVPN Access Server.

* Before that, it's a good practice to update and upgrade your system via
    
    ```sh
    sudo apt update
    sudo apt upgrade
    ```
    
* Execute the following command
    
    ```sh
    wget https://git.io/vpn -O openvpn-install.sh && sudo bash openvpn-install.sh
    ```
    
    It will download and execute a script that automates OpenVPN server configuration.
    
* Keep in mind to update the following options during the setup process & leave the rest in their default state:
    
    * `IP address`: Your *Public IP* for the azure machine.
        
    * `UDP or TCP`: Enter 2 for **TCP** as **UDP ports are blocked on the campus network**.
        
    * `PORT`: **443**
        
    * `DNS RESOLVER`: Enter 4 for **OpenDNS**.
        
    * `CLIENT`: One configuration for one client/device. Name it like pc, mobile, etc.
        
* The `.ovpn` file will be stored inside `/root` directory, copy it into your user's home directory using the following command
    
    ```sh
    sudo cp /root/client_name.ovpn ~/
    ```
    
    > <mark>Explaining the command</mark>  
    > **client\_name**: Name of the client you specified in the script.
    

> **Note**  
> Run the same script to generate new clients (you will need a unique client for each device that’s going to be connected to the VPN), i.e., **one**`.ovpn`**file and one connection**.

#### Configuration for Gaming

Use the `TCP_NODELAY` option if you are planning to use this VPN for gaming. Execute the following command on the remote VPN server

```sh
sudo echo "tcp-nodelay" | sudo tee -a /etc/openvpn/server.conf
```

Now restart the OpenVPN service using

```sh
sudo systemctl restart openvpn.service && sudo systemctl restart openvpn-server@server.service
```

### Step 5: Download ovpn files

Now we have to transfer the `.ovpn` files generated on the remote server to our local machine. The steps to achieve this are different for `*nix` (Linux or MacOS) & Windows, refer to the following sections to read about the steps for your platform of interest.

#### Windows

* [Download WinSCP](https://winscp.net/eng/download.php) a GUI implementation for `SCP (secure copy)` on windows. Open it.
    
* Click on `New Session`.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680272478011/6a6b485b-0538-4c62-b454-b3f5c732665c.png align="center")
    
* Enter the following login configuration
    
    * `File Protocol`: *SCP*.
        
    * `Host Name`: Your remote machine's Public IP address.
        
    * `Port`: 22 (Default).
        
    * `Username`: *The username* which you set for the remote machine.
        
    * `Password`: *The password* which you set for the remote machine.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680273219634/8a623433-423e-4736-8dd4-32955a054631.png align="center")
        
    * Press `Login` then `YES`.
        
* Select and download all the `.ovpn` files you created which will be shown on the interface.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680272567975/55073995-9663-4b99-bb87-0e51ca065f28.png align="left")
    
* Now shut down the `WinSCP session`
    

#### Linux & MacOS

Run the following command, the key will be downloaded in the `Downloads` directory after you enter the correct password set by you earlier.

```sh
scp user@host_address:client_name.ovpn ~/Downloads/
```

> <mark>Explaining the command</mark>  
> **user**: Name of the user given while creating the virtual machine.  
> **host\_address**: Public IP address of the machine.  
> **client\_name**: Name of the client you specified in the script.

To *start/stop/check* the status of the OpenVPN server use `systemctl`:

```sh
sudo systemctl start openvpn@server.service
sudo systemctl stop openvpn@server.service
sudo systemctl status openvpn@server.service
```

> **For Android**:  
> Follow either of the aforementioned methods and then transfer the downloaded `.ovpn` file to your Android device via Telegram/Bluetooth/Mail or whatever to your android device.

### Step 6: Connecting to the VPN on client devices

#### Android

Download the [OpenVPN Connect](https://play.google.com/store/apps/details?id=net.openvpn.openvpn&hl=en_IN&gl=US) app from Play Store. Open the app and after going through the first screen, go to the **Files** tab, there import the `.ovpn` file, and connect.

#### Linux & macOS

* Get `OpenVPN` Client.
    
    * **Linux**
        
        In most of the distros, you can go to the network manager and import the `.ovpn` file. If not then install OpenVPN with `sudo apt install openvpn`.
        
    * **macOS**
        
        You can either download the *GUI tool,*[tunnelblick](https://tunnelblick.net/downloads.html) for importing the `.ovpn` file or download the *CLI tool* for OpenVPN via [MacPorts](https://www.macports.org/install.php) or [HomeBrew](https://brew.sh/) using `sudo ports install openvpn` and `brew install openvpn` respectively.
        
* Start the client with your configuration file
    
    ```bash
    sudo openvpn --config /path/to/config.ovpn
    ```
    
    > <mark>Explaining the command</mark>  
    > **/path/to/config.ovpn**: It is the path to the .pem file which you downloaded just before deploying the VM.
    

#### Windows

Download the official [OpenVPN Connect client for Windows](https://openvpn.net/client-connect-vpn-for-windows/), import the `.ovpn` file, and toggle it ON to finally connect - [video guide](https://www.youtube.com/watch?v=P2SroQ_pzPU).

### Step 7: Budget Control

> **<mark>Warning</mark>**  
> This is a very important step, to ensure the long-term usability of your credits.

* Use only one instance.
    
* Bandwidth is ***free up to $100 credits***, so it's better not to waste resources on the VPN.
    

> **Note**  
> If in any case, you have to stop an instance forcibly, do it; to be on the safer side.