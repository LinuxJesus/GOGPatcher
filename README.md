Some Games will NOT start unless you add these libraries. To get these games to start you need to copy LinuxLibraries(Uncompressed Folder) to your Documents Folder. 


Then, if your game is a GOG Game you can:
1. Add this line to the start.sh script located in the GOG GAMES/GAMENAME directory:

export LD_LIBRARY_PATH=/home/$USER/Documents/LinuxLibraries/i386:/home/$USER/Documents/LinuxLibraries/x86_64


If your game is some random executable(argh!) then you can just run the above command and then run the executable.






### EXAMPLE start.sh File ###

#!/bin/bash
# GOG.com (www.gog.com)
# SW
export LD_LIBRARY_PATH=/home/$USER/Documents/LinuxLibraries/i386:/home/$USER/Documents/LinuxLibraries/x86_64
# Initialization
CURRENT_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"
cd "${CURRENT_DIR}"
source support/gog_com.shlib

# Game info
GAME_NAME="$(get_gameinfo 1)"
VERSION="$(get_gameinfo 2)"
VERSION_DEV="$(get_gameinfo 3)"

# Actions
run_game() {
 echo "Running ${GAME_NAME}"
 cd game
 ./"sw"
}

default() {
  run_game
}

# Options
define_option "-s" "--start" "start ${GAME_NAME}" "run_game" "$@"

# Defaults
standard_options "$@"
