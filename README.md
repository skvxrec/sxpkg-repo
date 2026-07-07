# sxpkg-repo
*it's our repo*

Package build scripts for [sxOS](https://github.com/skvxrec/sxos), used by sxpkg.

## layout

Each package is a directory with three files:

- `sources` — URL(s) to fetch, one per line
- `depends` — names of dependency packages, one per line
- `build` — a shell script that builds the package and installs it into `$1` (DESTDIR)

Example (`bash/`):

```sh
# build
#!/bin/sh
./configure --libdir=/usr/lib --prefix=/usr --without-bash-malloc --with-curses=no --disable-readline
make -j$(nproc)
make DESTDIR="$1" install
```

## commands

```
sxpkg sync           sync package repo
sxpkg install <pkg>  install a package (and its dependencies)
sxpkg remove <pkg>   remove a package
sxpkg list           list installed packages
sxpkg clean [pkg]    remove build cache
```

Since this repo lives on your disk, nothing stops you from opening a `build` script and fixing it yourself before rebuilding.

## contributing

Made a package for something not in here? Send it over and I'll review it and add it to the repo.
