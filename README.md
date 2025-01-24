# ffmpeg-hevc
Shell Script to re-encode videos using FFMPEG and NVENC in high quality mode.
- The script preserves all audio tracks and subtitles.
    - Works best with 2160p videos.

## Requirements
- NVIDIA GPU.
- NVIDIA drivers installed.
- FFMPEG installed.

## How to Use

`$ ffmpeg-hevc [-b] <directory|input-file> <file-extension|bitrate>`

<br>

**Examples of how to use this script:**

For a single file:

```shell
$ ffmpeg-hevc input.mp4 8192k
```

<br>

For batch mode (multiple files):

```shell
$ ffmpeg-hevc -b /path/to/files mp4 8192k
```

## Tip

Track NVIDIA GPU usage with the command below.

```shell
$ watch nvidia-smi
```

## HDR handling

The script shouldn't affect HDR's behavior, but if you have any problems, try one of the following parameter combinations.

### HDR10

```
-pix_fmt yuv420p10le -colorspace bt2020 -color_trc smpte2084 -color_range tv
```

### HLG (Hybrid Log-Gamma) HDR

```
-pix_fmt yuv420p10le -colorspace bt2020 -color_trc arib-std-b67 -color_range tv
```

### Common Pixel Formats for HDR
- `yuv420p10le`: 10-bit 4:2:0 for HDR content.
- `yuv422p10le`: 10-bit 4:2:2 (less common for consumer use but can be used for some professional HDR workflows).
- `yuv444p10le`: 10-bit 4:4:4 (rarely used in video but can be used for HDR).
