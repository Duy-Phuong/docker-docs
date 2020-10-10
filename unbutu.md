https://brb.nci.nih.gov/seqtools/installUbuntu.html

https://www.youtube.com/watch?v=QbmRXJJKsvs

# Install Ubuntu on Oracle VirtualBox

 

### Downloads

*Note the instruction here is based on the latest version of the VirtualBox. If you have already installed an earlier version of VirtualBox, your experience may be different. It is recommended to use the latest version of VirtualBox to avoid issues. The VirtualBox [forum](https://forums.virtualbox.org/) is a good place to find a solution if you see any problems.*

Go to VirtualBox website [here](https://www.virtualbox.org/wiki/Downloads) to download the binary for your current operating system. Since our host machine is running on Windows, I'll choose 'x86/amd64' from Windows hosts. When download is finished, run the executable file. Continue with the installation of VirtualBox with the defaults. This will open VirtualBox at the end of the installation.

[![Virtualbox homepage](unbutu.assets/image001.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image001.png)

### Create Virtual Machine

Click 'New' button to open a dialog. [![Create virtual machine](unbutu.assets/image003.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image003.png)

Type a name for the new virtual machine. Since I am planning to install Ubuntu 14.04, I'll enter 'ubuntu1404'. Note that VirtualBox automatically changes 'Type' to Linux and 'Version' to 'Ubuntu (64 bit)'. These two options are exactly what we need. [![Name virtual machine](unbutu.assets/image005.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image005.png)

The memory size depends on your host machine memory size. In my case, I have 12GB physical RAM. I like to allocate as much as possible for Ubuntu but leave some for my Windows host machine. I pick 8192 MB for my Ubuntu. Note that VirtualBox will create a [swap](https://help.ubuntu.com/community/SwapFaq) partition with the same amount space as base memeory you have entered here. So later when you are selecting the size of the virtual hard drive, make sure it is large enough since the [hard drive](https://help.ubuntu.com/community/DiskSpace) will be splitted into root (/)and swap partitions. The root partition contains by default all your system files, program settings and documents.

[![Control memory size](unbutu.assets/image007.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image007.png)

Accept the default 'Create a virtual hard drive now' and click 'Create' button. [![Create virtual drive](unbutu.assets/createVM.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/createVM.png)

Continue to accept the default 'VDI' drive file type and click 'Next' button. [![Select hard drive type](unbutu.assets/image009.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image009.png)

Change the storage type from the default 'Dynamically allocated' to 'Fixed size' to increase performance.

 [![Select storage type](unbutu.assets/image010.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image010.png)

For the virtual hard drive space, the default value is 8GB which is too little for RNA-Seq analysis. I'll pick 100GB since I have plenty of space in my hard disk. You want to choose a good size for your RNA-Seq analysis. If you realize the drive space is not large enough, you'll need to go over these steps again to create another virtual machine.

[![Confirm virtual drive settings](unbutu.assets/image011.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image011.png)

Click 'Create' button and VirtualBox will generate Ubuntu virtual machine. 

[![Create a virtual drive](unbutu.assets/image012.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image012.png)

Now the virtual machine is created. We are ready to install Ubuntu in this virtual machine. Select your new virtual machine and click 'Settings' button. Click on 'Storage' category and then 'Empty' under Controller:IDE. Click "CD/DVD" icon on right hand side and select the ubuntu ISO file to mount.

Note that if you have not downloaded 64-bit Ubuntu ISO file, you can check out [this page](https://brb.nci.nih.gov/seqtools/index.html#requirement) for more information. When downloading Ubuntu ISO file, make sure to selecte 64-bit version. Also make sure the **VT-x/Virtualization Technology** has been enabled in your computer's [BIOS/Basic Input Output System](http://en.wikipedia.org/wiki/BIOS).

 [![Select IDE](unbutu.assets/image013.png)

 [![Select an image file](unbutu.assets/image015.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image015.png) 

[![Done with selecting the image](unbutu.assets/image017.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image017.png)

Since Tophat program can take an advantage of multiple processors/threads, it is a good idea to specify a large number of processors in virtual machine (default value is 1). You can change this number by clicking on 'System' category. In this case, I change the number of CPUs to 4 since 4 is the largest value shown on the green bar in my case. Now you can click 'OK' button to continue.

[![Select processor number](unbutu.assets/VBSetting_Processor.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/VBSetting_Processor.png)

VirtualBox may pop up a message about 'Auto capture keyboard' option. Read the message there and check 'Do not show this message again' option before clicking OK.

[![Capture keyboard](unbutu.assets/image019.jpg)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image019.jpg)

### Install Ubuntu

Back to Oracle VM VirtualBox Manager, click on the new Ubuntu virtual machine and hit 'Start' button. Now you shall see a 'Welcome' screen. Click 'Install Ubuntu' button. Note that the installation process may differ a little bit from version to version. The screenshots here are based on Ubuntu 14.04.1. 

[![First screen in installing Ubuntu](unbutu.assets/image020.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image020.png)

Click 'Continue' button. [![Prepare to install Ubuntu](unbutu.assets/image022.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image022.png)

Chọn options install use third party ....

Make sure 'Erase disk and install Ubuntu' option is selected and click 'Install Now' button. [![Confirm installation type](unbutu.assets/image024.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image024.png)

Ubuntu will ask you a few questions. If the default is good, click 'Continue' button. [![Choose geolocation](unbutu.assets/image026.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image026.png) [![Keyboard layout](unbutu.assets/image028.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image028.png)

In 'Who are you?' dialog, enter your preferred name, username and password. ***Note that this user will have root/sudo privilege\***. Click 'Continue' button. 

[![Who you are](unbutu.assets/image030.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image030.png)

The installation will continue until it is finished. [![Installing the system](unbutu.assets/image032.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image032.png)

After installation is complete, click 'Restart Now' button. When you see a screen with a black background saying 'Please remove installation media and close the tray (if any) then press ENTER:', just follow it. 

Khi xuất hiện restart ấn nút X và chọn cái dưới cùng

[![Restart Ubuntu](unbutu.assets/image034.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image034.png)

Enter the password you have chosen and press 'Enter'. [![Enter the password](unbutu.assets/image036.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image036.png)

The Ubuntu Desktop OS is ready. You may find the desktop screen is too small. Don't worry. You can solve this easily with "VirtualBox Guest Additions".

[![Ubuntu desktop](unbutu.assets/image037.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image037.png)

### More About VirtualBox

#### Guest Additions

After the Ubuntu guest machine is installed, you will find the Ubuntu OS screen size is not extendable and you are not able to share folders between the host machine and Ubuntu.

**Guest Additions** software provide additional capability to a guest virtual machine, including mouse pointer integration, better video support, share folders, share clipboard, et al.

Before we proceed to install Guest Additions, make sure the current user has sudo/root privilege. If the current user does not have sudo/root privilege or it is not sure, run the following terminal command from an account (such as the user created when Ubuntu was first created; see the screenshot of 'Who are you?' above) with root privileges to enable the root privilege for the current user

```
sudo adduser USERNAME sudo
```

where USERNAME should be replaced by the current user's name.



To install **Guest Additions**, click **Devices > Insert Guest Additions CD images…** [![Insert guest additions](unbutu.assets/image038.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image038.png)

Click 'Run' button (next to 'Cancel' button) to start the installation. Note that the version of VBOXADDITIONS should be matched with the one of VirtualBox you have installed.

[![Confirm VBox](unbutu.assets/image039.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image039.png)

Installing **Guest Additions** requires root privilege. Enter user's password (assume the current user has sudo privilege). [![Enter password for VBox](unbutu.assets/image041.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image041.png)

When the installation is finished, press Return key to close the terminal window. [![Terminal window](unbutu.assets/image043.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image043.png)

Now prepare to restart the system to enable the change. Click 'Shutdown' on the menu and then the 'Restart' button. [![Restart Ubuntu](unbutu.assets/image045.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image045.png) [![Click to restart](unbutu.assets/image047.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image047.png)

After rebooting Ubuntu, you will see the desktop resolution is much better. [![Normal Ubuntu desktop](unbutu.assets/image049.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image049.png)

#### Share Folders

Before you can enable shared folders on the host machine, make sure you have installed VirtualBox **Guest Additions** software on the guest machine.

When Ubuntu guest machine is on, click on **Devices > Shared folders settings…** [![Share folder](unbutu.assets/image051.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image051.png)

Select **Machine Folders** and hit the **add button** (plus sign). [![Share folder setup](unbutu.assets/image053.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image053.png)

Browse to the folder you wish to access from the guest machine. Check **Auto-mount** and **Make Permanent** options and click OK button.

 [![Specify folder to share folder](unbutu.assets/image054.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image054.png)

Click OK button once more.

[![Click OK to confirm share folder](unbutu.assets/image055.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image055.png)

Now type 'terminal' in Dash to open a Terminal. [![Open terminal](unbutu.assets/image056.png)](https://brb.nci.nih.gov/seqtools/images/ubuntu/image056.png)

Type the following line in the Terminal to add a user to 'vboxsf' group. This step is necessary in order to use the VB's 'Shared Folder' feature.

```
sudo adduser brb vboxsf
```

Replace 'brb' with your account name in Ubuntu. When you are done, restart the Ubuntu guest machine and go to /media/ directory. From **Nautilus** (file manager in Ubuntu), click **Computer > File System > Media** folder and inside it you will see a folder beginning with **sf_** (the folder name is *sf_Downloads* in our example). Now you can transfer files between the Ubuntu guest machine and the Windows host machine in Nautilus.



Although Shared Folder system in VirtualBox is a nice feature, using VirtualBox shared folder directly for fastq data, annotation or output directory can significantly reduce the performance compared to a native (Ubuntu) system or VirtualBox native system.

## Resolution

![image-20200712114050709](unbutu.assets/image-20200712114050709.png)

Choose and click restart

## Phím tắt unbutu

```shell
CTRL ALT T : new terminal
CTRL SHIFT T : new tab in terminal
```

# Install chrome in unbutu



https://www.linuxbabe.com/ubuntu/install-google-chrome-ubuntu-18-04-lts

## Install Google Chrome on Ubuntu 18.04 LTS from the Command Line

For those of you who like to practice their command line skills, here is how to install Google Chrome on Ubuntu 18.04 using terminal. Open a terminal window from applications menu.

![google chrome command line linux](unbutu.assets/google-chrome-command-line-linux.png)

Then enter the following command in terminal to create a source list file for Google Chrome browser. Nano is a command line text editor, which allows you to edit text files in the terminal.

```
sudo nano /etc/apt/sources.list.d/google-chrome.list
```

![how to install google chrome in ubuntu 18.04 using terminal](unbutu.assets/how-to-install-google-chrome-in-ubuntu-18.04-using-terminal.png)

Next, copy the following APT line and paste it into **google-chrome.list** file.

```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```

![install google chrome browser ubuntu 18.04 from command line](unbutu.assets/install-google-chrome-browser-ubuntu-18.04-from-command-line.png)

To save the file in Nano text editor, press **Ctrl+O**, then press **Enter** to confirm. Next, press **CTRL+X** to exit out of this file. After that, run the following command to download Google’s [signing key](https://www.linuxbabe.com/security/a-practical-guide-to-gpg-part-1-generate-your-keypair).

```
wget https://dl.google.com/linux/linux_signing_key.pub
```

![install google chrome ubuntu command line](unbutu.assets/install-google-chrome-ubuntu-command-line.png)

Then use **apt-key** to add it to your keyring so the package manager can verify the integrity of Google Chrome deb package.

```
sudo apt-key add linux_signing_key.pub
```

Now update package list and install the stable version of Google Chrome.

```
sudo apt update

sudo apt install google-chrome-stable
```

If you want to install the beta or unstable version of Google Chrome, use the following commands:

```
sudo apt install google-chrome-beta

sudo apt install google-chrome-unstable
```

To start Chrome browser from the command line, run:

```
google-chrome-stable
```

# Pin your favorite apps to the dash

To add an application to the [dash](https://help.ubuntu.com/stable/ubuntu-help/shell-introduction.html.en#activities) for easy access:

1. Open the [Activities](https://help.ubuntu.com/stable/ubuntu-help/shell-introduction.html.en#activities) overview by clicking Activities at the top left of the screen

2. Click the grid button in the dash and find the application you want to add.

3. Right-click the application icon and select Add to Favorites.

   Alternatively, you can click-and-drag the icon into the dash.

# How to Install Visual Studio Code on Ubuntu 18.04

https://linuxize.com/post/how-to-install-visual-studio-code-on-ubuntu-18-04/

## Prerequisites

Before continuing with this tutorial, make sure you are logged in as a [user with sudo privileges](https://linuxize.com/post/how-to-create-a-sudo-user-on-ubuntu/).

## Installing Visual Studio Code on Ubuntu

To install Visual Studio Code on your Ubuntu system, follow these steps:Advertisement

1. First, update the packages index and install the dependencies by typing:

   ```
   sudo apt update
   sudo apt install software-properties-common apt-transport-https wget
   ```

2. Next, import the Microsoft GPG key using the following [wget command](https://linuxize.com/post/wget-command-examples/):

   ```
   wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
   ```

   And enable the Visual Studio Code repository by typing:

   ```
   sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
   ```

3. Once the [apt repository is enabled](https://linuxize.com/post/how-to-add-apt-repository-in-ubuntu/), install the latest version of Visual Studio Code with:

   ```
   sudo apt update
   sudo apt install code
   ```

That’s it. Visual Studio Code has been installed on your Ubuntu desktop and you can start using it.

## Starting Visual Studio Code

Now that VS Code is installed on your Ubuntu system you can launch it either from the command line by typing `code` or by clicking on the VS Code icon (`Activities -> Visual Studio Code`).

When you start VS Code for the first time, a window like the following should appear:

![img](unbutu.assets/ubuntu-virtual-studio-code.jpg)

You can now start installing extensions and configuring VS Code according to your preferences.

## Updating Visual Studio Code

When a new version is released you can update the Visual Studio Code package through your desktop standard Software Update tool or by running the following commands in your terminal:

```
sudo apt update
sudo apt upgrade
```

## Conclusion

You have successfully installed VS Code on your Ubuntu 18.04 machine. Your next step could be to install [Additional Components](https://code.visualstudio.com/docs/setup/additional-components) and customize your [User and Workspace Settings](https://code.visualstudio.com/docs/getstarted/settings).

To learn more about VS Code visit their official [documentation](https://code.visualstudio.com/docs/) page.





# Hướng dẫn cài bộ gõ tiếng Việt ibus-unikey trên Ubuntu 18.04 LTS

https://vinasupport.com/huong-dan-cai-bo-go-tieng-viet-ibus-unikey-tren-ubuntu/

### 1. Cài đặt ibus-unikey

Mở Terminal, thực hiện command sau để cài đặt ibus-unikey

- $ sudo apt-get install ibus-unikey

![img](unbutu.assets/Cai-Dat-Ibus-Unikey-Command.png)

Trường hợp phiên bản Ubuntu của bạn chưa có sẵn gói ibus-unikey thì hãy chạy 2 command sau để thêm vào:

- sudo add-apt-repository ppa:ubuntu-vn/ppa
- sudo apt-get update

### 2. Khởi động lại phần mềm ibus

Để khởi động lại ibus, các bạn dùng command sau:

- $ ibus restart

### 3. Thiết lập gõ tiếng việt cho ibus trên Ubuntu 18.04

**Bước 1:** Tìm kiếm chức năng quản lý **[ Settings ]**

![img](unbutu.assets/Thiet-Lap-Go-Tieng-Viet-Tren-Ubuntu-Step-4.jpg)

**Bước 2:** Ở cửa sổ **[ Settings ]** -> **[ Region & Language ]** -> **[Input Sources ]** -> Bấm **[ + ]** để thêm 1 input source

![img](unbutu.assets/Thiet-Lap-Go-Tieng-Viet-Tren-Ubuntu-Step-5.png)

**Bước 3:** Ở cửa sổ **[ Add an Input Source ]** -> Tìm kiếm ngôn ngữ là “**Vietnamese**” -> Chọn là “**Vietnamese (Unikey)**” -> Bấm “**Add**”

![img](unbutu.assets/Thiet-Lap-Go-Tieng-Viet-Tren-Ubuntu-Step-6.png)

**Chú ý**: Đối với Ubuntu 18.10 trở lên, khi tìm kiếm với “**Vietnamese**“, nó sẽ chỉ hiển thị **Vietnamese.** Các bạn bấm tiếp vào “**Vietnamese**” nó sẽ xổ ra 2 dòng như bên trên.

**Bước 4:** Sau đó restart lại Ubuntu và xác nhận Ibus-Unikey đã có 2 ngôn ngữ là tiếng Anh và tiếng Việt

![img](unbutu.assets/Thiet-Lap-Go-Tieng-Viet-Tren-Ubuntu-Thanh-Cong.png)

Bạn có thể chuyển đổi qua lại giữa 2 ngôn ngữ bằng phìm tắt là “Windows + Space”

### 4. Thiết lập gõ tiếng việt cho ibus trên Ubuntu 16.04 và 17.10 (Version cũ)

**Bước 1:** Mở Terminal lên và chạy command sau để thiết lập gõ tiếng Việt cho Ibus

- $ ibus-setup

**Bước 2:** Cửa sổ [**IBus Preferences**] hiện ra.

Ở tab [ **General** ] -> Tích vào ô “**Show icon on system tray**”

![img](unbutu.assets/Thiet-Lap-Go-Tieng-Viet-Tren-Ubuntu-Step-1.png)

**Bước 3:** Chuyển sang tab [ **Input Method** ] -> bấm vào “**Add**” để thêm ngôn ngữ tiếng Việt

![img](unbutu.assets/Thiet-Lap-Go-Tieng-Viet-Tren-Ubuntu-Step-2.png)

**Bước 4:** Tìm kiếm ngôn ngữ “**Vietnamese**” -> Chọn “**Unikey**” -> Bấm “Add” để thêm ngôn ngữ tiếng Việt

![img](unbutu.assets/Thiet-Lap-Go-Tieng-Viet-Tren-Ubuntu-Step-3.png)



https://vinasupport.com/cac-lenh-linux-kiem-tra-cac-thong-so-vps-server/

# Cách sử dụng lệnh grep trong Linux

https://vinasupport.com/cach-su-dung-lenh-grep-trong-linux/

## Giới thiệu về lệnh grep

[Lệnh grep](https://vinasupport.com/tag/lenh-grep/) thường được sử dụng để [tìm kiếm chuỗi văn bản](https://vinasupport.com/tag/tim-kiem-van-ban/), hoặc các dòng có các chuỗi trong các file văn bẳn mà match với 1 chuỗi đầu vào. [Grep Linux Command](https://vinasupport.com/tag/grep-linux-command/) được xem 1 trong những lệnh hữu ích và được sử dụng phổ biến trên hệ thống Linux/Unix

## Cú pháp lệnh grep

![img](unbutu.assets/cu-phap-lenh-grep-linux-command-e1568714482443.png)

## Một số ví dụ sử dụng lệnh grep

### Tìm kiếm một chuỗi văn bản

Tìm kiếm dòng có chưa chuỗi “**admin**” trong file /etc/passwd

- $ grep admin /etc/passwd

![img](unbutu.assets/Grep-Chuoi-admin-Trong-File-Passwd.png)

### Hiển thị số dòng (Line Number) trong kết quả

Sử dụng tham số -n

- $ grep -n admin /etc/passwd

### ![img](unbutu.assets/Grep-Hien-Thi-So-Dong-Line-Number.png)

### Chỉ hiển thị kết quả đầu tiên

Sử dụng head -1

- $ grep admin /etc/passwd | head -1

![img](unbutu.assets/Grep-Chi-Hien-Thi-Ket-Qua-Dau-Tien.png)

### Hiển thị kết quả cuối cùng

Sử dụng tail -1

- $ grep admin /etc/passwd | tail -1

### Tìm kiếm chuỗi văn bản trong 1 thư mục

Sử dụng tham số -r

- $ grep -r admin /etc/

### Ẩn nội dung không match với giá trị cần tìm

```shell
$ cat a.txt
test hello..[113a6d9e-7b06-42c6-a52b-7a4e4d2e216c]... this is
te [113a6d9e-7b06-42c6-a52b-7a4e4d2e216c].  this  is hello

$ grep -oP '(?<=\[)[^\]]*' a.txt
113a6d9e-7b06-42c6-a52b-7a4e4d2e216c
113a6d9e-7b06-42c6-a52b-7a4e4d2e216c
```

### Tìm kiếm chỉ 1 từ

Trường hợp bạn tìm kiếm chuỗi “admin” thì nó sẽ match kết quả với “admin1”, “admin234”, … Vậy để tìm chính xác với từ “admin” thì sử dụng tham số -w

- $ grep -w admin <file_name>

### Lấy số dòng match với giá trị cần tìm

Ví dụ chỉ ra số dòng match với giá trị “admin” trong file /etc/passwd sử dụng tham số -c

- $ grep -c admin /etc/passwd

![img](unbutu.assets/Grep-Hien-Thi-So-Dong-Match-Voi-Ket-Qua.png)  

# Hướng dẫn sử dụng lệnh apt trên Ubuntu Linux

https://vinasupport.com/huong-dan-su-dung-lenh-apt-tren-ubuntu-linux/

## Giới thiệu về lệnh APT

Ubuntu là 1 hệ điều hành thuộc nhánh Debian Linux. Nó sử dụng các dpkg package để đóng gói các chương trình, ứng dụng, dành để [cài đặt](https://vinasupport.com/tag/cai-dat-ubuntu-package/) vào hệ thống.

[Lệnh APT](https://vinasupport.com/tag/apt-command/) (Advanced Package Tool) là một công cụ dòng lệnh (Command Line Tool) được sử dụng để quản lý các dpkg package (phần mềm / ứng dụng) trên hệ thống của Ubuntu.

## Sử dụng lệnh APT trên Ubuntu

### Update thông tin package từ server

Chúng ta sử dụng lệnh apt update để cập nhật các thông tin mới nhất của các package về máy.

- sudo apt update

### ![img](unbutu.assets/APT-update-Linux-Command-Ubuntu.png)

### Nâng cấp package của hệ thống

Nâng cấp toàn bộ package

- sudo apt upgrade

![img](unbutu.assets/APT-upgrade-Linux-Command-Ubuntu.png)

Nâng cấp chỉ 1 package

- sudo apt install --only-upgrade <package_name>

Chúng ta có thể kết hợp cả 2 command apt update và upgrade để nâng cấp toàn bộ package trên hệ thống

- sudo apt update && sudo apt upgrade -y

Chú ý: Tham số -y để tự động đồng ý nâng cấp

### Cài đặt mới package

Để cài đặt mới 1 package chúng ta sử dụng lệnh **apt install**

- sudo apt install <package_name>

![img](unbutu.assets/APT-install-package-Linux-Command-Ubuntu.png)

Mặc định lệnh trên sẽ cài đặt với version mới nhất, còn nếu muốn cài đặt 1 package với 1 version cụ thể thì chúng ta làm như sau:

- sudo apt install <package_name>=<version_number>

Cài đăt nhiều package cho 1 lần

- sudo apt install <package_1> <package_2>

### Gỡ bỏ package

Để gỡ bỏ 1 package trên Ubuntu, sử dụng lệnh **apt remove**

- sudo apt remove <package_name>

![img](unbutu.assets/APT-remove-package-Linux-Command-Ubuntu.png)

Với lệnh apt remove thì hệ thống chỉ gỡ bỏ binary package, chứ ko xóa bỏ các file configs.

Vì vậy muốn gỡ bỏ hoàn toàn sạch sẽ 1 package, chúng ta sử dụng lệnh **apt purge**

- sudo apt purge <package_name>

![img](unbutu.assets/APT-purge-Linux-Command-Ubuntu.png)

### Ngoài ra còn các command hữu ích như:

Tìm kiếm package

- sudo apt search <package_name>

Hiển thị chi tiết thông tin 1 package

- sudo apt show <package_name>

![img](unbutu.assets/APT-show-package-information-Linux-Command-Ubuntu.png)

Liệt kê danh sách các pakage đã cài đặt

- apt list --installed

Dọn dẹp các package của hệ thống

- sudo apt autoremove

# Kiểm tra và thay đổi version mặc định của Java trong Linux

https://vinasupport.com/kiem-tra-va-thay-doi-version-mac-dinh-cua-java-trong-linux/

## Kiểm tra version của Java trên Linux

Để kiểm tra version của Java trên Linux các bạn sử dụng command sau:

- java -version

Kết quả các bạn sẽ được như hình bên dưới:

![img](unbutu.assets/Kiem-Tra-Version-Cua-Java-Ubuntu.png)

## Thay đổi Version mặc định của Java trên Linux

Để thay đổi version của Java trên Linux các bạn sử dụng command sau:

- sudo update-alternatives --config java

Câu lệnh trên sẽ liệt kê tất cả version của Java trên máy Linux của bạn, các bạn chọn phiên bản mặc định bằng cách gõ số tương ứng với phiên bản Java muốn sử dụng như hình bên dưới.

![img](unbutu.assets/Thay-Doi-Version-Cua-Java-Ubuntu.png)

Kết quả sau khi thay đổi version của Java: Phiên bản Java đã được hạ xuống sử dụng Java OpenJDK 1.8 thay cho bản Java OpenJDK 1.11

![img](unbutu.assets/Ket-Qua-Sau-Khi-Thay-Doi-Version-Java.png)

Vì mỗi 1 chương trình chạy trên Java thì chỉ chạy được trên 1 phiên bản Java nhất định, nên bài viết này hy vọng sẽ giúp ích cho các bạn trong [lập trình Java](https://vinasupport.com/tag/lap-trinh-java/)



# Chmod là gì? Hướng dẫn sử dụng lệnh chmod trên Linux/Unix

https://vinasupport.com/chmod-la-gi-huong-dan-su-dung-lenh-chmod-tren-linux-unix/

## Chmod là gì? Giới thiệu về lệnh chmod

Trong hệ điều hành Unix/Linux, chmod là lệnh được sử dụng để thay đổi [quyền truy cập](https://vinasupport.com/tag/phan-quyen-tren-linux/) của người dùng tới file/folder.

**Cú pháp lệnh chmod (Syntax):**

```
chmod [options] mode [mode] file1 file2 file3 ....
```

**Danh sách các option:** 

- -R: Recursive, áp dụng cho tất cả các file và folder bên trong
- -f: force, set quyền trong cả trường hợp xảy ra lỗi
- -v: verbose, hiển thị đối tượng đã xử lý

Nếu là một symbolic link thì đối tượng đích sẽ bị ảnh hưởng.

**Danh sách các mode:** 

| #    | Permission              | rwx  |
| :--- | :---------------------- | :--- |
| 7    | read, write and execute | rwx  |
| 6    | read and write          | rw-  |
| 5    | read and execute        | r-x  |
| 4    | read only               | r–   |
| 3    | write and execute       | -wx  |
| 2    | write only              | -w-  |
| 1    | execute only            | –x   |
| 0    | none                    | —    |

**VD:** Trường hợp mode = 777 (Kiểu chữ số)

- Với file => -rwxrwxrwx
- Với folder => drwxrwxrwx

– Từ bên phải sang ký tự đầu tiên là dấu gạch ngang [**–**] thì là file, chữ [***\*d\****] thì là folder
– 3 ký tự tiếp theo tương ứng là quyền đọc, ghi, thực thi của Owner (Người tạo file/folder)
– 3 ký tự tiếp theo nữa tương ứng là quyền đọc, ghi, thực thi của Owner Group (Group của người tạo file/folder)
– 3 kỳ tự cuối cùng tương ứng là quyền đọc, ghi, thực thi của EveryOne (Tất cả các user còn lại)

![img](unbutu.assets/chmod-mode.png)

## Hướng dẫn sử dụng chmod trên Linux

– Kiểm tra quyền của file/folder

- ls -l /duong-dan-file-hoac-folder

![img](unbutu.assets/Kiem-Tra-Quyen-Chmod-File-Folder.png)

Như ảnh trên thì quyền của file **RubyMine-2018.1.4.tar.gz** là -rw-rw-r– (664)

– Phân quyền cho file/folder

- chmod 644 /duong-dan-file-hoac-folder

![img](unbutu.assets/Phan-Quyen-Chmod-Cho-File-Folder-e1530630345966.png)

Kết quả thì quyền trên file **RubyMine-2018.1.4.tar.gz** đã được thay đổi là -rw-r–r– (644)

– Phân quyền cho folder và các file, thư mục bên trong của nó. (Thêm tham số -R)

- chmod -R 644 /duong-dan-folder

– Để folder có thể mở được thì folder cần quyền thực thi, ta có thể thêm quyền thực thì bằng cách cộng mode x

- chmod +x /duong-dan-folder

Tương tự ta có thể +r, +w để thêm quyền đọc, ghi.

– Thay đổi quyền của file trong 1 folder

- find /opt/lampp/htdocs -type f -exec chmod 644 {} \;

– Thay đổi quyền chỉ folder và các folder con trong nó.

- find /opt/lampp/htdocs -type d -exec chmod 755 {} \;

# Cách giải nén một số định dạng file phổ biến trong Linux

https://vinasupport.com/cach-giai-nen-mot-so-dinh-dang-file-pho-bien-trong-linux/

### 1. Giải nén file .tar ( TarBall File )

– **Để giải nén file .tar**

- tar -xvf file.tar

Để giảm dung lương lưu trữ và băng thông khi truyền tải qua mạng Internet, thì thường sẽ sử dụng các chương trình như gzip hoặc bzip2 để nén file TarBall tạo ra file có định dạng là tar.gz và tar.bz2. Để giải nén 2 loại file này sử dụng command sau:

**– Để giải nén file .tar.gz**

- tar -xzvf file.tar.gz

**– Để giải nén file .tar.bz2**

- tar -xjvf file.tar.bz2

Giải thích các tham số:

- -x: Giải nén TarBall file
- -v: Hiển thị nội dung giải nén
- -f: Chỉ định tên file
- -j: Giải nén tệp nén được tạo bởi chương trình bzip2 (phần mở rộng tar.bz2).
- -z: Giải nén tệp nén được tạo bởi chương trình gzip (phần mở rộng tar.gz).

### 2. Giải nén file .zip

Zip là 1 định dạng phổ biến trên cả 2 hệ điều hành Windows và Linux, để giải nén định dạng .zip trên Linux các bạn cần chương trình giải nén có tên là **unzip**.

– Cài đặt chương trình **unzip** trên Linux

- *# For Ubuntu, Debian*
- sudo apt-get update
- sudo apt-get install unzip
- 
- *# For Centos, Redhat, ...*
- sudo yum install unzip

– Giải nén file .zip

- unzip file.zip

### 3. Giải nén file .rar

Tương tự file .zip, để giải nén định dạng .rar trên Linux các bạn cần chương trình giải nén có tên là unrar

– Cài đặt chương trinh **unrar** trên Linux

- *# For Ubuntu, Debian*
- sudo apt-get update
- sudo apt-get install unrar
- 
- *# For Centos, Redhat, ...*
- sudo yum install unrar

– Giải nén file .rar

- unrar file.rar

### 4. Giải nén file .tgz

Để giải nén file .tgz, các bạn sử dụng command sau:

- tar -xvzf file.tgz

### 5. Giải nén file .gz

- gunzip file.gz

### 6. Giải nén file .bz2

- bunzip2 file.bz2

### 7. Giải nén file .tbz2

- tar -jxvf file.tbz2

## Are you getting permission denied error message while removing directories?

Only owners can delete their directories. However, a sysadmin can delete any directories created by anyone on the system. The syntax is:

```shell
sudo rmdir /path/to/dir/
sudo rm -rf dir2
```

https://www.cyberciti.biz/faq/delete-or-remove-a-directory-linux-command/

# Ubuntu Linux Install vim Text Editor using apt-get

https://www.cyberciti.biz/faq/howto-install-vim-on-ubuntu-linux/

## Ubuntu Linux install vim using apt

The procedure is as follows:

1. Open terminal application. You can also press CTRL+ALT+T keyboard shortcut
2. Update package database by typing the **sudo apt update** command
3. Search for vim packages run: **sudo apt search vim**
4. Install vim on Ubuntu Linux, type: **sudo apt install vim**
5. Verify vim installation by typing the **vim --version** command

Let us see all steps in details to install vim on Ubuntu system.

## How to install full version of Vim on Ubuntu

First open the terminal application and then update package database using the [apt command](https://www.cyberciti.biz/faq/ubuntu-lts-debian-linux-apt-command-examples/) or [apt-get command](https://www.cyberciti.biz/tips/linux-debian-package-management-cheat-sheet.html):
`sudo apt update`

```
Hit:1 http://us-central1.gce.archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://us-central1.gce.archive.ubuntu.com/ubuntu focal-updates InRelease             
Hit:3 http://us-central1.gce.archive.ubuntu.com/ubuntu focal-backports InRelease           
Hit:4 http://security.ubuntu.com/ubuntu focal-security InRelease                           
Hit:5 http://archive.canonical.com/ubuntu focal InRelease                                  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```

[Apply all patches on Ubuntu Linux](https://www.cyberciti.biz/faq/how-do-i-update-ubuntu-linux-softwares/):
`sudo apt upgrade`

### Search for vim package

Run any one of the following command:
`sudo apt search vimsudo apt-cache search vimsudo apt-cache search vim | grep editor`

```
vim - Vi IMproved - enhanced vi editor
vim-tiny - Vi IMproved - enhanced vi editor - compact version
....
```

You don’t have to install above vim packages. Typically we eiter install vim or vim-tiny on Ubuntu Linux.

### Get info about vim package of your choice

Use the apt as follows:
`apt show vim-tinyapt show vim`

```
Package: vim
Version: 2:8.1.2269-1ubuntu5
Priority: optional
Section: editors
....
```

### Installing vim text editor on Ubuntu

Open a terminal and/or login to the remote Ubuntu server using the ssh client. Type the following apt-get command to install vim text editor (when promoted type your own password):
`sudo apt-get updatesudo apt-get install vim`
OR
`sudo -ssudo apt-get updateapt-get install vim`  

### How do I edit file with vim

You can now use vim text editor:
`$ vi file.c$ vim file.c$ sudo vim /etc/sysctl.conf`



# Others

https://vinasupport.com/huong-dan-khoi-phuc-file-bi-xoa-tren-linux-unix/

https://vinasupport.com/tao-shortcut-icon-de-chay-ung-dung-tren-ubuntu-desktop/

https://vinasupport.com/cach-kiem-tra-thong-tin-cua-he-dieu-hanh-linux-unix/

https://vinasupport.com/dat-ngay-gio-tren-linux-server-su-dung-command-line/

https://vinasupport.com/huong-dan-cai-dat-python-3-va-pip-3-tren-ubuntu-linux/

https://vinasupport.com/postgresql-tools-huong-dan-cai-dat-pgadmin-4-tren-linux/

https://vinasupport.com/cai-dat-moi-truong-ao-virtualenv-cho-python/

https://vinasupport.com/huong-dan-cai-dat-apache-maven-tren-ubuntu/

https://vinasupport.com/huong-dan-cai-dat-apache-tomcat-8-tren-may-chu-ubuntu/

https://vinasupport.com/tim-va-thay-the-ky-tu-trong-mot-file-su-dung-sed-linux-command-linux/



https://www.omgubuntu.co.uk/2019/09/ubuntu-19-10-default-wallpaper-download

Git

https://linuxize.com/post/how-to-install-git-on-ubuntu-18-04/

---