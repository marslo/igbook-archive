### Get Package name by command
    [marslo@MJ ~]
    $ apt-cache search mkpasswd
    whois - intelligent WHOIS client
    libstring-mkpasswd-perl - Perl module implementing a random password generator

### Search package name for apt-get
    [marslo@MJ ~]
    $ sudo apt-cache search chrome browser
    chromium-browser - Chromium browser
    chromium-chromedriver - WebDriver driver for the Chromium Browser
    cloudprint - Server for Google Cloud Print
    collabtive - Web-based project management software
    epiphany-browser - Intuitive GNOME web browser
    jsxgraph - Interactive Geometry with JavaScript
    kpartsplugin - Netscape-compatible plugin to embed KDE file-viewers into browser
    libjs-excanvas - HTML5 Canvas for Internet Explorer
    libjs-jquery-jplayer - HTML5 Audio & Video for jQuery with a Flash fallback
    libjs-jquery-jush - jQuery Syntax Highlighter
    google-chrome-beta - The web browser from Google
    google-chrome-stable - The web browser from Google
    google-chrome-unstable - The web browser from Google

### Install Ubuntu Theme
    $ sudo add-apt-repository ppa:noobslab/themes
    $ sudo apt-get update
    $ sudo apt-get install nokto-theme

### Open Font Viewer and install font
    ┌─ (root@MarsloJiao ~) ->
    └─ # gnome-font-viewer ~/Tools/Monaco/Monaco_Linux.TTF

### Show launcher icon
    ┌─ (marslo@MarsloJiao ~/Desktop) ->
    └─ $ gsettings get com.canonical.Unity.Launcher favorites
    ['application://nautilus.desktop', 'application://gnome-terminal.desktop', 'application://firefox.desktop', 'unity://running-apps', 'application://gvim.desktop', 'unity://desktop-icon', 'unity://expo-icon', 'unity://devices']

### Show the softer renderer
    ┌─ (marslo@MarsloJiao ~/Desktop) ->
    └─ $ /usr/lib/nux/unity_support_test -p
    OpenGL vendor string:   VMware, Inc.
    OpenGL renderer string: Gallium 0.4 on SVGA3D; build: RELEASE;
    OpenGL version string:  2.1 Mesa 10.1.0

    Not software rendered:    yes
    Not blacklisted:          yes
    GLX fbconfig:             yes
    GLX texture from pixmap:  yes
    GL npot or rect textures: yes
    GL vertex program:        yes
    GL fragment program:      yes
    GL vertex buffer object:  yes
    GL framebuffer object:    yes
    GL version is 1.4+:       yes

    Unity 3D supported:       yes

### Specified Context Menu
    ┌─ (marslo@MarsloJiao ~/Desktop) ->
    └─ $ sudo apt-get install nautilus-actions
    ┌─ (marslo@MarsloJiao ~/Desktop) ->
    └─ $ nautilus -q
    ┌─ (marslo@MarsloJiao ~/Desktop) ->
    └─ $ utilus-actions-config-tool

### Disable Ubuntu Desktop notification
    ┌─ (marslo@MarsloJiao ~/Desktop) ->
    └─ $ sudo chmod -x /usr/lib/notify-osd/notify-osd

### Recode activity as a GIF file (Inspired from [here](http://askubuntu.com/a/13462/92979) and [here](http://askubuntu.com/a/107735/92979))
    ┌─ (marslo@MarsloJiao ~) ->
    └─ $ sudo add-apt-repository ppa:fossfreedom/byzanz
    ┌─ (marslo@MarsloJiao ~) ->
    └─ $ sudo apt-get update && sudo apt-get install byzanz
