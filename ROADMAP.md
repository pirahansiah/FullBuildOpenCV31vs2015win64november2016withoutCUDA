# ROADMAP.md — FullBuildOpenCV31vs2015win64november2016withoutCUDA

## 12-Month Vision

Modernize the static OpenCV 3.1 binary repository into a fully automated, cross-platform build and distribution system targeting OpenCV 5.x with hardware-specific optimizations, Python 3.14 bindings, and C++26 compliance.

---

### Q1 (Months 1–3): Foundation & Build Infrastructure

**Goal:** Reproducible cross-platform builds from source.

- [ ] Set up CMake 4.0 build system with C++26 target support
- [ ] Create conda environment (`py314`) with Python 3.14 and PyO3
- [ ] Implement CI matrix: Windows 11 (MSVC 14.4), macOS 27 (Clang 19), Ubuntu 26.04 (GCC 15)
- [ ] Add OpenCV 5.11 as submodule or fetch-content dependency
- [ ] Baseline benchmarks on Intel Ultra 9 Gen 2 and Apple M5 Max
- [ ] Remove legacy VS 2015 pre-built binaries from main branch

### Q2 (Months 4–6): Hardware-Specific Optimizations

**Goal:** SIMD and GPU acceleration per target platform.

- [ ] AVX-512 kernels for Intel Ultra 9 (resize, blur, feature matching)
- [ ] Apple Neural Engine integration for M5 Max (via CoreML/Metal)
- [ ] NEON optimizations for Raspberry Pi 5 16GB
- [ ] CUDA 13 backend for NVIDIA Spark (128GB VRAM) — batch inference pipeline
- [ ] Runtime SIMD dispatch system (detect capabilities at startup)
- [ ] Publish performance benchmarks table in README

### Q3 (Months 7–9): Python Bindings & API Modernization

**Goal:** First-class Python 3.14 support with zero-copy interop.

- [ ] PyO3-based `cv2` replacement module with type stubs
- [ ] Zero-copy `cv::Mat` ↔ NumPy ndarray memory sharing
- [ ] `std::expected`-based error handling replacing exception-heavy API
- [ ] `std::print` for debug/diagnostic output (C++26)
- [ ] Migration guide: OpenCV 3.1 → 5.x API changes with compatibility shim
- [ ] Integration tests across all 4 platforms

### Q4 (Months 10–12): Distribution, Documentation & Release

**Goal:** Production-ready distribution with full documentation.

- [ ] Versioned binary releases with SBOM attestation (SLSA Level 2)
- [ ] vcpkg, pip, and conda-forge package manifests
- [ ] Comprehensive API docs (Sphinx + Doxygen)
- [ ] Docker images for each platform (GPU and CPU variants)
- [ ] ROADMAP.md update for Year 2 (ONNX Runtime, TensorRT, WebAssembly targets)
- [ ] Archive legacy 2016 binaries to a `legacy/` branch

---

## Technical Debt

| ID | Description | Severity | Target Quarter |
|----|-------------|----------|----------------|
| TD-1 | Remove VS 2015 pre-built binaries from default branch | Medium | Q1 |
| TD-2 | Replace `CV_BGR2GRAY`-style constants with `cv::COLOR_*` namespaced enums | Low | Q1 |
| TD-3 | Eliminate raw pointer usage in any remaining C wrapper code | Medium | Q2 |
| TD-4 | Replace manual memory management with `std::unique_ptr` / RAII patterns | Medium | Q2 |
| TD-5 | Add missing type stubs for Python `cv2` module | Low | Q3 |
| TD-6 | Migrate CI from Travis/AppVeyor to GitHub Actions with matrix builds | High | Q1 |
| TD-7 | Resolve license header inconsistencies (Apache 2.0 vs legacy headers) | Low | Q4 |

## Future Features (Year 2+)

| Feature | Target | Priority |
|---------|--------|----------|
| ONNX Runtime 2.x integration for model inference | Q1 Y2 | High |
| TensorRT 10.x backend for NVIDIA hardware | Q1 Y2 | High |
| WebAssembly build target for browser-based CV | Q2 Y2 | Medium |
| Vulkan compute backend (replacing legacy OpenCL) | Q2 Y2 | Medium |
| G-API graph-based parallel processing pipeline | Q3 Y2 | Medium |
| Stereo DNN depth estimation module (OpenCV 4.9+) | Q3 Y2 | Low |
| Real-time video analytics pipeline (GStreamer integration) | Q4 Y2 | Low |
| Multilingual bindings: Rust, Go, Swift | Q4 Y2 | Low |
