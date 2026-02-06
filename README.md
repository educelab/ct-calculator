# Cone Beam CT Geometry Calculator

A web-based tool for Radiographers and CT Lab Managers to estimate scanning resolution and geometric parameters. This application helps determine the optimal Source-to-Object (SOD) and Source-to-Detector (SDD) distances to achieve the best voxel resolution for a given object size, while respecting the physical travel limits of the scan system.

## 🚀 Features

* **Auto-Optimization Mode:** Automatically calculates the maximum magnification and best resolution where the object still fits within the Field of View.
* **Manual Positioning Mode:** Manually set SOD and SDD to see resulting pixel size and check for collisions or FOV clipping.
* **System Presets:** Includes generic presets for Micro-CT, Nano-CT, and Industrial systems.
* **Custom Import:** Load your own scanner definitions via JSON.
* **Double-Wide Support:** Toggle offset-detector calculations for systems that support half-fan scans.
* **Live Visualizer:** Dynamic HTML5 Canvas diagram showing the source, object, and detector relationship.

## 🛠 Usage

1.  **Select a System:** Choose a preset from the dropdown or load a custom JSON configuration.
2.  **Input Object Size:** Enter the diameter of your sample in millimeters.
3.  **Choose Mode:**
    * *Auto:* The app solves for the best resolution.
    * *Manual:* You define the geometry, the app warns of errors.
4.  **Read Results:** View the effective pixel size, required travel positions, and magnification.

## ⚙️ Custom System Configuration (JSON)

You can upload a `.json` file to add your specific machine intrinsics to the calculator. Use the following format:

```json
{
  "name": "Nikon XT H 225",
  "pixelPitch": 0.200, 
  "widthPx": 2000,
  "minSOD": 25.0,
  "maxSOD": 950.0,
  "minSDD": 300.0,
  "maxSDD": 1100.0,
  "allowDoubleWide": true,
  "overlapPx": 150
}
```

* `pixelPitch`: The physical size of a detector pixel (mm).
* `widthPx`: The number of horizontal pixels on the detector.
* `minSOD` / `maxSOD`: The travel range of the manipulator (mm).
* `maxSDD`: The maximum distance the detector can move back (mm).
* `allowDoubleWide`: `true` if the detector can shift for offset scans, `false` otherwise.
* `overlapPx`: The number of pixels used for overlap reconstruction in offset scans (usually 100-200).

## 📦 Deployment

This is a static web application (HTML/CSS/JS in a single file).

1.  Ensure your main file is named `index.html`.
2.  Push to GitHub.
3.  Enable GitHub Pages (or use the provided GitHub Actions workflow).

## 📄 License

MIT License. Free to use for academic and industrial scan planning.