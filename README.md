# FullBuildOpenCV31vs2015win64november2016withoutCUDA

[![OpenCV](https://img.shields.io/badge/OpenCV-3.1-5C3EE8?style=for-the-badge&logo=opencv)](https://opencv.org)
[![Visual Studio](https://img.shields.io/badge/Visual_Studio-2015-5C2D91?style=for-the-badge&logo=visualstudio)](https://visualstudio.microsoft.com)
[![Windows](https://img.shields.io/badge/Windows-10-0078D4?style=for-the-badge&logo=windows)](https://microsoft.com)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)

## Overview

Pre-built **OpenCV 3.1** binaries for **Windows 64-bit** compiled with **Visual Studio 2015** without CUDA support. Ready-to-use libraries for legacy Windows projects.

> **Note:** This is a historical build from November 2016. For current OpenCV development, use OpenCV 4.11+ with Visual Studio 2022.

## Build Configuration

| Property | Value |
|----------|-------|
| OpenCV Version | 3.1.0 |
| Compiler | MSVC 19.0 (VS 2015) |
| Platform | Windows x64 |
| CUDA | Not included |
| Build Date | November 2016 |

## Project Structure

```
FullBuildOpenCV31vs2015win64november2016withoutCUDA/
├── .git/
└── README.md
```

## OpenCV Version History

| Version | Year | Key Features |
|---------|------|--------------|
| 3.1 | 2016 | DNN module, TF/Caffe support |
| 4.0 | 2018 | API modernization, DNN improvements |
| 4.5 | 2021 | Vision Transformers, CUDA 11.x |
| 4.8 | 2023 | WeChat QR, ONNX 1.14 |
| 4.9 | 2024 | Stereo DNN, AV1 support |
| 4.10 | 2025 | CUDA 12.x, improved G-API |
| 4.11 | 2025 | Vulkan backend, enhanced SIMD |

## Migration Guide (2025-2026)

### From OpenCV 3.1 to 4.11+

```cpp
// Old (3.x)
cv::Mat img = cv::imread("image.jpg");

// New (4.x) — same API, but add:
#include <opencv2/core.hpp>
#include <opencv2/imgcodecs.hpp>
```

### Key Breaking Changes

1. **`CV_BGR2GRAY`** → `cv::COLOR_BGR2GRAY`
2. **`CV_WINDOW_AUTOSIZE`** → `cv::WINDOW_AUTOSIZE`
3. **DNN module** now supports more frameworks (ONNX, OpenVINO)
4. **`cv::ml`** API improvements for ML models
5. **G-API** for graph-based parallel processing

### Modern OpenCV Stack (2025-2026)

```
┌─────────────────────────────────────────┐
│         Application Layer               │
│   Python (cv2) / C++ / Java / JS        │
├─────────────────────────────────────────┤
│         High-Level APIs                 │
│   DNN / G-API / CUDA / contrib          │
├─────────────────────────────────────────┤
│         Core Libraries                  │
│   imgproc / imgcodecs / videoio         │
├─────────────────────────────────────────┤
│         Hardware Acceleration           │
│   CUDA 12.x / OpenCL / Vulkan / NEON    │
└─────────────────────────────────────────┘
```

## Installation (2025-2026)

### Windows (Modern)

```bash
# Using vcpkg (recommended)
vcpkg install opencv4[contrib]:x64-windows

# Using pip (Python)
pip install opencv-python opencv-contrib-python

# Using conda
conda install -c conda-forge opencv
```

### Linux

```bash
# Ubuntu/Debian
sudo apt install libopencv-dev

# Or build from source
git clone https://github.com/opencv/opencv.git
cd opencv && mkdir build && cd build
cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local ..
make -j$(nproc) && sudo make install
```

### macOS

```bash
brew install opencv
```

## Resources

- [OpenCV Official](https://opencv.org)
- [OpenCV Python Tutorials](https://docs.opencv.org/4.x/d6/d00/tutorial_py_root.html)
- [OpenCV C++ Documentation](https://docs.opencv.org/4.x/)
- [OpenCV GitHub](https://github.com/opencv/opencv)

## License

Apache License 2.0

---

**Maintainer:** [Farshid Pirahansiah](https://github.com/pirahansiah)