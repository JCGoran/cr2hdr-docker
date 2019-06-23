# Dockerfile for cr2hdr
This is a simple Dockerfile for installing the `cr2hdr` tool for processing Magic Lantern dual ISO images ([source repo](https://bitbucket.org/hudson/magic-lantern/)). I couldn't find a simple installer for GNU/Linux, so after some trial and error this is is the end result.

## How to install
The image from [Dockerhub](https://hub.docker.com/r/jcgoran/cr2hdr):
```
docker pull jcgoran/cr2hdr
```
Building the Docker image from this repo:
```
git clone https://github.com/JCGoran/cr2hdr-docker
docker build cr2hdr-docker
```

## How to use
Once you've installed it, you can run `cr2hdr` as follows:
```
docker run --rm -ti -v "$(pwd):/data" jcgoran/cr2hdr /bin/bash -c "cr2hdr [OPTIONS] [IMAGE_NAME(S)]"
```
As the above is lengthy, you may want to make a `bash`/`csh`/whatever shortcut, by putting something like the below in one of your shell dotfiles:
```
cr2hdr(){
    args="$@"
    docker run --rm -ti -v "$(pwd):/data" jcgoran/cr2hdr /bin/bash -c "cr2hdr $args"
}
```
Then to invoke it, you can just run `cr2hdr` from a shell (note: it will only work for images in the current directory and below, i.e. going up (`../` or similar) or using absolute paths will not work).

## License
`cr2hdr` and Magic Lantern are properties of their respective owners.
