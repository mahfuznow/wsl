# Install Windows Subsystem for Linux (WSL)

## Step 1: Enable Windows Subsystem for Linux system feature
1. Open Control Panel.
2. Click on Programs.
3. Click the Turn Windows features on or off link.
4. Check "Windows Subsystem for Linux"
5. Click OK to enable and disable the feature.
6. Restart

**Or,**

Open PowerShell as Administrator and run the following command
```bash
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

## Step 2: Download a Linux distro

|System| 	URL|
|------|--------|
|Ubuntu 20.04| https://aka.ms/wslubuntu2004|
|Ubuntu 20.04 ARM| https://aka.ms/wslubuntu2004arm|
|Ubuntu 18.04| https://aka.ms/wsl-ubuntu-1804|
|Ubuntu 18.04 ARM| https://aka.ms/wsl-ubuntu-1804-arm|
|Ubuntu 16.04| https://aka.ms/wsl-ubuntu-1604|
|Debian GNU/Linux| https://aka.ms/wsl-debian-gnulinux|
|Kali Linux| https://aka.ms/wsl-kali-linux-new|
|OpenSUSE Leap 42| https://aka.ms/wsl-opensuse-42|
|SUSE Linux Enterprise Server 12| https://aka.ms/wsl-sles-12|
|Fedora Remix for WSL| https://github.com/WhitewaterFoundry/WSLFedoraRemix/releases/|
|Ubuntu 18.04| 	https://aka.ms/wsl-ubuntu-1804|
|Ubuntu 18.04 ARM| 	https://aka.ms/wsl-ubuntu-1804-arm|
|Ubuntu 16.04| 	https://aka.ms/wsl-ubuntu-1604|
|Debian GNU/Linux| 	https://aka.ms/wsl-debian-gnulinux|
|Kali Linux| 	https://aka.ms/wsl-kali-linux|
|OpenSUSE| 	https://aka.ms/wsl-opensuse-42|
|SLES|	https://aka.ms/wsl-sles-12|


> For update visit here: https://docs.microsoft.com/en-us/windows/wsl/install-manual

You can download it normally 

**Or,**

You can download using powershell:

Run the following command in PowerShell to download a distro:

```bash
    Invoke-WebRequest -Uri https://aka.ms/wsl-ubuntu-1804 -OutFile Ubuntu.appx -UseBasicParsing
```
> **If this ERROR occurs:** Invoke-WebRequest : The request was aborted: Could not create SSL/TLS secure channel. Then execute following comand and then try again with previous one.

```bash
    [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
```


## Step 3: Installation
Before installation check if the WSL is already installed or not. If already registered then unregister that first otherwise there will be error. For this execute the following command:
```bash
    #this will list down the registered WSLs
    wslconfig /l
    #if you want to unregister one then run following
    wslconfig /u distro-name
```

### Install as Windows app
It will be installed as windows app in "C:\Program Files\WindowsApps\distro-folder" and the Filesystem of the wsl will be in "C:\Users\Mahfuz\AppData\Local\Packages\distro-folder"

for this double click the "distro-name.appx" to install

**Or,**
run the following command
```bash
    .\distro-name.appx
```

### Install as separate app in other dirve

1. Rename distro-name.appx to distro-name.zip
2. Extract the zip file
3. If after extraction you find more .appx file then choose the biggest one & delete rest of the files.
4. Now rename this remaining file "distro-name.zip"
5. Extract the file
6. Now you shoud get the "distro-name.exe" file
7. Now run it.

**Or,**
Run the executable to initialize:
```bash
    .\distro-name.exe
```
> If you use "windows update blocker" then it might cause issue on running WSL. Disable the windows update blocker and try again


## Step 4: Setting up
If everithing goes right then input username and password will apear. Then set an username (i use mahfuz) and a password for your WSL.

Once the installation is done, you can see a new folder is created named distro-name . This is the location of your WSL.

```bash
    cd distro-name
    ls
```
Output will look something like this.

![output3](https://raw.githubusercontent.com/mahfuznow/wsl/master/images/output3.png)

>  **The highlighed folder is the FILESYSTEM  of your new WSL.**

Now you can pin this app on your taskbar or in your start menu
>You can also open this from CMD also. For this you can run any of this bellow. It will bring the default WSL terminal.
```bash
    bash
    wsl
```
>If you want to change the default one you can do it also :
```bash
    wslconfig /s distro-name
```

## Step 5: Testing
After completing those Ubunto Terminal should apear on your start menu program list. Run that and input following commands:

```bash
    #this will print the username
    whoami
    #this will print the current working directory
    pwd
    #this will create a file named "test.txt"
    touch test.txt
    #this will list down the files on current directory
    ls
```
![output4](https://raw.githubusercontent.com/mahfuznow/wsl/master/images/output4.png)

>**now you can check the file from Windows Explorer:** Location will be: F://WSL/Ubuntu/rootfs/home/mahfuz

<mark> Do not modify or Edit the files on this loacation using any windows software because it may cause corupted file in WSL

# Install wsl-2
http://aka.ms/wsl2-install

## Requirements
* For x64 systems: Version 1903 or higher, with Build 18362 or higher.
* For ARM64 systems: Version 2004 or higher, with Build 19041 or higher.
* Builds lower than 18362 do not support WSL 2. Use the Windows Update Assistant to update your version of Windows.

## Step 1 - Enable Windows feature
1. Open Control Panel.
2. Click on Programs.
3. Click the Turn Windows features on or off link.
4. Check "Windows Subsystem for Linux"
5. Check "Virtual Machine feature"
6. Click OK to enable and disable the feature.
7. Restart

**Or,**

Open PowerShell as Administrator and run the following command
```bash
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

### Step 2 - Download the Linux kernel update package
* Download the latest package:
https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi
* Run the update package downloaded in the previous step. (Double-click to run - you will be prompted for elevated permissions, select ‘yes’ to approve this installation.)


### Step 3 - Change previously WSL version

* Check the WSL versions:

```bash
wsl -l -v
```
* Upgrade previously installed WSL
```bash
wsl --set-version <distribution name> <versionNumber>
wsl --set-version kali-linux 2
```
* Set default for future WSL installations
```bash
wsl --set-default-version 2
```
