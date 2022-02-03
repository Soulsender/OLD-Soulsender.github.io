### Migrating to the Pycord Discord API

I have a discord [bot](https://github.com/Soulsender/scarabbot) that is my favourite python project I've done. I run it persistantly through Repl.it which is a cloud-based IDE. My bot which I named Scarab (because it sounds cool mostly) uses the outdated and unsupported [discord.py](https://github.com/Rapptz/discord.py) python API wrapper. I've been meaning to switch to a new and up-to-date API wrapper, so I chose [Pycord](https://github.com/Pycord-Development/pycord).

### A Quick Brief of Discord.py
Discord.py was the main API wrapper used by most discord bot developers. It had the most support and a team of 270 people. Unfortunately, the owner Rapptz, [was not able to continue the project](https://gist.github.com/Rapptz/4a2f62751b9600a31a0d3c78100287f1) due to the time needed to maintain it. This caused the project to stop, and become archived on GitHub. Due to the closing of discord.py, there was a new contender for the discord python API wrapper spot. Many projects came along that mimiked the syntax of discord.py, and some projects (which had been maintained before the archiving) became more widely used like [Hikari](https://github.com/hikari-py/hikari). After the dust cleared, Pycord was a very good choice.

### Why Did I Choose Pycord?
I chose Pycord because it uses the same syntax that discord.py uses, which means I would not have to port all the code over and effectively re-write it. Pycord also seems to have the most active support and most users out of any of the other options. 

### Problems While Trying to Install
Pycord used the same package name as discord.py which was simply `discord`. This meant that you could port over your project very easily and have it running the updated Pycord and not discord.py. I was using Repl.it for my bot due to it's free hosting abilities. You could have persistant code running and have an upkeep with a server pinger like [UptimeRobot](https://uptimerobot.com/).
