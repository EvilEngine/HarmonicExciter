# Harmonic Exciter (VST3 / AU, 64-bit)

Adds missing air, presence and bite by saturating a high band and blending the generated harmonics back in.

## Signal flow
input -> LR4 high-pass @ Frequency -> Drive -> 4x oversampled tanh saturator (Color = odd/even balance) -> LR4 high-pass -> Amount -> added to the latency-aligned dry signal -> Mix -> Output

## Parameters
Frequency 500 Hz-16 kHz | Drive 0-24 dB | Amount 0-100% | Color 0-100% (odd -> even) | Mix | Output +/-18 dB | Listen (harmonics only)

## Build
Requires CMake 3.22+ and a C++17 compiler.

    cmake -B build -DCMAKE_BUILD_TYPE=Release
    cmake --build build --config Release --parallel

Windows (VST3, x64) and macOS (VST3 + AU, universal arm64/x86_64) build with the same commands. The plugin is copied to your system plugin folder after a successful build. A GitHub Actions workflow in `.github/workflows` builds all three platforms.
Change COMPANY_NAME and the manufacturer code in CMakeLists.txt before releasing.
