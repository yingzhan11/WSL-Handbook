# With PowerShell or Windows Terminal

Open PowerShell, enter command ```Ubuntu``` to login the Ubuntu shell, need to wait a while sometimes, and ```exit``` to logout.

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/8d7d3494-d546-4e16-85ea-69f557c0c04c)

If you use Windows Terminal, you can also ccustomize the appearance, check the step: [https://learn.microsoft.com/en-us/windows/wsl/setup/environment](url)

# Install apt

Update before each time you install some tools

```sudo apt update && sudo apt upgrade```

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/0be3f824-14a0-4f08-9180-03d8689dc448)

...

Then you can install tools you need, like gcc, make, git, vim, etc.

Like: ```sudo apt install gcc```, ```sudo apt install make``` or whatever you want.

![image](https://github.com/yingzhan11/WSL-Handbook/assets/153290203/919961fc-4f4e-4abf-955f-03f3b71692c4)

check the installation with ```dpkg -s <name>```

# Use Ubuntu in VS Code```

install VS Code extension of WSL: UBUNTU, then you can open ubuntu teminal in VS Code
