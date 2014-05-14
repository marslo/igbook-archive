- Get Package name by command
    <pre><code>[marslo@MJ ~]
    $ apt-cache search mkpasswd
    whois - intelligent WHOIS client
    libstring-mkpasswd-perl - Perl module implementing a random password generator
    </code></pre>

- Search package name for apt-get
    <pre><code>[marslo@MJ ~]
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
    </code></pre>

- Install Ubuntu Theme
    <pre><code>$ sudo add-apt-repository ppa:noobslab/themessudo
    $ sudo apt-get update
    $ sudo apt-get install nokto-theme
    </code></pre>

- Open Font Viewer and install font
    <pre><code>┌─ (root@MarsloJiao ~) ->
    └─ # gnome-font-viewer ~/Tools/Monaco/Monaco_Linux.TTF
    </code></pre>

- Show launcher icon
    <pre><code>┌─ (marslo@MarsloJiao ~/Desktop) ->
    └─ $ gsettings get com.canonical.Unity.Launcher favorites
    ['application://nautilus.desktop', 'application://gnome-terminal.desktop', 'application://firefox.desktop', 'unity://running-apps', 'application://gvim.desktop', 'unity://desktop-icon', 'unity://expo-icon', 'unity://devices']
    </code></pre>

- Show the softer renderer
    <pre><code>┌─ (marslo@MarsloJiao ~/Desktop) ->
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
    </code></pre>

- Specified Context Menu
    <pre><code>┌─ (marslo@MarsloJiao ~/Desktop) ->
    └─ $ sudo apt-get install nautilus-actions
    ┌─ (marslo@MarsloJiao ~/Desktop) ->
    └─ $ nautilus -q
    ┌─ (marslo@MarsloJiao ~/Desktop) ->
    └─ $ utilus-actions-config-tool
    </code></pre>


