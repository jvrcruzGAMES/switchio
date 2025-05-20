# Switchio

<img src="scripts/org.player.switchfin.svg" alt="icon" height="128" width="128" align="left">

Switchio is third-party NX player for Stremio that provides a native user interface to browse and play movies and series.
<br>

**This project is in its early stages so expect bugs.**

## Screenshots

<table>
  <tbody>
    <tr>
      <th>Home</th>
      <th>Library</th>
    </tr>
    <tr>
      <td><img src="images/home.jpg" alt="Home"></td>
      <td><img src="images/library.jpg" alt="Library"></td>
    </tr>
    <tr>
      <th>Search</th>
      <th>Music</th>
    </tr>
    <tr>
      <td><img src="images/search.jpg" alt="Search"></td>
      <td><img src="images/music.jpg" alt="Music"></td>
    </tr>
    <tr>
      <th>Series</th>
      <th>Episode</th>
    </tr>
    <tr>
      <td><img src="images/series.jpg" alt="Series"></td>
      <td><img src="images/episode.jpg" alt="Episode"></td>
    </tr>
  </tbody>
</table>

## Features
- Completely native interface
- Supported media items: movies, series, seasons, episodes 
  - Direct play and transcoding
- Remote browser for Webdav/Apache/Nginx/FTP server
- Base on MPV Player
  - Container formats: mkv, mov, mp4, avi
  - Video codecs: H.264, H.265, VP8, VP9, AV1
  - Audio codecs: Opus, FLAC, MP3, AAC, AC-3, E-AC-3, TrueHD, DTS, DTS-HD
  - Subtitle codecs: SRT, VTT, SSA/ASS, DVDSUB
  - Optionally force software decoding when hardware decoding has issues.
- External drive support using [libusbhsfs](https://github.com/DarkMatterCore/libusbhsfs)

## Input mapping during playback

- A Play/Pause
- B Stop during
- Y Toggle OSD
- X Show Menu 
- R/L Seek +/-
- L Stick Button Toggle Speed Select
- R Stick Button Toggle Video Quality Select
- \+ Show video profile

## FAQ

1. Q: Subtitles didn't display?
   A: Put any ttf file at `/switch/Switchio/subfont.ttf`
2. Q: How to enable external drive on switch?
   A: Edit config file `config.json`

```json
{
  "setting": {
    "ums": true
  }
}
```

![ums](images/ums.jpg)

## TODO list

- [x] Movie view
- [x] Series detail
- [x] Search page
- [x] Websocket connection (MirrorPlay)
- [x] [danmu plugin](https://github.com/cxfksword/jellyfin-plugin-danmu) integration

## Develop

```shell
git clone https://github.com/dragonflylee/switchfin.git --recurse-submodules --shallow-submodules
```

### Building for Switch

To build for Switch, a standard development environment must first be set up. In order to do so, [refer to the Getting Started guide](https://devkitpro.org/wiki/Getting_Started).

```bash
sudo dkp-pacman -S switch-dev switch-glfw switch-libwebp switch-curl switch-libmpv
cmake -B build_switch -DPLATFORM_SWITCH=ON
make -C build_switch Switchfin.nro -j$(nproc)
# for debug
nxlink -a <YOUR IP> -p Switchfin/Switchfin.nro -s Switchfin.nro --args -d -v
```

## Thanks to

- **@xfangfang for [wiliwili](https://github.com/xfangfang/wiliwili)**
- @dragonflylee for the original [Switchfin](https://github.com/dragonflylee/switchfin)
- @devkitpro and switchbrew for [libnx](https://github.com/switchbrew/libnx)
- @natinusala and XITRIX for [borealis](https://github.com/natinusala/borealis)
- @proconsule for [nxmp](https://github.com/proconsule/nxmp)
- @averne for great work of [FFmpeg](https://github.com/averne/FFmpeg) hwaccel backend
- @averne deko3d backend of [mpv](https://github.com/averne/mpv)
