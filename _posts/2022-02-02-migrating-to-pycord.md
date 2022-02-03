### Migrating to the Pycord Discord API

I have a discord [bot](https://github.com/Soulsender/scarabbot) that is my favourite python project I've done. I run it persistantly through Replit which is a cloud-based IDE. My bot which I named Scarab (because it sounds cool mostly) uses the outdated and unsupported [discord.py](https://github.com/Rapptz/discord.py) python API wrapper. I've been meaning to switch to a new and up-to-date API wrapper, so I chose [Pycord](https://github.com/Pycord-Development/pycord).

### A Quick Brief of Discord.py
Discord.py was the main API wrapper used by most discord bot developers. It had the most support and a team of 270 people. Unfortunately, the owner Rapptz, [was not able to continue the project](https://gist.github.com/Rapptz/4a2f62751b9600a31a0d3c78100287f1) due to the time needed to maintain it. This caused the project to stop, and become archived on GitHub. 
<br />
Due to the closing of discord.py, there was a new contender for the discord python API wrapper spot. Many projects came along that mimiked the syntax of discord.py, and some projects (which had been maintained before the archiving) became more widely used like [Hikari](https://github.com/hikari-py/hikari). After the dust cleared, Pycord was a very good choice.

### Why Did I Choose Pycord?
I chose Pycord because it uses the same syntax that discord.py uses, which means I would not have to port all the code over and effectively re-write it. Pycord also seems to have the most active support and most users out of any of the other options. 

### Problems While Trying to Install
Pycord used the same package name as discord.py which was simply `discord`. This meant that you could port over your project very easily and have it running the updated Pycord and not discord.py. I was using Replit for my bot due to it's free hosting abilities. You could have persistant code running and have an upkeep with a server pinger like [UptimeRobot](https://uptimerobot.com/). Repl.it uses a package named Poetry for it's dependacies instead of the classic `requirements.txt`. Poetry is great and overall it makes less problems in getting dependacies. 
<br />
Replit being the user-friendly cloud IDE that it is, was confused when I tried to get it to install Pycord. Looking through the configuration file though, I was able to change the line installing discord.py to pycord. Once again, I ran the code... and it still didn't work. I then learned that I was supposed to run a command that added it to the config as well.
```
poetry add pycord
```
This worked, but I still wanted to make sure it worked client-side as I like to edit the code on my local machine and then upload it to Replit. I installed Poetry via a simple: (I was running Linux, not Windows)
```
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python3 -
poetry install --no-root
```
I was expecting it to work then. **Plot twist: it did not work**. I learned that I needed to initalize Poetry. I did with 
```
poetry install
```
And it STILL did not want to cooperate. After looking around and discussing with one of my friends that knows more about Poetry than I do, we discovered that the reason was because Poetry was not bound in my $PATH. I added the command:
```
export PATH="$PATH:/home/$USER/.poetry/bin"
```
to the end of my `.bashrc` file. This file is loaded whenever you launch a bash shell/terminal/command prompt. Now, this command will automatically be ran whenever I open a new session, and Poetry will be initalized and ready to go at a moment's notice!
