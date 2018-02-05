This repository contains a [conda][conda] recipe for building
[PSIPRED][psipred], a tool for predicting protein secondary structure
given a sequence profile.

## Prerequisites

1. You will need an installation of [conda][miniconda].

2. Your root conda installation must have the `conda-build` installed.

## Building

You should be able to build this package by simply running `conda build .`.

## Patches

This recipe contains the following patches:

* `makefile.patch`
    Play nicely with `conda build` by allowing the `$(CC)` environment variable
    to pass through. Also change the location of the data files to
    `$PREFIX/share/psipred/data`.

[conda]: https://conda.io
[psipred]: http://bioinf.cs.ucl.ac.uk/psipred/
[miniconda]: https://conda.io/miniconda.html
