# *WSL*

![](https://img.shields.io/github/last-commit/varshan-4068/wsl-setup?&style=for-the-badge&color=FFB1C8&logoColor=D9E0EE&labelColor=292324)
![](https://img.shields.io/github/repo-size/varshan-4068/wsl-setup?color=CAC992&label=SIZE&logo=googledrive&style=for-the-badge&logoColor=D9E0EE&labelColor=292324)

Hey there i am Sirivarshan K and welcome to the world of wsl let's get started..

<details>

<summary> WSL </summary>

- WSL is an now an open sourced project by Microsoft (Didin't expected to be open sourced by microsoft lol)

- The Windows Subsystem for Linux (WSL) lets developers install a Linux distribution (such as Ubuntu, Debian, Arch Linux, Kali, etc) and use Linux applications, utilities, and Bash command-line tools directly on Windows, unmodified, without the virtual machine or dualboot setup.

</details>

> [!Tip]
> To install wsl a Terminal is required and windows 11 ships with a default terminal named windows terminal so just delete it and install windows terminal preview through microsoft store because this terminal ships with the latest new features when compared with windows terminal

<details>

<summary>  Installation </summary>

- After installing the terminal open it as a powershell profile (by default windows terminal opens it so need to worry )and type the commands given below :

      wsl --list --online  # gives you the list of available distros for to be installed in the wsl  
  
      wsl --install -d <distroname>  # pick a distro from the above command and install it with this command

- Now after the installation is completed you should exit and reopen the terminal with wsl.exe command and follow the steps given below according to the distribution you have installed..

<details>

<summary> Archlinux </summary>

- If you have installed archlinux then type ``wsl -d archlinux`` in your windows terminal and you would be entering into the bash(a default shell in linux) environment of linux as a root user so to add a sudo user and open wsl as sudo user follow the commands mentioned below : 
    
      useradd <your preferred user>  # here replace <your preferred user> with the user name you wanna create for example useradd izagi

      passwd <username>  # if u have created a user as for example izagi with the above command then to create a user password for the user izagi use this command 

      usermod -aG wheel <username>  # this command is used to modify your user for example the user izagi as a sudo user

      pacman -S sudo archlinux-keyring base-devel vim
    
      visudo  # Opens the sudoers file and you need to uncomment the line  %wheel ALL=(ALL) ALL by erasing the # in thae opened sudoers file now after uncommenting save the file and exit with :wq 

      su <username>  # to switch from root user to the sudo user for example the user izagi 

- Finally we had added a new user with sudo previleges, now whenever we open the wsl if you need to login as the created user with sudo privileges instead of a root user open your powershell and type the commands below : 

      wsl --manage archlinux --set-default-user <username>  # this command helps wsl to open bash shell with created user for example izagi instead of a root user

- Exit the powershell and now open the windows terminal and type wsl.exe Boom! you have been logged in as the created user with sudo previlegies instead of a root user. So after this type the command given below :

      cd ~
      vim ~/.bash_profile   # add the code given below in the opened file and save it with the command :wq 

      if [[ -f ~/.bashrc ]]; then   # Add these lines in the ~/.bash_profile file 
          ~/.bashrc
          cd ~
      fi
  
      sudo pacman -Sy  # it will ask for sudo password enter your's and update the pacman 

- That's it now u can install the pacman packages that you needed to be in your wsl..

- I hope i explained it in detail with proper explanation But if u want a perfect non detailed Setup Check down the Summary Section Below...

# *Summary*

- Uninstall Windows Terminal and Install Windows Terminal Preview app from microsoft store..

       wsl --list --online  # gives you the list of available distros for to be installed in the wsl  --> In powershell 
  
      wsl --install -d <distroname>  # pick a distro from the above command and install it with this command --> In powershell 

      wsl.exe --> In powershell 
    
      useradd <your preferred user>  # here replace <your preferred user> with the user name you wanna create for example useradd izagi --> In wsl

      passwd <username>  # if u have created a user as for example izagi with the above command then to create a user password for the user izagi use this command --> In wsl 

      usermod -aG wheel <username>  # this command is used to modify your user for example the user izagi as a sudo user --> In wsl
    
      visudo  # Opens the sudoers file and you need to uncomment the line  %wheel ALL=(ALL) ALL by erasing the # in thae opened sudoers file now after uncommenting save the file and exit with :wq    --> In wsl

      su <username>  # to switch from root user to the sudo user for example the user izagi  --> In wsl

      wsl --manage archlinux --set-default-user <username>  # this command helps wsl to open bash shell with created user for example izagi instead of a root user    --> In powershell 

      sudo pacman -Sy archlinux-keyring base-devel   # it will ask for sudo password enter your's and update the pacman  --> In wsl 

      sudo pacman -Su --> In wsl 

      sudo pacman -S (needed packages to install) --> In wsl 

Recommended Packages : neovim base base-devel yazi fzf zoxide eza bash-completion git npm gcc wget curl unzip 

To Install My Neovim Setup Checkout my [Neovim-Setup Repo](https://github.com/varshan-4068/Neovim-Setup.git) and Enjoy Using and Learning it...

</details>

<details>

  <summary> Ubuntu </summary>

   - If you have installed ubuntu then type ``wsl -d ubuntu`` in your windows terminal and you would be entering into the bash(a default shell in linux) environment of linux and would be prompting to ask for the username to be added and considered as sudo automatically and it will also ask the password to be set for that created user or existing user after these you would be entering into the wsl..
   - Next follow the steps below :

         vim ~/.bash_profile   # open this file and add the line given below

         if [[ -f ~/.bashrc ]]; then  # Add these codes in the opened file and save it with the command :wq on vim...
             source ~/.bashrc
             cd ~
         fi
     
   - That's it you have setup your ubuntu wsl and now you can install the packages needed by following the commands below :

         sudo apt update
     
         sudo apt upgrade

         sudo aot install <your needed packages>

         sudo apt autoremove

         # if you want neovim then install it using sudo snap install nvim i know snaps are garbages but give it a try or build neovim from source

   - To Install My Neovim Setup Checkout my [Neovim-Setup Repo](https://github.com/varshan-4068/Neovim-Setup.git) and Enjoy Using and Learning it...
    
</details>

</details>

<details>

<summary> My Setup </summary>

    sudo pacman -S base base-devel bash-completion eza fastfetch fzf zoxide gcc git unzip wget curl npm htop starship trash-cli unzip nvim 

    git clone https://aur.archlinux.org/paru-bin.git 

    cd paru-bin 

    makepkg -si 

    cd ~

    rm paru-bin 

    paru -S python-pywal16 

    wal -q -e -i /mnt/c/Users/<username>/<wallpaper location>  # this will apply your wallpaper colors to the terminal 

    vim .bashrc 

    (cat .cache/wal/sequences)&  # Add this line in your .bashrc that's it save it using :wq and reopen your wsl boom ! u have your wallpaper colors in your terminal this is optional if you want you can set it up or else skip it..
    
</details>
