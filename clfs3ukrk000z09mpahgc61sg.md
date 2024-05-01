---
title: "Connect to DC Hub at IIT KGP"
seoTitle: "Connecting to MetaHub, the DC hub for IIT Kharagpur"
seoDescription: "Everything you need to know about DC (Direct Connect) and setting up its client, this article will be focusing on IIT KGP but can also be used generally."
datePublished: Wed Mar 08 2023 07:38:26 GMT+0000 (Coordinated Universal Time)
cuid: clfs3ukrk000z09mpahgc61sg
slug: dc-client-setup
canonical: https://gist.github.com/proffapt/5785ae1ddf34728f24805c2bc9ba23c8
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680280077071/1991e8a6-cb56-41bc-934c-63c6277277d0.png
tags: directconnect, dc, iitkgp, metahub, eiskaltdcpp

---

## Introduction

IIT Kharagpur [**once had**](https://www.quora.com/Which-campus-has-highest-total-share-and-users-on-DC++-in-India) one of the largest DC ([Direct Connect](https://en.wikipedia.org/wiki/Advanced_Direct_Connect)) networks in India. It lost its glory when the pandemic hit and everything went online. This is an effort to restore that glory, by educating students about "*How can one connect to the DC Hub properly*".

## Installing the client

The IITKGP DC Hub is a private hub and inaccessible from outside the IIT Kharagpur network. Users connect to hubs using DC clients and can share files at high speeds. The most popular hub is [HiT Hi FiT Hai](https://wiki.metakgp.org/w/HiT_Hi_FiT_Hai).  
There are various DC clients available for different platforms. To name a few, we have

| Platform | Client(s) |
| --- | --- |
| Windows | [EiskaltDC++](https://sourceforge.net/projects/eiskaltdcpp/files/Windows/EiskaltDC%2B%2B-2.4.2-x86_64-installer.exe/download), [DC++](https://dcplusplus.sourceforge.io/) |
| Linux | [EiskaltDC++](https://sourceforge.net/projects/eiskaltdcpp/files/Linux/), [LinuxDC++](https://linux.softpedia.com/get/Communications/Filesharing/LinuxDCplusplus-16399.shtml), [ncdc](https://dev.yorhel.nl/ncdc) |
| MacOS | [EiskaltDC++](https://sourceforge.net/projects/eiskaltdcpp/files/macOS/EiskaltDC%2B%2B-2.4.2-x86_64.dmg/download), [Shakespeer](https://sourceforge.net/projects/shakespeer/), [ncdc](https://saiankit.medium.com/how-to-use-dc-on-mac-using-ncdc-50bcc78aad01) |

However, it is recommended to use [Eiskalt DC++](https://sourceforge.net/projects/eiskaltdcpp/files) for uniformity across different platforms.  
To install EiskaltDC++ on your platform of interest refer to the corresponding section.

#### Windows

[Download Eiskalt DC++](https://sourceforge.net/projects/eiskaltdcpp/files/Windows/).  
Go through the basic installation setup and install it.

#### Linux

Install Eiskalt DC++ on **Debian-based distros** like - *ubuntu, linux mint etc* using the following command

```bash
sudo apt install eiskaltdcpp
```

> **Note**  
> If you are not on a Debian-based distro, search for the package name using the package manager your distro uses and install it.

#### MacOS

* [Install Homebrew](https://brew.sh/) - *skip this step if already installed*.
    
    * To check whether it is installed or not, use the following command
        
        ```bash
        command -v brew
        ```
        
    * If the output is like the following, then brew is installed!
        
        ```bash
        ~> command -v brew
        /opt/homebrew/bin/brew
        ```
        
* Install Eiskalt DC++ using the following command
    
    ```bash
    brew install eiskaltdcpp
    ```
    

## Configuring the client

1. Open Eiskalt DC++ & press the following keyboard shortcut to open its **preferences** window according to your platform.
    
    * `Windows`: **ctrl+o**
        
    * `Linux`: **ctrl+o**
        
    * `macOS`: **cmd+,**
        
2. Set a `Nick` aka *username* for your current instance.
    
    ![image](https://user-images.githubusercontent.com/86282911/223125464-437cbbc0-4e88-46ab-aa5c-a72adf9ba3a8.png align="left")
    
    > **Note**
    > 
    > * **Nick** must be unique.
    >     
    > * Other entries are optional, setting or not-setting them will not create any problem in connecting to the hub.
    >     
    
3. Now Goto: `Connection` &gt; `Advanced` &gt; `TLS settings` and choose `Allow TLS`.
    
    ![image](https://user-images.githubusercontent.com/86282911/223126546-7bbd64fd-e098-4427-91f0-0eaaf80c1ef1.png align="left")
    
4. Now click `Ok`.
    
5. Press the following key combination for the quick connect dialog box, according to your platform.
    
    * `Windows`: **ctrl+n**
        
    * `Linux`: **ctrl+n**
        
    * `macOS`: **cmd+n**
        
6. Enter the domain for MetaHub - `dc.metakgp.org` - to connect. Press `Ok`.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696227283202/fef0c0a9-705a-472c-8c96-e99d3339d406.png align="center")
    
    > **Note**
    > 
    > Refer to [this page](https://wiki.metakgp.org/w/DC) for official updates on the Hub IP and MetaHub as a whole.
    
7. You should now be connected to the hub and if the fonts are set properly you should see something like this.
    
    ![image](https://user-images.githubusercontent.com/86282911/223134018-c1f1c1f2-4272-4611-bc39-d62fe42cbd2a.png align="left")
    
    > NOTE:
    > 
    > * *Just focus on the Prompts and that you are connected, your exact GUI will be different since I customized mine to not bleed my eyes.*
    >     
    > * To properly render (display) the "**METAHUB**" text as shown in the screenshot above follow the steps in the "[Rendering MOTD](https://proffapt.hashnode.dev/dc-client-setup#heading-rendering-motd)" section.
    >     
    
8. You *may* encounter one of these common issues::
    
    * Connected to the hub but unable to browse or download files.
        
    * Nick is already taken by another user.
        
    
    These issues are well explained with their solutions in the [**Some Common Issues**](https://proffapt.hashnode.dev/dc-client-setup#heading-some-common-issues) section. If you run into any other problems not documented here, please fill out the [**MetaHub Issue Tracker Form**](https://bit.ly/dc-issue) to report them. We're always working to improve the user experience and your feedback helps.
    

## How to share content

It's not enough to just download content - **to bring back the DC culture** - everyone is encouraged to share their collection as well.  
To share folder(s) follow the following steps:

> **<mark>Warning</mark>**  
> It is a must to mirror (share) whatever you download, so you at least have to share the folder in which you download content from the HUB.

1. Open Eiskalt DC++ & press the following keyboard shortcut to open its **preferences** window according to your platform
    
    * `Windows`: **ctrl+o**
        
    * `Linux`: **ctrl+o**
        
    * `macOS`: **cmd+,**
        
2. Now navigate to: `Sharing` &gt; `Basic` and toggle off the `View share in simple mode`.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679988433022/d34d5d13-3868-4901-8456-8b2c122edd6a.png align="left")
    
3. Now select the folder(s) where you keep downloaded content from the HUB. Keep the following things in mind:
    
    * You can choose other folders as well, but choosing your download folder is essential to mirror your downloaded files.
        
    * You will need to click on `down arrows` to expand folders.
        
    * You might need to **increase the width of the Name column** to be able to see the names of the folders.
        

## How to download content

1. To browse the files of a specific user, simply `Right-Click` on their profile and select the `Browse Files` option.
    
    ![image](https://user-images.githubusercontent.com/86282911/223689275-e472a0d7-72ab-437e-be6f-402184bacd47.png align="left")
    
2. Now you will be taken to the file explorer for the user's shared directory. Use the `Down Arrow` to expand the folders of your interest.
    
3. Now `Right-click` on the file you want to download and select `Download` or `Download to` (for a list of frequently used folders to download).
    
    ![image](https://user-images.githubusercontent.com/86282911/223690165-a7b398a7-ebd9-4ea6-ae22-3cc71ba4de62.png align="left")
    
4. Now enjoy tremendously fast download speed and the file will be downloaded.
    
    > **Note**  
    > Don't forget to [mirror the content you download](https://proffapt.hashnode.dev/dc-client-setup#heading-how-to-share-content).
    

## Some common issues

1. You are connected to the hub and can also see the list of all connected users but when you try to browse the files for any user it keeps on connecting and finally, nothing happens. This might be a result of multiple configurational and system issues. To fix them you are recommended to follow the below practices:
    
    * Allow all incoming connections for the client through your firewall - recommended for all platforms.
        
    * Changing the mode of your connection.  
        To do so, Goto: `Preferences` &gt; `Connection` &gt; `Connection`, explore the available options and select the one that works for you.
        
        ![image](https://user-images.githubusercontent.com/86282911/223679604-5e05c4df-e0e0-4cfb-b6c1-e4c688e3ebc7.png align="left")
        
    * Make sure you meet the minimum sharing requirement to be able to browse and download content from other users.  
        Refer to the rules for the exact number. At the time of writing this documentation, the rules are:
        
        ![image](https://user-images.githubusercontent.com/86282911/223686051-32cd9e9c-adfd-4911-ab60-0d668f6bdd41.png align="left")
        
2. Nick was already taken by another user, even if your Nick was unique.
    
    ![image](https://user-images.githubusercontent.com/86282911/223686661-ff00172a-2da2-47b2-8836-b77c4671d553.png align="left")
    
    This happens when the connection with the hub is dropped abruptly. It can be due to multiple reasons:
    
    * The network was turned off abruptly.
        
    * The network was changed abruptly.
        
    
    Due to this, the connection packets remain alive and it appears to the hub that you are still connected, i.e., your previous connection wasn't closed properly.
    
    `FIX:` The only way to fix it is to wait for at max 15 minutes so that the packets expire automatically and then you can connect to the hub normally. Usually, they expire quite early but sometimes might take time so better have a walk outside your room, get some fresh air then try to connect to the hub again.
    

## Rendering MOTD

This is completely an optional step based on personal preference. If you want to render the *ASCII art* for `METAHUB` to be rendered properly, as shown in the image below, you will need a mono font.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695802384063/8bb6c1e6-aba1-432c-aabd-a0562112fcba.png align="center")

### Installing mono font

However there are many options available, for the sake of documenting the exact process, we will be installing `hack-nerd-font` which comes with a *mono* version of itself. To install it on your system of preference refer to the sections below.

#### On Windows

1. Download a [Nerd Font](http://nerdfonts.com/) - recommended [Hack Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v2.3.3/Hack.zip).
    
2. Extract the downloaded zip file.
    
3. To install all of them simultaneously, you first need to select them all. To do so, click the first font on the list, hold the `Shift key`, and click the last font. You can also drag to select them if you want. As long as they’re all selected, it doesn’t matter how you do it. It should look like this.:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679988099391/72e81a36-d3ff-43f0-941f-6c5c7edbf71c.png align="left")
    
4. Next, `right-click` on the name of any of the font files. If you have multiple user accounts on your PC, you might want to click `Install for All Users`. Otherwise, just click `Install`.
    
    ![image](https://user-images.githubusercontent.com/86282911/223693099-98f7f279-4540-470a-8d17-0bbe3a219f07.png align="left")
    
5. If you already installed some of the fonts, you’ll get a popup warning you about it. Click `Yes` and let it proceed.
    
    ![image](https://user-images.githubusercontent.com/86282911/223693473-433f1958-ffe4-4768-8c11-9f54fefd06a6.png align="left")
    
6. Another window will indicate the progress of the installation. Once it disappears, your fonts are installed and ready for use.
    

#### On Linux

1. Download a [Nerd Font](http://nerdfonts.com/) - recommended [Hack Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v2.3.3/Hack.zip).
    
2. Unzip and copy to `~/.fonts`.
    
3. Run the following command to manually rebuild the font cache.
    
    Bash
    
    ```markdown
    fc-cache -fv
    ```
    

#### On macOS

* [Install Homebrew](https://brew.sh/) if not already installed.
    
* Use the following command to install the `hack-nerd-font`
    
    Bash
    
    ```markdown
    brew install font-hack-nerd-font
    ```
    

### Changing fonts on your client

Now that the fonts are installed on your system, follow the steps below to configure the client to use those fonts.

1. Press the following keyboard shortcut to open its **preferences** window according to your platform.
    
    * `Windows`: **ctrl+o**
        
    * `Linux`: **ctrl+o**
        
    * `macOS`: **cmd+,**
        
2. Goto: `GUI` &gt; `Fonts`.
    
    ![image](https://user-images.githubusercontent.com/86282911/223131317-2b5329b3-abda-48d3-b1bd-b0f531c4b841.png align="left")
    
3. Double-click on the currently set font's name.
    
4. A dialogue box will appear, search for `mono` keyword.
    
5. Then select the mono-font you wish to use.