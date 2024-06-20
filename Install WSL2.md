# Index

1. [Install WSL2](#1-Install-WSL2)

2. [Update WSL](#2-Update-WSL)

3. [Move WSL to desired location](#3-Move-WSL-to-desired-location)

4. [Delete WSL](#4-Delete-WSL)

# 1-Install WSL2

Open PowerShell or Windows Command Prompt with administrator permission.

Step1 Check whether there is a Lunix subsystem on your pc.

Use command ```wsl -l -v``` or ```wsl --list --verbose```

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/3fbe0272-40dc-4d8d-884c-2d52aa64837c)

It shows there is a Linux subsystem for Windows without any distribution, and give some command suggestions to list and install Linux distribution. Go to Step3.

If it shows there isn't a Linux subsystem on your windows, go to Step2.

Step2 Install wsl

Enter ```wsl --install``` command to install wsl.

The default installation path is
```
C:\Users\YourUsername>\AppData\Local\Packages\CanonicalGroupLimited.UbuntuonWindows_<some_random_string>\LocalState\
```

If you want to install WSL distribution to a different path, you need to finish all installation first then see [Move WSL to desired location](#3-Move-WSL-to-desired-location)

Step3 Set WSL2 version

Use ```wsl --set-default-version 2``` to set the WSL2 as the default version.

Step4 Install a Linux Distribution (Ubuntu as example)

```wsl --install -d Ubuntu```, recommand this one.

_command ```wsl --install``` seems choose Ubuntu automatically on my computer_

You can also install distribution from Microsoft Store, search for your desired Linux distribution (e.g., Ubuntu, Debian, Kali Linux, etc.).

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/d46b8a0e-43a7-426d-82fa-82f69b4f0e11)

If you use command line to install distribution, when it done, it will run distribution automatically.

If you install distribution through Microsoft Store, launch it after installation finished from start menu.

It will ask you to set your Linux user name and password.

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/a99529c3-6993-4170-9629-a82d57f639f2)

After ser username and password successfully, it will login into Ubuntu shell automatically.

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/0bb3db22-6210-49bf-b058-12f2a1ab580b)

Now you can use Ubuntu in shell and also software like vs code.

# 2-Update WSL

```wsl --update```

# 3-Move WSL to desired location

Step1 List your installed distributions to find the exact name

```wsl --list --verbose```

Step2 Export the distribution to a .tar file

```wsl --export <DistributionName> <FilePath>.tar```

Replace <DistributionName> with the name of your distribution (e.g., Ubuntu) and <FilePath> with the path where you want to save the .tar file (e.g., D:\WSL\Ubuntu.tar).

like: ```wsl --export Ubuntu D:\WSL\Ubuntu.tar```

Step3 Unregister the Distribution

Unregister the distribution to remove it from its current location

```wsl --unregister <DistributionName>```

like ```wsl --unregister Ubuntu```

This command is use to delete distributiong.(SEE Delete WSL)

Step4 Import the Distribution to the New Location

Import the distribution from the .tar file to the new location:

```wsl --import <DistributionName> <InstallLocation> <FilePath>.tar```

Replace <DistributionName> with the name you want for the distribution (e.g., Ubuntu), <InstallLocation> with the new path where you want to install the distribution (e.g., D:\WSL\Ubuntu), and <FilePath> with the path to the .tar file.

like: ```wsl --import Ubuntu D:\WSL\Ubuntu D:\WSL\Ubuntu.tar```

Step5 Verify the Installation

List your installed distributions again to verify the new location: ```wsl --list --verbose```

Step6 Launch the Distribution:

```wsl -d <DistributionName>```

like:

```wsl -d Ubuntu```

# 4-Delete WSL

Step1 List Installed Distributions:

```wsl -l -v``` or ```wsl --list --verbose```

Step2 Unregister and Delete a Distribution:

Unregister the specific distribution you want to delete. This will remove the distribution and all its data.

```wsl --unregister <DistributionName>``` like ```wsl --unregister Ubuntu```

Step2 Disable WSL and Virtual Machine Platform Features

```
dism.exe /online /disable-feature /featurename:Microsoft-Windows-Subsystem-Linux /norestart
dism.exe /online /disable-feature /featurename:VirtualMachinePlatform /norestart
```

Step2 Remove WSL-Related Files(optional)

If you want to clean up any residual files, you can manually delete the WSL directory (if it still exists) under your user profile. This is typically located at:

```
C:\Users\<YourUsername>\AppData\Local\Packages\CanonicalGroupLimited.UbuntuonWindows_<some_random_string>
```

or the path you set.














