---
layout: post
title: Getting Started with PDF Viewer in Blazor WSL mode | Syncfusion
description: Learn how to getting started with PDF Viewer control in Blazor WSL (Windows Subsystem for Linux) mode. 
platform: Blazor
control: PDF Viewer
documentation: ug
---

# Getting Started with Blazor PDF Viewer Component in WSL mode

To run the Syncfusion Blazor PDF Viewer in WSL (Windows Subsystem for Linux) mode, you will need to take the following steps:

**Step 1:** Enable the Windows Subsystem for Linux.

![Create-new-blazor-wsl-app](GettingStarted_images/1.png)

To enable the Windows Subsystem for Linux (WSL) on Windows, follow these steps:

Open the Start menu and search for `Control Panel`. Click on `Programs`, then click on `Turn Windows features on or off`. Scroll down and check the box next to `Windows Subsystem for Linux`. Click `OK` and restart your machine.

After your computer restarts, you will be able to install a Linux distribution from the Microsoft Store, such as Ubuntu, and run Linux commands directly in Windows.

**Step 2:** Install the `Ubuntu`

![Create-new-blazor-wsl-app](GettingStarted_images/2.png)

Ubuntu can be installed on a Windows 10 machine through the Microsoft Store. Here are the steps to do so:

Open the Microsoft Store on your Windows 10 machine, Search for `Ubuntu` in the store. Select `Ubuntu` from the search results and click `Get` to begin the installation.

Once the installation is complete, open the Windows Terminal application. In the terminal, type `Ubuntu` and press enter. This will launch the Ubuntu terminal inside of Windows.

On Ubuntu, create a new user with a username and password. 

**Step 3:** Install the dotnet framework for running the WSL (Windows Subsystem for Linux) in the project by running the following code one by one. 

```
    wget https://packages.microsoft.com/config/ubuntu/22.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb

    sudo dpkg -i packages-microsoft-prod.deb

    rm packages-microsoft-prod.deb

    sudo apt-get update && \
    sudo apt-get install -y dotnet-sdk-6.0

```

Check the comment dotnet --info and it should come like below

![Create-new-blazor-wsl-app](GettingStarted_images/3.png)

If the above result is not shown, Please run the comments below or follow the steps in the link below to uninstall and reinstall dotnet. 
```
    sudo apt remove dotnet*
    sudo apt remove aspnetcore*
    sudo apt remove netstandard*
    sudo apt-get remove dotnet-host
    sudo apt autoremove
    sudo apt autoremove -y dotnet-sdk-6.0
    sudo apt-get update
    dotnet
    sudo apt-get install -y dotnet-sdk-6.0
    dotnet
    dotnet --info

```
**Step 4:** Run the sample in WSL (Windows Subsystem for Linux) mode and it will run our Blazor PDF Viewer.

N> Facing any issue while running in WSL (Windows Subsystem for Linux) mode use the following instruction to resolve the issue.

Sample does not load the PDF file and throws an exception like below in console window. 
![Create-new-blazor-wsl-app](GettingStarted_images/4.png)

Use the following codes to install the dependence need for our Blazor PDF Viewer run to fix the issue.

Open the Ubuntu comment window and type the following comments.

```
    sudo cp -u /lib/x86_64-linux-gnu/libdl.so.2 /lib/x86_64-linux-gnu/libdl.so
```
Blazor PDF Viewer uses libdl.so. It has a different name in different WSL Linux versions. need to check its presence in the
\wsl.localhost\Ubuntu\usr\lib\x86_64-linux-gnu location like below.

![Create-new-blazor-wsl-app](GettingStarted_images/5.png)

If it’s in different name like libdl.so.4 then change the comment like below.

```
sudo cp -u /lib/x86_64-linux-gnu/libdl.so.4 /lib/x86_64-linux-gnu/libdl.so
```

Then, in the Ubuntu command window, run the following commands one by one to instal all necessary Blazor PDF Viewer dependencies for a Linux run. 

```
    sudo apt-get install libfontconfig1
    sudo apt-get update && apt-get install -y --allow-unauthenticated libgdiplus libc6-dev libx11-dev
    sudo apt-get update
    sudo apt install libgdiplus

```

Close the project, reopen it, and run it in WSL mode. It will run properly.

![Create-new-blazor-wsl-app](GettingStarted_images/6.png)