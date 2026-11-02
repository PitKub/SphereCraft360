# SphereCraft 360 — Windows Edition

**Freeware • Closed Source • Proprietary Software**

SphereCraft 360 is a free Windows application for placing flat videos and images onto 360° equirectangular footage. It creates correctly positioned equirectangular overlays and supports transparent and chroma-key exports.

The application is provided free of charge. SphereCraft 360 is not open source, and its source code is not included in this public repository.

## Latest release

Download **SphereCraft 360 1.3.6 for Windows** from [GitHub Releases](https://github.com/PitKub/SphereCraft360/releases/latest).

## Download and run

Download **SphereCraft360.exe** from [GitHub Releases](https://github.com/PitKub/SphereCraft360/releases) and run it. No ZIP extraction or separate `assets` folder is required.

Python and development packages are not needed to run the compiled application. The EXE includes the application icon and runtime assets.

## FFmpeg and FFprobe

SphereCraft 360 requires external **FFmpeg** and **FFprobe** tools to read video information, preview media, and export files. They are not included in the release.

Download a Windows build from the [FFmpeg download page](https://ffmpeg.org/download.html) and extract it to a permanent folder, such as `C:\ffmpeg`.

In the app, open **Tools → Settings** and select both executables from the `bin` folder:

- **FFmpeg executable:** `C:\ffmpeg\bin\ffmpeg.exe`
- **FFprobe executable:** `C:\ffmpeg\bin\ffprobe.exe`

Use `ffmpeg.exe` and `ffprobe.exe` from the same build. Do not select `ffplay.exe`. If both tools are available on the system `PATH`, the app may detect them automatically.

SphereCraft remembers the selected paths between launches.

FFmpeg and FFprobe run in the background without opening separate console windows. Errors appear in the app. At startup the status bar shows **FFmpeg: checking…** while the app checks your FFmpeg build for hardware encoders; the window stays usable during this check.

## Basic workflow

1. Select **Open 360 Master** and load an equirectangular 360° video.
2. Select **Open Flat Media** and load a flat video or image.
3. Use **Navigate** to rotate the panorama view, or **Place Layer** to position the flat layer on the sphere.
4. Adjust **Yaw**, **Pitch**, **Roll**, **Scale**, **Distance**, and **Opacity** in the Inspector.
5. Export the overlay and add it above the 360° footage in your editor.

Use the **Dark theme**/**Light theme** switch at the right end of the top toolbar to change the app appearance. SphereCraft remembers your selection.

**Scale** changes the layer’s physical size. Increasing **Distance** moves it farther from the sphere’s center and makes it appear smaller; decreasing Distance moves it closer and makes it appear larger. These controls work independently.

## Export

- **Transparent PNG** — a single equirectangular image with an alpha channel.
- **Transparent Video** — ProRes 4444 MOV with alpha. ProRes encoding uses the CPU.
- **Opaque Video** — MP4 with a solid green chroma-key background. The app uses a hardware encoder when one works at the 360 Master's size; otherwise, it uses the CPU. NVIDIA's H.264 encoder cannot encode 8K, so an 8K H.264 master is exported as HEVC. NVIDIA NVENC, Intel Quick Sync and AMD AMF are each tested on your PC, so the app works with any of these GPUs, or with no GPU at all.

For playback, SphereCraft times CPU decoding and each available hardware decoder on the opened 360 Master and uses the fastest. **Tools → Settings** shows the encoders and decoders chosen on your PC.

Transparent exports preserve the overlay’s alpha channel, so you can place the result on a timeline above your 360° footage without adding placement filters. Opaque exports use a green background for editors that need chroma keying.

For video exports, resolution, frame rate, and available technical parameters come from the **360 Master**. Export duration comes from the **Flat Video**:

- **Entire Flat Video** exports the complete file duration, including fractional seconds.
- **Custom Range** accepts **From** and **To** values in whole seconds. The maximum **To** value is the last whole second within the video duration.

When exporting a video from an image, **Image duration** accepts whole seconds from 1 to 86,400.

Both Flat Video exports include the Flat Video's audio for the exported range. The audio is copied unchanged when the output file accepts its format; otherwise it is converted to AAC.

To stop a video export, select **Cancel Export** in the status bar. The partly written output file is left in place and may be incomplete.

16-bit PNG and TIFF images are converted to 8 bits per channel when loaded.

### Optional layer frame

Use **Layer Frame** below **Viewer** in the Inspector to add a solid-color outline around the projected layer. Enable the frame, choose a color from the visual swatch palette or select **Custom color…**, then set a thickness from 1 to 100 pixels. Thickness is measured in output equirectangular pixels. The preview updates as you adjust the frame, and the same settings are used for transparent PNG, transparent video, and opaque video exports.

## If FFmpeg is not detected

Open **Tools → Settings** and select the full paths to `ffmpeg.exe` and `ffprobe.exe` again. The app warns you if either file does not exist at the selected location. Any error message includes details to help diagnose the problem.

## Controls

- **N** — Navigate
- **P** — Place Layer
- **R** — Reset layer transform
- **Space** — Play or pause preview
- **Ctrl+O** — Open 360 Master
- **Ctrl+Shift+O** — Open Flat Media
- **Ctrl+E** — Export

## Privacy

SphereCraft 360 works offline. It does not send your media, settings or usage data anywhere. The only network action is **Help → Donate → Open PayPal**, which opens the PayPal website in your browser.

## License

SphereCraft 360 is proprietary software.

You are free to:

- Download and use the application.
- Use it for personal purposes.
- Use it for commercial purposes.
- Keep copies of the original application for backup purposes.

You may not:

- Modify the application.
- Decompile, disassemble, or reverse engineer the application.
- Redistribute modified versions.
- Sell, sublicense, or commercially redistribute the application itself.
- Copy or reuse the application’s proprietary code or implementation.
- Claim the application or its source code as your own.

The source code is not included in this public repository and is not licensed for public use.

Free to use does not mean open source. All rights not expressly granted are reserved by the copyright holder.

## Copyright

Copyright © 2026 Piotr Kubicki. All rights reserved.

SphereCraft 360, its executable code, source code, design, and proprietary implementation remain the property of the copyright holder.

## Third-party software

SphereCraft 360 uses FFmpeg and FFprobe as external components. These components are subject to their respective licenses. Please refer to the FFmpeg documentation and licensing information for details.

## Donations and contact

SphereCraft 360 is free to use. Donations are completely optional. If you enjoy the app and would like to support its continued development, choose **Help → Donate** and send a voluntary PayPal donation to **pitkub@gmail.com**. The dialog lets you copy the address or open PayPal.

For contact or support, email **pitkub@gmail.com**.
