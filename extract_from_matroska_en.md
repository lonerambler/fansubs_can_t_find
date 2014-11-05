How to extract the subtitles from a Matroska video file * English version *
===========================================================================

Assuming that you are using Linux, depending on your distribution, first you need to install the mkvtoolnix package.

For example, in Debian based distributions it would be something like...

sudo apt-get install mkvtoolnix

After that, all you need to know is which track within the matroska file contains the subtitles.

mkvinfo /path/to/your/video/file.mkv

From the output, which can be long or short depending on the embedded information in the video, look for a line or set of lines like the following ones.

| + A track
|  + Track number: 3
|  + Track UID: 1581319848
|  + Track type: subtitles
|  + Lacing flag: 0
|  + Codec ID: S_TEXT/ASS
|  + CodecPrivate, length 15885
|  + Name: English subtitles

Note particularly, the track number and the de ID, in this example, this says that track 3 contains an Advanced SubStation Alpha set of subtitles, therefore, the subtitles file extension would be .ass

For the actual extraction, you just need to remember such track number, something like this...

mkvextract tracks /path/to/your/video/file.mkv 3:/path/to/your/subtitles/file.ass

And that is it.
