# Elm Compiler Stale Cache

This repository is meant to demonstrate a stale cache bug in the Elm 0.14 compiler. To reproduce, run

```bash
elm-make --yes --output=build/a.html src/a.elm
elm-make --yes --output=build/b.html src/b.elm
```

Now open `build/b.html` in your browser. It will incorrectly show the text "File A" because of a cache from the build of a.elm that is not properly invalidated.

You can forcefully invalidate the cache and then rebuild by running

```bash
rm -rf elm-stuff/build-artifacts
elm-make --yes --output=build/b.html src/b.elm
```
