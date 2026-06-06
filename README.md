i3-wm - My tiling i3 configuration for Debian
================================================================

### Screenshot:

![i3](/examples/i3.png)

### Installation:

  * **`Install dependencies:`**
  
    * Install the packages necessary for i3 to function properly:

      ```shell
      sudo apt install i3 i3lock arandr i3status nitrogen diodon dmenu lxappearance atril bash vim \
      simplescreenrecorder xfce4-screenshooter python3 python3-tk python3-psutil pulseaudio-utils wget \
      pipewire pipewire-pulse slurp xterm alacritty kitty xscreensaver xautolock coreutils picom unzip \
      x11-xserver-utils lxrandr ristretto grim arc-theme papirus-icon-theme adwaita-icon-theme mpv curl \
      adwaita-qt6 adwaita-qt qt5ct qt6ct rofi keepassxc wmctrl conky-all compton pcmanfm jq dex dunst \
      geany xarchiver iwd fonts-noto fonts-noto-core fonts-noto-extra fonts-noto-mono procps git zenity \
      xdg-desktop-portal-gtk xdg-desktop-portal xorg xserver-xorg fonts-liberation psmisc terminator \
      brightnessctl iw wpasupplicant upower
      ````

      ```shell
      curl -L "https://gs.yougeek.dev/i3-wm/scripts/update-firefox.sh" | sudo bash
      curl -L "https://gs.yougeek.dev/i3-wm/scripts/update-telegram.sh" | sudo bash
      curl -L "https://gs.yougeek.dev/i3-wm/scripts/update-electronmail.sh" | sudo bash
      curl -L "https://gs.yougeek.dev/i3-wm/packages/vim-conf-onedark.sh" | sudo bash
      curl -L "https://gs.yougeek.dev/i3-wm/packages/um-nerd-fonts.tar.gz" | sudo tar -zxvf - -C /
      curl -L "https://gs.yougeek.dev/i3-wm/packages/iwd-connectd.tar.gz" | sudo tar -zxvf - -C /
      sudo systemctl daemon-reload
      ````
 
  * **`Install configuration (dotfiles):`**
  
    * Clone repository and copy files to your home:

      ```shell
      git clone https://github.com/dmesg00/i3-wm
      cd i3-wm
      cp -rf .config ~/
      cp -rf wallpapers ~/
      cp -rf scripts ~/
      echo "export QT_QPA_PLATFORMTHEME=qt5ct" >> ~/.bashrc
      ````

### Configuration:

  * **`Network (Optional):`**
  
    * By default, I use `iwd` as my network manager via the `iwd-connectd` script. Alternative using [interfaces](https://github.com/dmesg00/i3-wm/blob/master/.config/network/interfaces) file.
    * To modify the configuration, you must edit the file `/usr/bin/iwd-connectd-cfg` with root:
    
      ```shell
      interface="wlan0"
      wireless="yes" # Change to "no" for ethernet
      wireless_ssid="miwifiname"
      wireless_pass="passwordwifi"
      ip_interface="192.168.0.100/24"
      gw_interface="192.168.0.1"
      dns_one="1.1.1.1"
      dns_two="1.1.0.0"
      ````

    * After modifying the configuration, restart the service:

      ```shell
      $ sudo systemctl enable iwd-connectd
      $ sudo systemctl restart iwd-connectd
      ````

  * **`Monitor & resolution:`**
  
    * The configuration load my monitor configuration:
    * Use the command `xrandr` or `lxrandr` for show your config & edit the file `~/.config/i3/startxrandr.sh`:
    
      ```shell
      xrandr --output HDMI-A-0 --mode 1920x1080 -r 74.97
      xrandr --output HDMI-A-1 --mode 1280x1024 -r 75.02 --rotate left --right-of HDMI-A-0
      ````

  * **`Screensaver:`**
  
    * The configuration file set the time in 20 minutes:
    * Edit the file `~/.config/i3/startscreensaver.sh`:
    
      ```shell
      # Basic configuration variables
      ScreensaverProgram="xautolock" # Options: xautolock or xscreensaver
      ScreensaverTime="20" # 20 minutes (only for xautolock)
      ````

 * **`Wallpaper:`**
  
    * By default, the config load wallpaper on `~/wallpapers/awesome.jpg`:
    * Edit  `~/.config/i3/config` for set your favorite wallpaper:
    
      ```shell
      exec --no-startup-id "sleep 3 && nitrogen --head=0 --set-scaled ~/wallpapers/awesome.jpg"
      ````

 * **`Tray:`**
  
    * By default, the config set tray on monitor `HDMI-A-1`:
    * Edit  `~/.config/i3/config` for set your output monitor:
    
      ```shell
      tray_output HDMI-A-0
      ````

  * **`Layout:`**
  
    * By default, the config load my spanish layout.:
    * Edit  `~/.config/i3/config` for set your configuration:
    
      ```shell
      # Input layout
      #exec --no-startup-id setxkbmap us 
      exec --no-startup-id setxkbmap es  
      ````

### Keys configuration:

My list of extra combinations:

    - Super + d = Open Dmenu (fbrun mode)
    - Super + p = Open Dmenu (run mode)
    - Super + q = Open Dmenu (window mode)
    - Super + o = Open Dmenu (drun mode)
    - Super + b = Open Firefox
    - Super + n = Open PCManFM
    - Super + t = Open Xfce4-Screenshoot
    - Super + g = Open Geany
    - Super + m = Open Telegram 
    - Super + z = Open Simplescreenrecorder
    - Super + x = Open LXRandr
    - Super + u = Open Xterm
    - Super + i = Open LXAppearance
    - Super + c = Open Diodon
    - Super + Shift + c = Caffeine Mode
    - Super + Shift + x = Display Tools
    - Volume-Up = Volume +5
    - Volume-Down = Volume -5
    - VolumeMute = Mute Volume
    - Super + Ctrl + Shift + l = Screen Off/On
    - Super + Shift + e = Logout
    - Super + Backspace = Menu Logout
