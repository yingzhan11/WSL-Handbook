# Index

1. [In Powershell or Windows Terminal](#1-In-PowerShell-or-Windows-Terminal)

2. [Install apt](#2-Install-apt)

3. [In VS Code](#3-Use-Ubuntu-in-VS-Code)

# 1-In PowerShell or Windows Terminal

Open PowerShell, enter command ```Ubuntu``` to login the Ubuntu shell, need to wait a while sometimes.

```exit``` to logout.

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/8d7d3494-d546-4e16-85ea-69f557c0c04c)

_If you use Windows Terminal, you can also ccustomize the appearance, check the step: [https://learn.microsoft.com/en-us/windows/wsl/setup/environment](url)_

# 2-Install apt

Update before each time you install some tools: ```sudo apt update && sudo apt upgrade```

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/0be3f824-14a0-4f08-9180-03d8689dc448)

...

Then you can install tools you need, like gcc, make, git, vim, etc.

Like: ```sudo apt install gcc```, ```sudo apt install make``` or whatever you want.

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/919961fc-4f4e-4abf-955f-03f3b71692c4)

check the installation with ```dpkg -s <name>```

# 3-Use Ubuntu in VS Code

If you open vs code after install WSL and Ubuntu, there would be a popup window to recommand you install WSL extension of WSL. You can also search it in vscode.

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/93c15149-da14-4e93-99fe-e8d36e3a1bd3)

Then open VScode terminal, and you can choose Ubuntu shell now, and your code will be run in the environment of Linux system.

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/d764bee6-4e4a-42df-ab52-0dafeafcf7fc)

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/fd056503-1520-4e93-9537-509d65bf3e62)

