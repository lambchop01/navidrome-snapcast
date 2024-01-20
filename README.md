# navidrome-snapcast
Navidrome and snapcast configured in Docker


This is just what is working on my server... I give no guarantees it will work on yours!  Also please forgive my poor coding skills, I'm a self taught noob :)

This uses the jukebox mode in navidrome (currently only available via the subsonic api)

### Navidrome Container:
I created Dockerfile.navidrome to add mpd, alsa to the docker image then installed navidrome from the releases page.
I added my asound.conf to pipe audio to /tmp/snapfifo inside the container so that snapcast can pick it up.  and shared /tmp with the snapserver via a volume
I also edited and added navidrome.toml directly to the container rather than giving the option to use env vairables in the compose file.
I don't know if it is nessecary or not, but while playing with alsa trying to get it to work I gave the container access to /dev/snd and groupadd 29 so that it had permission to access it.

### Snapserver Container:
I started out using [jaedb's iris/snapcast setup](https://github.com/jaedb/Iris), so the snapserver container is still his...  Just edited the snapserver.conf file to put my streams into it.

From there set up your snapclients as you see fit. to test you can just use the web page @ server-ip:1780
