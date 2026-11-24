# simplicial-toolkit-opencv

The optional image-processing toolkit for [Paperboat](https://github.com/paperboatlab/paperboat):
filtering, morphology, contour and Hough detection on `image` wires, an `Image` station object and
an `image` instrument for the Board, built on OpenCV. Optional toolkits are installed by the user
and never bundled into Paperboat release artifacts.

**Docs:** <https://paperboatlab.github.io/toolkits/opencv/> (sources in
[`engine/toolkit/opencv/docs/`](engine/toolkit/opencv/docs/) and each block's `doc.rst`, also in
the Help window (F1))

## Install

Requires the OpenCV development headers (`libopencv-dev` on Debian/Ubuntu, `opencv-devel` on Fedora,
`opencv` on Homebrew):

```sh
paperboat toolkit install opencv --repo https://github.com/paperboatlab/simplicial-toolkit-opencv.git
```

Declare `toolkits = ["opencv"]` in `station.toml` and import `"opencv"` in `descriptor.toml`.

## Build

Against a Paperboat checkout or installed SDK (`-DCMAKE_PREFIX_PATH=<prefix>`):

```sh
cmake -S engine/toolkit/opencv -B build -G Ninja -DPAPERBOAT_SOURCE_DIR=../paperboat
cmake --build build
```

## Check

```sh
ctest --test-dir build --output-on-failure
```

## CI

[![ci](https://github.com/paperboatlab/simplicial-toolkit-opencv/actions/workflows/ci.yml/badge.svg?branch=dev)](https://github.com/paperboatlab/simplicial-toolkit-opencv/actions/workflows/ci.yml?query=branch%3Adev) builds the toolkit both in-tree and as an external SDK plugin against `paperboat` (`dev`) and runs `paperboat check` on `ocv-01`.

## Licence

GNU General Public License version 3 (see [LICENSE](LICENSE)). Installed by the user and never
bundled into a Paperboat release artifact.
