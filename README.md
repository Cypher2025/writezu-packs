# writezu-packs

Programs that [Writezu](https://writezu.com) downloads on request, kept here so each one stays available at
exactly the version Writezu was tested with. **Binaries and their sources only. There is no Writezu code here.**

Writezu pins every file by its SHA-256 and refuses any file that doesn't match.

## ffmpeg 9.0.2 (LGPL), Windows x64

Release: [`ffmpeg-9.0.2-lgpl`](../../releases/tag/ffmpeg-9.0.2-lgpl)

| File | SHA-256 |
|---|---|
| `ffmpeg-n9.0.2-17-g2a571b6068-win64-lgpl-9.0.zip` | `6b264b9e6019103f601d98c292bd332fd87acf1c5e941ddff4fb71760fe63432` |
| `ffmpeg-source-2a571b606854520cf89804d8030c8b328e621689.tar.gz` | `f02fc0809a13f37e3d4e1f74254d07e035a5ef01a6d91e727b915b1764d97540` |
| `BtbN-FFmpeg-Builds-scripts-6c9aec5fc9a72ec3abedd1fa84db141fa18cf52b.tar.gz` | `81da4f7c878dc0f60e6b8d0049a112e32178e20f025d468fe4e99e77b2dfe0ec` |
| `LICENSE-ffmpeg-LGPLv3.txt` | `da7eabb7bafdf7d3ae5e9f223aa5bdc1eece45ac569dc21b3b037520b4464768` |

- **What it is:** FFmpeg 9.0.2 (`n9.0.2-17-g2a571b6068`), built by [BtbN/FFmpeg-Builds](https://github.com/BtbN/FFmpeg-Builds), the LGPL Windows build from the
  [`autobuild-2026-09-30-13-08`](https://github.com/BtbN/FFmpeg-Builds/releases/tag/autobuild-2026-09-30-13-08) release.
  This copy is byte-for-byte the same file. Its SHA-256 matches both GitHub's record for that release and BtbN's own `checksums.sha256`.
  BtbN's builds are one of the two Windows builds linked from [ffmpeg.org's download page](https://ffmpeg.org/download.html).
- **Licence:** [GNU LGPL v3](LICENSE-ffmpeg-LGPLv3.txt). The build is configured with `--enable-version3` and **without** `--enable-gpl` or `--enable-nonfree`.
  It contains no GPL components: x264, x265 and vid.stab are turned off.
- **Corresponding source:**
  - FFmpeg at commit [`2a571b6068`](https://github.com/FFmpeg/FFmpeg/commit/2a571b606854520cf89804d8030c8b328e621689). The tarball is in this release.
  - BtbN's build scripts at commit [`6c9aec5f`](https://github.com/BtbN/FFmpeg-Builds/tree/6c9aec5fc9a72ec3abedd1fa84db141fa18cf52b). The tarball is in this release.
    Each library linked in (libass, FreeType, FriBidi, HarfBuzz, nv-codec-headers, AMF, oneVPL and others) is fetched by these scripts at the version given in its `scripts.d/` file.
- **What Writezu uses it for:** exporting edits, cleaning and measuring sound, captions, titles and effects.
  It encodes H.264 on the graphics card (NVENC, Quick Sync or AMF) or with Windows' own Media Foundation encoder.

FFmpeg is a trademark of Fabrice Bellard, originator of the FFmpeg project. This repository is not affiliated with the FFmpeg project or with BtbN.
