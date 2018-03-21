# Olympic Ripper

This is a small script to help rip Olympic events from olympicchannel.com

## UPDATE

Thanks to /u/berryh on reddit for writing a script that got all the m3u8 playlist urls and names from the site. That combined with youtube-dl made my whole script obsolete. If you have youtube-dl installed, you can just run the oly-fetch script and all the videos will be downloaded. Warning though, they are 1080p 30fps so each video is around 4gb, which is going to add up.

## Getting Started

No need to clone the whole repo for one script. Just a quick:
```
wget https://raw.githubusercontent.com/Mr-Schneider/Olympics-Ripper/master/oly-ripper
```

### Prerequisites

The only things needed are wget and ffmpeg. If you do not already have ffmpeg it is any easy install from any linux distribution.

```
sudp apt-get install ffmpeg
```
```
sudo yum install ffmpeg
```

### Usage

There are only two arguments needed, the name of the event and a .ts link. We will describe both here.

```
./oly-ripper <name> <link>
```

If you want to get multiple videos at once, you can compile a list of events in a file with the format <name> <url>:
```
Mens-Hockey-Gold https://vod.olympicchannel.com/NBCR_Production_-_OCS/399/888/GCDG-PYREPL18S09E030-_E17101101_master_stream_1024_xa16f9030227d4dcd9c3d7eae1848677e_00008.ts
Opening-Ceremony https://vod.olympicchannel.com/NBCR_Production_-_OCS/906/448/GCDG-PYREPL18S04E001-_E17101101_master_stream_1024_x91f7e479b9a040249130434abab76df6_00014.ts
```
Be sure to make sure the name does not have any spaces. You can pass the file to the script with an -i flag.
```
./oly-ripper -i <file name>
```
Once a video is completed the line in the file will be commented out (be sure to have have duplicate names). This lets you add links to the file and re-run the script without having to worry about getting videos twice.

The name given will be what the final .mp4 file will be named.

### Finding Links

The link is a link to a .ts file. The way olympicchannel.com streams there media is with FL Player. There used to be ways to find a whole .mp4 link to download, but that no longer works. Follow the instructions bellow to get the .ts link for the event you want to download.

First go to [Winter Olympics](https://www.olympicchannel.com/en/events/pyeongchang-2018/) section of the website. After finding the video you want to download, start to view it in your browser. Right click and select 'Inspect Element' to bring up information about your current page.

![inspect element image](https://i.imgur.com/4PAtyyN.gif)

Now, Navigate to the 'Network' tab. Select 'Media' to reduce what you see to media elements. We are looking for 'mp2t' type files. Select one, but be careful, try and make sure the video you are currently watching is good quality, and try and select a recent file. When the streams start out they start at 480p, we want to be sure we get a link for a 720p video. Now on the right a dialog box will appear. Select the headers tab and the URL we want is listed next to 'Request URL'.

![finding link image](https://i.imgur.com/zkCAbTK.gif)

Make sure it has five numbers followed by '.ts'. Here is an example of a correct link:
```
https://vod.olympicchannel.com/NBCR_Production_-_OCS/906/448/GCDG-PYREPL18S04E001-_E17101101_master_stream_1024_x91f7e479b9a040249130434abab76df6_00014.ts
```
Once you have the link, simply pass it to the script.
