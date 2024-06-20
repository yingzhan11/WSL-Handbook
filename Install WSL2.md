# Index

1. [Install WSL2](#1-Install-WSL2)

2. [Update WSL](#2-Update-WSL)

3. [Move WSL to desired location](#3-Move-WSL-to-desired-location)

4. [Delete WSL](#4-Delete-WSL)

# 1-Install WSL2

_**MUST! Open PowerShell or Windows Command Prompt with administrator permission.**_

**Step1-Check whether there is a Lunix subsystem on your pc**

Use command ```wsl -l -v``` or ```wsl --list --verbose```

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/3fbe0272-40dc-4d8d-884c-2d52aa64837c)

It shows there is a Linux subsystem for Windows, but no distribution. Go to Step3.

If it shows there isn't a Linux subsystem on your windows, go to Step2.

**Step2-Install wsl**

Enter ```wsl --install``` command to install wsl.

The default installation path is:
```
C:\Users\YourUsername>\AppData\Local\Packages\CanonicalGroupLimited.UbuntuonWindows_<some_random_string>\LocalState\
```

You cannot change the path when install wsl. If you want to install WSL distribution to a different path, you need to finish all installation first then see [3. Move WSL to desired location](#3-Move-WSL-to-desired-location)

**Step3-Set WSL2 version**

Use ```wsl --set-default-version 2``` to set the WSL2 as the default version.

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/85e56fe8-1deb-414c-bc23-67e608fd692b)

**Step4-Install a Linux Distribution (Ubuntu as example)**

```wsl --install -d Ubuntu``` (recommand this one)

_command ```wsl --install``` seems choose Ubuntu automatically on my computer_

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/d46b8a0e-43a7-426d-82fa-82f69b4f0e11)

You can also install distribution from Microsoft Store, search for your desired Linux distribution (e.g., Ubuntu, Debian, Kali Linux, etc.).

If you use command line to install distributions, when it done, it will run the distribution automatically.

If you install distributions through Microsoft Store, launch it after installation finished from start menu.

It will ask you to set your Linux user name and password.

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/a99529c3-6993-4170-9629-a82d57f639f2)

After set username and password successfully, it will login into Ubuntu shell automatically.

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/0bb3db22-6210-49bf-b058-12f2a1ab580b)

If you didn't set a user name it will login as root user.

If you set a wrong name or password or you just want to change them, you can use command ```wsl --unregister Ubuntu``` to delete your user and Ubuntu, then enter ```wsl --install -d Ubuntu``` again and you can enter a new name and password.

**Step5 Check installation and open Virtual Machine platform**

Use command ```wsl -l -v``` to check whether you already installed a distribution successfully.

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/a62bcbde-edae-4314-9176-132e2f575677)

Then restart your computer.

Open the file explorer, there should be a Linux subsystem here with Ubuntu. 

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/daae089c-36da-47d2-828a-c2d6f0486af8)

If not, you should enable the VM platform manully, use commands:

```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/5679a07d-1088-49d6-acd0-0137bb045da9)

Then restart computer again, and the Linux icon should be there now. And we finish installation now.

# 2-Update WSL

Remember to update wsl regularly or before install more distribution ```wsl --update```

# 3-Move WSL to desired location

WSL2 need about 1GB of disk space, and Ubuntu need 1-2GB, if you install any apt in Ubuntu later they may need more space. I install gcc, make and vim, they use 1GB. Totally 4-5GB. 

If your system disk space isn't rich, or you want a lot of distributions and apts, you'd better move the wsl to other disk.

Good news is I found it seems we don't need to put our codes or files in Linux VM. I try to use ubuntu shell in **VScode**, to visit my normal windows folders and compile some codes, it works. _Not work in powershell, must VScode_

So you only need about 5GB in system disk for all installation pkgs if you use VScode. _Not sure for other softwares_

Therefore I didn't move my Ubuntu to other disk now. So this part only shows the command steps without images.

**Step1-Check the name of distributions**

List your installed distributions to find the exact name

```wsl --list --verbose```

**Step2-Export distributions**

Export the distribution to a .tar file with: ```wsl --export <DistributionName> <FilePath>.tar```

Replace <DistributionName> with the name of your distribution (e.g., Ubuntu) and <FilePath> with the path where you want to save the .tar file (e.g., D:\WSL\Ubuntu.tar).

Like: ```wsl --export Ubuntu D:\WSL\Ubuntu.tar```

**Step3-Unregister the distribution on the current location**

Unregister the distribution to remove it from its current location. Command is: ```wsl --unregister <DistributionName>```

like ```wsl --unregister Ubuntu```

**Step4-Import the distribution to the new location**

Import the distribution from the .tar file to the new location: ```wsl --import <DistributionName> <InstallLocation> <FilePath>.tar```

Replace <DistributionName> with the name you want for the distribution (e.g., Ubuntu), <InstallLocation> with the new path where you want to install the distribution (e.g., D:\WSL\Ubuntu), and <FilePath> with the path to the .tar file.

Like: ```wsl --import Ubuntu D:\WSL\Ubuntu D:\WSL\Ubuntu.tar```

**Step5-Verify the Installation**

List your installed distributions again to verify the new location: ```wsl --list --verbose```

**Step6-Launch the Distribution**

```wsl -d <DistributionName>```

Like: ```wsl -d Ubuntu```

# 4-Delete WSL

**Step1-List Installed Distributions**

```wsl -l -v``` or ```wsl --list --verbose```

**Step2-Unregister and Delete a Distribution**

Unregister the specific distribution you want to delete. This will remove the distribution and all its data.

```wsl --unregister <DistributionName>``` like ```wsl --unregister Ubuntu```

**Step3-Disable WSL and Virtual Machine Platform Features**

This command will disablt the WSL and VM platform, and you cannot see the Linux subsystem in folder explorer anymore. Next time if you want to use Linux subsystem and WSL again, you need to enbale this manually, see [Step5 Check installation and open Virtual Machine platform](#Step5-Check-installation-and-open-Virtual-Machine-platform)

```
dism.exe /online /disable-feature /featurename:Microsoft-Windows-Subsystem-Linux /norestart
dism.exe /online /disable-feature /featurename:VirtualMachinePlatform /norestart
```




