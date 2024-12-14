# Dockerfile Bug: Missing Requirements File

This repository demonstrates a common error in Dockerfiles: attempting to use a requirements.txt file before it's copied into the image.  The original Dockerfile fails to build because the `pip3 install` command cannot find the `requirements.txt` file.

The solution demonstrates the correct order of instructions to ensure the `requirements.txt` file is present before the installation.

## Bug

The original `Dockerfile` attempts to install dependencies using `pip3 install -r requirements.txt` before the file is copied into the image.

## Solution

The `Dockerfile_fixed` file shows the corrected order:  `requirements.txt` is copied *before* the installation command is executed.

## How to Reproduce

1. Clone this repository.
2. Attempt to build the original `Dockerfile` using `docker build -t buggy-app .`
3. Observe the build failure.
4. Build the corrected `Dockerfile_fixed` using `docker build -t fixed-app .`
5. Observe the successful build.