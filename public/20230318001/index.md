# 重新折腾服务器


服务器用Archlinux有段时间了，感觉还不错。所以把另外一个服务器重新折腾了一下。

1. 有些服务器自带的系统是没有Archlinux的，要先装Ubuntu然后转换为Archlinux。

   ```shell
   wget https://felixc.at/vps2arch
   chmod +x vps2arch
   ./vps2arch


2. 安装zsh：

   `pacman -S zsh`

3. 更改默认SHELL：

   `chsh -s $(which zsh)`

4. 安装neovim：

   `pacman -S neovim`

5. 安装zimfw：

   `curl -fsSL https://raw.githubusercontent.com/zimfw/install/master/install.zsh | zsh`

6. 安装git：

   `pacman -S git`

7. 克隆自己的相关配置：

   `git clone https://github.com/gudk/zsh_config.git`

8. 切换到zsh后，复制相关文件：

   ```shell
   cp .zshrc ~/
   cp .zimrc ~/
   cp .p10k.zsh ~/
   cp .gitconfig ~/
   source ~/.zshrc
   ```

9. 基本配置完成，重新登录一下就能看到效果了。

10. 然后 Arch Linux下面没有crontab，要自己安装一个cronie程序。安装完docker、nginx等都要systemctl start一下，设置hostname用hostnamectl set-hostname命令。

11. ssh相关配置可以用sftp上传，这样下次登录就不用输入帐号密码了。

12. hugo相关命令：hugo server -e production --liveReloadPort 443 --baseURL "https://xxx.xx"，有个注意点，hugo的主题是submodule模式提供的，要先git submodule init;git submodule update。

