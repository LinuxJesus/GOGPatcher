Some Games will NOT start unless you add these libraries. To get these games to start you need to copy LinuxLibraries(Uncompressed Folder) to your Documents Folder. 


Then, if your game is a GOG Game you can:
1. Add this line to the start.sh script located in the GOG GAMES/GAMENAME directory:
```
export LD_LIBRARY_PATH=/home/$USER/Documents/LinuxLibraries/i386:/home/$USER/Documents/LinuxLibraries/x86_64
```

If your game is some random executable(argh!) then you can just run the above command and then run the executable.


# Why?
Because GOG doesnt take very good care for their linux game releases. So a lot of them are broken on install.
