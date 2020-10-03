# Install Windows Subsystem for Linux (WSL) on a Non-System Drive

## Enable Windows Subsystem for Linux system feature
Open PowerShell as Administrator and run the following command to enable WSL feature:

```bash
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```


## Create a folder in a non-system drive
Run the following command in PowerShell to create a folder for the installation. For my environment, I will create the folder in F drive.

```bash
    cd F:\
    mkdir WSL
    cd WSL
```

## Download a Linux distro
Run the following command in PowerShell to download a distro:

```bash
    Invoke-WebRequest -Uri https://aka.ms/wsl-ubuntu-1804 -OutFile Ubuntu.appx -UseBasicParsing
```

The following distros are available:

|System| 	URL|
|------|--------|
|Ubuntu 18.04| 	https://aka.ms/wsl-ubuntu-1804|
|Ubuntu 18.04 ARM| 	https://aka.ms/wsl-ubuntu-1804-arm|
|Ubuntu 16.04| 	https://aka.ms/wsl-ubuntu-1604|
|Debian GNU/Linux| 	https://aka.ms/wsl-debian-gnulinux|
|Kali Linux| 	https://aka.ms/wsl-kali-linux|
|OpenSUSE| 	https://aka.ms/wsl-opensuse-42|
|SLES|	https://aka.ms/wsl-sles-12|

## Unpack the downloaded distro
In the unzipped folder, there is one executable (*.exe).

```bash
    cd .\Ubuntu\
    ls
```

![output1](https://raw.githubusercontent.com/mahfuznow/wsl/master/images/output1.png)

## Run the executable to initialize:
```bash
    .\ubuntu1804.exe
```
> If you use "windows update blocker" then it might cause issue on running WSL. Disable the windows update blocker and try again
![output2](https://raw.githubusercontent.com/mahfuznow/wsl/master/images/output2.png)

## Finish
If everithing goes right then input username and password will apear. Then set an username (i use mahfuz) and a password for your WSL.

Once the installation is done, you can see a new folder is created named Ubuntu. This is the location of your WSL.

```bash
    cd Ubuntu
    ls
```
![output3](https://raw.githubusercontent.com/mahfuznow/wsl/master/images/output3.png)

>  **The highlighed folder is the FILESYSTEM  of your new WSL.**

## Testing
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




