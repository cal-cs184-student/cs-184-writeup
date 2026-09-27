# Homework 1 write-up

Open `index.html` to read and edit the report for Tasks 1–6. When it is ready, open it in your browser and use Command-P → Save as PDF to create the PDF required for Gradescope. The PNG figures were captured through the renderer's `S` key handler, including the pixel inspector where required. No extra credit is included.

Before submission, replace the public webpage URL at the top of `index.html` with your actual Repo184 write-up URL and confirm the author line. Copy the contents of this directory into the separate public write-up repository's root, preserving the relative image and SVG paths. Do not publish the private code repository to host the report.

The report includes the required overview, Task 1–6 explanations, and image comparisons. Lecture-reference sections and testing commentary have been removed from the submitted report.

## Reproduce the figures

From the code repository root on this Mac:

```sh
cmake --build build -j 4
python tests/capture_report.py
```

This opens temporary renderer windows and sends its `=`, `P`, `L`, `Z`, and `S` keyboard events. It requires access to the macOS window server. `tests/capture.cpp` uses the unmodified application screenshot handler. Every figure is 800 × 600; capture settings and inspector locations are in `tests/capture_report.py`.

To inspect scenes manually:

```sh
./build/draw svg/transforms/my_robot.svg
./build/draw svg/basic/test7.svg
./build/draw svg/texmap/test5.svg
./build/draw docs/mipmap_demo.svg
```

Use `P` for pixel filtering, `L` for mip-level filtering, `=` and `-` for samples per pixel, `Z` for the inspector, and `S` to save a PNG. Space resets the view.

## Texture source

`checkerboard.png` is the original 800 × 600 PNG downloaded from:

https://commons.wikimedia.org/wiki/File:1px-black-white-pattern_checkerboard.png

Author: Johannes Kalliauer. License: CC0 1.0. `mipmap_demo.svg` adapts the starter `svg/texmap/test6.svg` mesh to use this PNG.

## Numerical checks

From the code repository root, run `sh tests/run_checks.sh`. This compiles and runs the checks with address and undefined-behavior sanitizers.
