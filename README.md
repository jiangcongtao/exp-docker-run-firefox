# Run GUI Firefox GUI application in Docker

## Build

```bash
docker build -t firefox .
```

## Run

### On linux

```bash
docker run -ti --rm \
       -e DISPLAY=$DISPLAY \
       -v /tmp/.X11-unix:/tmp/.X11-unix \
       firefox
```

### On Mac

```bash

# 1. Install xQuartz

# 2. Terminal 1
socat TCP-LISTEN:6000,reuseaddr,fork UNIX-CLIENT:\"$DISPLAY\"

# 3. Terminal 2
docker run -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$(ipconfig getifaddr en0):0 firefox
```
