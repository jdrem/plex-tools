https://stackoverflow.com/questions/30305953/is-there-an-elegant-way-to-split-a-file-by-chapter-using-ffmpeg

How to extract part of a file by time using ffmpeg:
```bash
ffmpeg -i LOONEY\ TUNES\ GOLDEN\ COLLECTION\ DISC\ 3-C1_t00.mp4 -ss 01:20:49 -to 01:27:49 -c copy "Looney Tunes - S1953E01 - Don't Give Up the Sheep.mp4"
```

How to split a mp4 by chapters:

```bash
ffmpeg -i "$SOURCE.$EXT" 2>&1 |
grep '^\s*Chapter' |
sed -E "s/ *Chapter #([0-9]+\.[0-9]+): start ([0-9]+\.[0-9]+), end ([0-9]+\.[0-9]+)/-i \"$SOURCE.$EXT\" -vcodec copy -acodec copy -ss \2 -to \3 \"$SOURCE-\1.$EXT\"/" |
xargs -n 11 ffmpeg
```


https://mkvtoolnix.download/downloads.html#fedora

 sudo rpm -Uhv https://mkvtoolnix.download/fedora/bunkus-org-repo-2-4.noarch.rpm 
 sudo dnf install mkvtoolnix mkvtoolnix-gui 

```
mkvmerge -o output.mkv --split chapters:all input.mkv
```
