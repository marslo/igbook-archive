- Backup PuTTy sessions
    <pre><code>C:> regedit /e "%userprofile%\desktop\putty-registry.reg" HKEY_CURRENT_USER\Software\Simontatham
    </code></pre>

- Launchy PuTTy session as shortcut
    <pre><code>C:> [PuTTy.exe] -load [SessionName]
    </code></pre>

- Backup PuTTy session
    <pre><code>C:> regedit /e "%userprofile%\desktop\putty-sessions.reg" HKEY_CURRENT_USER\Software\SimonTatham\PuTTY\Sessions
    </code></pre>

- Get the list of programs
    <pre><code>[12:26:33.40 C:\Windows\SysWOW64]
    $ wmic product get name,version
    Name                                                                     Version
    ALM-Platform Loader 11.5x                                                11.52.444.0
    Microsoft Lync Web App Plug-in                                           15.8.8308.577
    Google App Engine                                                        1.8.6.0
    Microsoft Office Professional Plus 2010                                  14.0.6029.1000
    Microsoft Office OneNote MUI (English) 2010                              14.0.6029.1000
    ...
    </code></pre>
