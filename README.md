# Raylib Starter Template

## Project Structure

```
project-root/
├── main.cpp                 # entry point
├── headers/                 # all your .h files go here
├── raylib/                  # raylib library (headers, static lib, dll) — don't touch
│   ├── libraylib.a
│   ├── raylib.dll
│   └── raylib.h
├── src/                     # additional .cpp files go here (everything except main.cpp)
└── assets/
    ├── graphics/            # sprites, textures, tilesets — .png, .jpg
    ├── sounds/              # sfx and music — .wav, .mp3, .ogg
    └── fonts/               # .ttf, .otf
```

## Adding source files

`main.cpp` stays at the project root as the entry point. Any additional `.cpp` file goes into `src/`. The Makefile auto-discovers everything there — no need to edit any build config.

```
project-root/
├── main.cpp
└── src/
    ├── player.cpp
    ├── enemy.cpp
    └── world.cpp
```

## Adding headers

Drop any new `.h` file into `headers/`. It's already on the include path, so from any `.cpp` file you just write:

```cpp
#include "player.h"
```

no relative path juggling needed, regardless of which `.cpp` file is including it.

## Adding assets

Assets are organized by type under `assets/`. Keep this structure so paths stay predictable in code:

```
assets/
├── graphics/
│   ├── player.png
│   ├── enemy.png
│   └── tileset.png
├── sounds/
│   ├── jump.wav
│   └── theme.mp3
└── fonts/
    └── pixel.ttf
```

Load them in code using the folder as part of the path:

```cpp
Texture2D player = LoadTexture("assets/graphics/player.png");
Sound jump = LoadSound("assets/sounds/jump.wav");
Font pixelFont = LoadFont("assets/fonts/pixel.ttf");
```

**Note on working directory:** these paths are relative to wherever the `.exe` is run *from*, not where the `.exe` file physically sits. Always run the built exe from `project-root/` (where `assets/` lives), e.g. via `make run`, so these relative paths resolve correctly.

## Adding new asset categories

If you need a new category (e.g. `assets/shaders/`, `assets/data/`), just create the folder and start referencing it in code — no build config changes needed, since assets are loaded at runtime rather than compiled in.
