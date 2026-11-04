# writezu-packs

Programs and models that [Writezu](https://writezu.com) downloads on request, kept here so each one stays available at
exactly the version Writezu was tested with. **Other makers' programs are here unchanged, with their sources. There is no Writezu program code here.**
The one thing made by Writezu's makers is the AI voice model in the AI voice pack (below).

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

## Intel Open Image Denoise 2.4.1, Windows x64

Release: [`oidn-2.4.1`](../../releases/tag/oidn-2.4.1)

| File | SHA-256 |
|---|---|
| `oidn-2.4.1.x64.windows.zip` | `682d94ba57525ed177d73412e0ed903f576867bd048f830a5c6f63c56b25e8b8` |
| `oidn-2.4.1.src.tar.gz` | `9c7c77ae0d57e004479cddb7aaafd405c2cc745153bed4805413c21be610e17b` |
| `LICENSE-oidn-Apache-2.0.txt` | `3ddf9be5c28fe27dad143a5dc76eea25222ad1dd68934a047064e56ed2fa40c5` |

- **What it is:** Intel's own [v2.4.1 release](https://github.com/RenderKit/oidn/releases/tag/v2.4.1), the Windows x64 build, byte-for-byte unchanged. Every program and library inside is signed by Intel Corporation.
- **Licence:** Apache 2.0. Its third-party programs and their licences are in the `third-party-programs` files in the release, which are also inside the zip.
- **What Writezu uses it for:** taking the grain out of 3D renders.

## Writezu AI voice pack 1

Release: [`ai-voice-1`](../../releases/tag/ai-voice-1)

| File | SHA-256 |
|---|---|
| `ai-voice-pack-1.zip` | `2e67620b60fa1e58a6e589953e2a73ed84ed8d83028e7401428f344246884454` |

- **What's in it:**
  - `hear.onnx`: the first layers of Microsoft's [WavLM Large](https://github.com/microsoft/unilm/tree/master/wavlm), which turns speech into what was said and how. Exported to ONNX from torchaudio's `WAVLM_LARGE` weights, unchanged. **Licence:** MIT (`LICENSE-WavLM.txt`, in the zip).
  - `speak.onnx`: **Writezu's own voice model**, made by Chrono Travel, LLC, which speaks those sounds back in the voice it's given. Licensed for use with Writezu only. It was trained on [LibriTTS](https://www.openslr.org/60/) (train-clean-100, by Heiga Zen, Viet Dang, Rob Clark, Yu Zhang, Ron J. Weiss, Ye Jia, Zhifeng Chen and Yonghui Wu at Google), under [Creative Commons Attribution 4.0](https://creativecommons.org/licenses/by/4.0/). It holds no one reader's voice.
  - `NOTICE.txt`: all of the above.
- Both models are plain ONNX files: standard operators with their weights inside, nothing that runs code. Writezu runs them on the user's own computer with Microsoft's ONNX Runtime, fetched from Microsoft's own package. Nothing anyone says leaves their computer.
- **What Writezu uses it for:** making AI voices from recordings people make with permission, and speaking in them live.
