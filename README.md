# SphereCraft 360 — Windows Edition

Freeware • Closed Source • Proprietary Software

SphereCraft 360 is a free Windows application for placing flat video and images onto 360° equirectangular footage, with transparent and chroma-key export options.

The application is provided free of charge. SphereCraft 360 is not open source and the source code is not publicly available.

License

SphereCraft 360 is proprietary software.

You are free to:

• Download and use the application.
• Use it for personal purposes.
• Use it for commercial purposes.
• Keep copies of the original application for backup purposes.

You may not:

• Modify the application.
• Decompile, disassemble, or reverse engineer the application.
• Redistribute modified versions.
• Sell, sublicense, or commercially redistribute the application itself.
• Copy or reuse the application’s proprietary code or implementation.
• Claim the application or its source code as your own.

The source code is not included in this repository and is not licensed for public use.

Free to use does not mean open source.

All rights not expressly granted are reserved by the copyright holder.

Copyright

Copyright © 2026 Piotr Kubicki. All rights reserved.

SphereCraft 360, its executable code, source code, design and proprietary implementation remain the property of the copyright holder.

Third-Party Software

SphereCraft 360 uses FFmpeg and FFprobe as external components. These components are subject to their respective licenses.

Please refer to the respective FFmpeg documentation and licensing information for details.

## Run the compiled application

1. Extract the release ZIP to a folder.
2. Run **SphereCraft360.exe**.

You do not need to install Python or development packages to run the compiled application. The app icon is embedded in the EXE.

## FFmpeg and FFprobe

SphereCraft 360 requires the external **FFmpeg** and **FFprobe** tools to read video information, preview media, and export files. They are not included in the EXE.

Download a Windows build from the [FFmpeg download page](https://ffmpeg.org/download.html), which links to available Windows builds. Extract it to a permanent folder, such as `C:\ffmpeg`.

In the app, open **Tools → Settings** and select both executables from the `bin` folder:

- **FFmpeg executable:** `C:\ffmpeg\bin\ffmpeg.exe`
- **FFprobe executable:** `C:\ffmpeg\bin\ffprobe.exe`

Use `ffmpeg.exe` and `ffprobe.exe` from the same build. Do not select `ffplay.exe`. If both tools are available on the system `PATH`, the app may detect them automatically.

FFmpeg and FFprobe run in the background without opening separate console windows. Errors appear in the app. Initial FFmpeg detection can take up to 30 seconds.

## Basic workflow

1. Select **Open 360 Master** and load an equirectangular 360° video.
2. Select **Open Flat Media** and load a flat video or image.
3. Use **Navigate** to rotate the panorama view, or **Place Layer** to move the layer.
4. Adjust **Yaw**, **Pitch**, **Roll**, **Scale**, **Distance**, and **Opacity** in the Inspector.

**Scale** changes the layer's physical size. Increasing **Distance** moves it farther away and makes it appear smaller; decreasing Distance moves it closer and makes it appear larger. These controls work independently.

## Export

- **Transparent PNG** — a single equirectangular image with an alpha channel.
- **Transparent Video** — ProRes 4444 MOV with alpha. ProRes encoding uses the CPU.
- **Opaque Video** — MP4 with a solid green chroma-key background. The app uses an available hardware encoder when FFmpeg provides one; otherwise, it uses the CPU.

For video exports, resolution, frame rate, and available technical parameters come from the **360 Master**. Export duration comes from the **Flat Video**:

- **Entire Flat Video** exports the complete file duration, including fractional seconds.
- **Custom Range** accepts **From** and **To** values in whole seconds. The maximum **To** value is the last whole second within the video duration.

When exporting a video from an image, **Image duration** accepts whole seconds from 1 to 86,400.

## If FFmpeg is not detected

Open **Tools → Settings** and select the full paths to `ffmpeg.exe` and `ffprobe.exe` again. Confirm that both files exist at those locations, then restart the app. Any error message includes details to help diagnose the problem.

## Controls

- **N** — Navigate
- **P** — Place Layer
- **R** — Reset layer transform
- **Space** — Play or pause preview
- **Ctrl+O** — Open 360 Master
- **Ctrl+Shift+O** — Open Flat Media
- **Ctrl+E** — Export

## Donations and contact

SphereCraft 360 is free to use. Donations are completely optional. If you enjoy the app and would like to support its continued development, choose **Help → Donate** and send a voluntary PayPal donation to **pitkub@gmail.com**. The dialog lets you copy the address or open PayPal.

For contact or support, email **pitkub@gmail.com**.
