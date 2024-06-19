# Index

1. [Install WSL2](#1-Install-WSL2)

2. [Update WSL](#2-Update-WSL)

3. [Move WSL to desired location(optional)](#3-Move-WSL-to-desired-location(optional))

4. [Delete WSL](#4-Delete-WSL)

# 1-Install WSL2

Open PowerShell or Windows Command Prompt with administrator permission.

Step1 Enter ```wsl --install``` command to install wsl.

The default installation path is
```
C:\Users\YourUsername>\AppData\Local\Packages\CanonicalGroupLimited.UbuntuonWindows_<some_random_string>\LocalState\
```

If you want to install WSL distribution to a different path, you need to export the distribution, unregister it, and then import it to other location you want.

Step2 Set WSL2 version

List your installed Linux distributions and check the version of WSL

```wsl -l -v```

If the version is not WSL2, use ```wsl --set-version <distro name> 2``` (```wsl --set-default-version 2``` from GPT) to se the WSL2 as the default version.

Step3 Install a Linux Distribution (Ubuntu)

```wsl --install -d Ubuntu```

You can also install distribution from Microsoft Store, search for your desired Linux distribution (e.g., Ubuntu, Debian, Kali Linux, etc.).

If you use command line to install distribution, when it done, it will run distribution automatically.

If you install distribution through Microsoft Store, launch it after installation finished from start menu.

It will ask you to set your Linux user name and password.

Step4 Check WSL version

```wsl --list --verbose```

# 2-Update WSL

```wsl --update```

# 3-Move WSL to desired location(optional)

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














