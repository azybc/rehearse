# How To Switch From Bash To ZSH On Linux

Linux users that spend a lot of time in the terminal become very familiar with the Bash Shell. It’s versatile and reliable, though lacking features that make it feel modern. If you’re looking for something with more features than the Bash Shell, a good alternative to check out is the Z Shell (aka Zsh). It’s based on Bash but has major improvements that make it more usable. In this guide, we’ll go over how you can switch from Bash to ZSH and make it your primary Shell as well as how to activate the Oh My Zsh framework for further improvements.

### Install Zsh

Before using the Zsh shell in place of Bash, you’ll need to install it on your Linux PC. Luckily, as Zsh is one of the most well-known Bash alternatives, getting it is no problem. Open up a terminal window and enter the command to get it working on your distribution.

#### Ubuntu

```
sudo apt install zsh
```

#### Debian

```
sudo apt-get install zsh
```

#### Arch Linux

[Arch Linux](https://www.addictivetips.com/ubuntu-linux-tips/how-to-install-arch-linux/) actually uses the Z Shell by default, in the live disk. Still, even though the live disk uses Zsh doesn’t mean that your installation will have it enabled by default. If you’ve decided to go with traditional Bash, you may still need to install the shell with Pacman.

```
sudo pacman -S zsh
```

#### Fedora

```
sudo dnf install zsh
```

#### OpenSUSE

```
sudo zypper install zsh
```

#### Other Linuxes

As previously mentioned, Zsh is very popular in the Linux community. As a result, users of even the most obscure Linux distributions shouldn’t have any issues finding it in the package manager. To install Zsh, open up a terminal, search for “zsh” and install it like you normally install software.

Alternatively, head over to [the Zsh website](http://www.zsh.org/) and learn how to get it on your Linux OS of choice.

### Configuring Zsh

To configure Zsh, open up the terminal and run it. Running the Z Shell for the first time will automatically open up the configuration wizard. In the wizard, press **1** on the keyboard to start the setup process.

On the next page, Zsh has a lot of options to choose from. These options are to make setting up the shell easy. Once again, press **1**. Selecting this option will walk you through configuring Shell history settings, and etc.

[![](https://cloud.addictivetips.com/wp-content/uploads/2018/06/zsh-1.png)](https://www.addictivetips.com/ubuntu-linux-tips/switch-from-bash-to-zsh-on-linux/attachment/zsh-1/)

First, press **1** to set the history line-size. Then press **2** to create the new history file, and **3** to customize the number of lines to save. When all 3 settings are configured, press **Q** to move back to the main menu.

At the Zsh configuration menu, press **2** to set up the auto-complete system. This system will automatically fill in commands it detects within the history file.

With auto-complete active, press **Q** to go back to the menu.

Setting up options **1** and **2** are the only critical steps. If you’d like, go through the rest of the settings to fully customize your Z Shell experience. Otherwise, press **0** to save the changes and exit.

### Chang Default Shell

Zsh is correctly configured, but not the default Desktop Shell. Bash still opens by default whenever a terminal opens. To solve this problem, go to the terminal and use the **chsh** command.

First, change the shell for Root:

```
$ sudo -s
$ chsh -s /bin/zsh root
```

Now that the Root user is using Zsh by default, it’s time to transition your user over. Keep in mind that you’ll need to re-run this command for every user that wants to use the Zsh Shell. Replace **user** in the command below with your username.

```
chsh -s /bin/zsh username
```

Enter the user’s password to confirm the change. Close the terminal and re-open it to access Zsh.

### Install Oh My Zsh

[![](https://cloud.addictivetips.com/wp-content/uploads/2018/06/zsh-themes.png)](https://www.addictivetips.com/ubuntu-linux-tips/switch-from-bash-to-zsh-on-linux/attachment/zsh-themes/)

Using Zsh alone is enough for most users, but if you want to get even more out of this shell, installing Oh My Zsh is the way to go. To get Zsh, use the **wget** downloading tool to grab the latest version of the installation script. Keep in mind that you’ll need to have the Git package installed on your Linux PC. Search “git” in the package manager, and install it before using Wget.

```bash
$ sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
$ wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh
```

Oh My Zsh, once on your Linux PC, sets up a nice Zsh configuration file complete with dozens of different plugins to choose from. To enable any of these plugins, you’ll need to edit the Zsh config file. In the terminal, use the Nano text editor to open ~/.**zshrc**.

```
$ vim ~/.zshrc
```

First on the list of plugins to choose from in Oh My Zsh are themes. By default, the “Robby Russel” theme is enabled. Want something else? [Go to this page here](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes), find a theme and change the name in the quotation marks to your favorite theme.

Following the theme, there are many other Zsh plugins to enable. Scroll down the list with the arrow key, and read the description of the plugins. See one you like? Remove the # sign from in front of the code to activate the plugin.

Enable the plugins by saving **~/.zshrc** file + X)** and restarting the terminal.

