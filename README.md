# FBX2GLTF

[![Build FBX2GLTF](https://github.com/DmLvkvch/FBX2glTF/actions/workflows/build.yml/badge.svg)](https://github.com/DmLvkvch/FBX2glTF/actions/workflows/build.yml)

Change skinning-weights to 4 if your engine does not support that feature.

Change the default import of the engine to be different from 30 fps if needed.

There are artifacts in the Github Actions for Windows, MacOS and Linux.

You need to install the MVSC redistributable on Windows. https://support.microsoft.com/en-ca/help/2977003/the-latest-supported-visual-c-downloads.

## Build Instructions

Reference the Github workflow.

## Apple Silicon

    pip install --upgrade conan
    conan profile new default --detect
    git config --global filter.lfs.required false
    git config --global filter.lfs.smudge "git-lfs smudge --skip %f"
    git config --global filter.lfs.process "git-lfs filter-process --skip"
    curl -O -L "https://github.com/V-Sekai/FBXSDK-Darwin/archive/refs/tags/2020.2.zip"
    7z x 2020.2.zip
    mv ./FBXSDK-Darwin-2020.2/sdk .
    zstd -d -r --rm ./sdk || true
    env CMAKE_OSX_ARCHITECTURES=aarch64 conan install . -i build -s build_type=Release --build missing
    env CMAKE_OSX_ARCHITECTURES=aarch64 conan build -bf build .



