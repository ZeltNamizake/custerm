# Custerm
Customize Termux with Neofetch and Starship
<div align="center">
  <p>
    <img src="https://i.ibb.co/xqmgg4QM/Screenshot-20250503-003552-Termux.jpg" alt="terminal-termux" border="0"/>
  </p>
</div>

### What is needed?
 * __[starship](https://starship.rs/)__ to customize the termux prompt
 * __wget__ to download font nerdfont
 * __p7zip__ to extract archive font
 * __neofetch__ to print device info
 * __font custom__ to support icon
 * __zsh__ (optional)

### Install the required
 * Install Packages
```bash
apt install starship wget p7zip neofetch -y
```
 * Download and install font "Hack"
```bash
mkdir HackFont && cd HackFont && wget https://github.com/ryanoasis/nerd-fonts/releases/download/v3.4.0/Hack.zip && 7z x Hack.zip && mkdir ~/.termux && cp HackNerdFont-Regular.ttf ~/.termux/font.ttf
```
*if the Termux application suddenly exits, reopen it*

### Configure Shell
 * if you want to set the terminal using __zsh__
 ```bash
cd $PREFIX/bin && chsh -s zsh
 ```
 * __Configure bashrc or zshrc__
   <br>create the file bashrc or zshrc (if not yet available) 
   `touch ~/.bashrc`  or  `touch ~/.zshrc`  and fill the file like this:
   ```bash
   #bashrc
   neofetch --ascii_distro star
   eval "$(starship init bash)"
   ```
   ```bash
   #zshrc
   neofetch --ascii_distro star
   eval "$(starship init zsh)"
   ```
   
 
 * __Note:__ After configuring the shell. Restart the termux application 
 
### Configure Starship
 * Create configuration file for customization
```bash
mkdir ~/.config && touch ~/.config/starship.toml
```
 * Example of customization
```toml
#configuration staship

format = """${directory}
{character}"""

[directory]
home_symbol = "\ueb06"
style = "blue bold"
format = "[$path]($style)"
truncation_length = 2
truncation_symbol = "../"

[character]
success_symbol = "[❯](green bold)"
error_symbol = "[❯](red bold)"

```

### My adjusted results:
<div align="center">
  <p>
    <img src="https://i.ibb.co.com/m5GYpXCy/Screenshot-20250503-002239-Termux.jpg" alt="custerm-res1" border="0"/>
  </p>
  <p>
  <img src="https://i.ibb.co.com/TqbjNHf5/Screenshot-20250503-003718-Termux.jpg" alt="custerm-res2" border="0"/>
  </p>
</div>

 * __Note:__ If you use bash as a shell on the terminal, some starship modules are not supported.
 I suggest you use zsh as a terminal shell if you want to customize more widely but if you still 
 want to use bash as a terminal shell, you can see my configuration file __~/starship.toml__

###### `Created by Driyas (ZeltNamizake)`
