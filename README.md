# esbuild-plugin-clean
[![npm](https://img.shields.io/npm/v/esbuild-plugin-clean.svg)](https://www.npmjs.com/package/esbuild-plugin-clean)
[![build](https://github.com/jwilsson/esbuild-plugin-clean/actions/workflows/build.yml/badge.svg)](https://github.com/jwilsson/esbuild-plugin-clean/actions/workflows/build.yml)

An [esbuild](https://esbuild.github.io/) plugin to clean your build folder.

## Installation
```sh
npm install esbuild-plugin-clean
```

### Requirements
* Node 14.15.0 (LTS) or later.
* esbuild 0.11.18 or later.

## Usage
```js
import { build } from 'esbuild';
import { cleanPlugin } from 'esbuild-plugin-clean';

build({
  bundle: true,
  entryPoints: [path.resolve(__dirname, 'index.js')],
  metafile: true,
  outdir: path.resolve(__dirname, 'dist'),
  watch: true,
  plugins: [cleanPlugin({
      // Plugin options
  })],
});
```

*Note: The `metafile` and `outdir` options must be set for the plugin to have any effect.*

### Options
* `dry` (default `false`) - Run the plugin in dry mode, not deleting anything. Most useful together with the `verbose` option to see what would have been deleted.
* `initialCleanPatterns` (default `['**/*']`) - File patterns to remove on plugin setup, useful to clean the build directory before creating new files. Pass an empty array to disable it.
* `verbose` (default `false`) - Print all files that have been deleted after each run.
