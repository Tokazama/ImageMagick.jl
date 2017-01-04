# ImageMagick

[![Build Status](https://travis-ci.org/JuliaIO/ImageMagick.jl.svg?branch=master)](https://travis-ci.org/JuliaIO/ImageMagick.jl)
[![Build status](https://ci.appveyor.com/api/projects/status/hl0j4amikte3pl9c/branch/master?svg=true)](https://ci.appveyor.com/project/SimonDanisch/imagemagick-jl/branch/master)
[![Coverage Status](https://coveralls.io/repos/JuliaIO/ImageMagick.jl/badge.svg?branch=master&service=github)](https://coveralls.io/github/JuliaIO/ImageMagick.jl?branch=master)
[![codecov.io](http://codecov.io/github/JuliaIO/ImageMagick.jl/coverage.svg?branch=master)](http://codecov.io/github/JuliaIO/ImageMagick.jl?branch=master)

This package was split off from [Images.jl](https://github.com/timholy/Images.jl) to make image I/O more modular.

# Installation

Add the package with

```jl
Pkg.add("ImageMagick")
```

# Usage

ImageMagick will be used as needed if you've said

```
using FileIO
```

in your session or module. You should **not** generally say `using
ImageMagick`.  See [FileIO](https://github.com/JuliaIO/FileIO.jl) for
further details.

It's worth pointing out that packages such as Images load FileIO.

# Troubleshooting

## OSX

ImageMagick.jl will by default not use the system installed ImageMagic in
`/usr/local`, but rather install it's own copy via Homebrew.jl, because the
former results in problems like `ERROR: no encode delegate for this image format
'MIFF'`.

An alternative to ImageMagick on OS X is
[QuartzImageIO](https://github.com/JuliaIO/QuartzImageIO.jl).

You may also find [debugging
Homebrew](https://github.com/JuliaLang/Homebrew.jl/wiki/Debugging-Homebrew.jl)
useful.

## Manual installation on Windows

If automatic installation fails, get the current version from
http://www.imagemagick.org/script/binary-releases.php#windows
(e.g. ImageMagick-6.8.8-7-Q16-x86-dll.exe) and make sure that the "Install
development headers and libraries for C and C++" checkbox is selected.  You may
choose to let the installer add the installation directory to the system path or
provide it separately.  In the later case you may add it to your `.juliarc.jl`
file as (for example) `push!(Base.DL_LOAD_PATH,
"C:/programs/ImageMagick-6.8.8"`). Alternatively, you can set your `MAGICK_HOME` environment variable.

**When manual intervention is necessary, you need to restart Julia for the
necessary changes to take effect.**

## Linux

ImageMagick.jl automatically searches for an installed version of
libMagickWand.  Use the environment variable `MAGICK_HOME` to add to the search
path.  Use `ImageMagick.libversion` to see what version it found.  Version 6.7+
(up to but not including 7.0) are the most supported versions, in particular
for multipage TIFFs.

The environment variable `MAGICK_THREAD_LIMIT` can be used to throttle multithreading.
