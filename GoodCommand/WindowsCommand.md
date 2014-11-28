### Backup PuTTy sessions

      C:> regedit /e "%userprofile%\desktop\putty-registry.reg" HKEY_CURRENT_USER\Software\Simontatham

### Launchy PuTTy session as shortcut

      C:> [PuTTy.exe] -load [SessionName]

### Backup PuTTy session

      C:> regedit /e "%userprofile%\desktop\putty-sessions.reg" HKEY_CURRENT_USER\Software\SimonTatham\PuTTY\Sessions

### Get the list of programs

      [12:26:33.40 C:\Windows\SysWOW64]
      $ wmic product get name,version
      Name                                                                     Version
      ALM-Platform Loader 11.5x                                                11.52.444.0
      Microsoft Lync Web App Plug-in                                           15.8.8308.577
      Google App Engine                                                        1.8.6.0
      Microsoft Office Professional Plus 2010                                  14.0.6029.1000
      Microsoft Office OneNote MUI (English) 2010                              14.0.6029.1000
      ...

### Set `%USERPROFILE%` as `${HOME}` for **cygwin** (Inspired from [here](http://stackoverflow.com/questions/225764/safely-change-home-directory-in-cygwin))

      [15:55:36.30 C:\]
      $ reg add HKCU\Environment /v HOME /t REG_EXPAND_SZ /d ^%USERPROFILE^%

### Remove Graphics card context menu
- Unregister igfxpph.dll

        [11:39:50.61 C:\]
        $ regsvr32 /u igfxpph.dll

- Remove register
    - Setting from regedit

          [11:47:10.20 C:\]
          $ REG DELETE "HKEY_CLASSES_ROOT\Directory\Background\shellex\ContextMenuHandlers\igfxcui" /f

    - Setting from setx

          [11:47:10.20 C:\]
          $ REG DELETE "HKEY_CLASSES_ROOT\Directory\Background\shellex\ContextMenuHandlers\igfxcui" /f

### Set Environment Variables
- Set User Varialbe

        [13:48:11.20 C:\]
        $ setx VIM_HOME C:\Marslo\MyProgramFiles\Vim\vim74\gvim.exe

- Set System Variable

        [13:48:11.20 C:\]
        $ setx /M VIM_HOME C:\Marslo\MyProgramFiles\Vim\vim74\gvim.exe

### setx problem

      [14:31:18.67 C:\]
      $ setx /M PATH %PATH%;%M2_HOME%\bin
      ERROR: Invalid syntax. Default option is not allowed more than '2' time(s).
      Type "SETX /?" for usage.

- Fix:

        [14:31:18.67 C:\]
        $ REG ADD "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Environment" /v Path /t REG_SZ /d "%path%;%M2_HOME%\bin" /f
