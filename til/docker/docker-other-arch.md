---
title: Docker emulate another architecture
draft: true
tags: 

---
# Docker emulate another architecture
You might sometimes want to run a docker image with a different architecture from your machine.

In my case, I have a MacBook M2 laptop with Linux/Arm64 architecture, and I wanted to run a Docker image that was only available for Linux/AMD64`.

At the first attempt, I keep getting the following warning and the container wouldn't run

```
WARNING: The requested image's platform (linux/amd64) does not match the detected host platform (linux/arm64/v8) and no specific platform was requested
```

Docker allow you to specify a platform to run a container different from the machine platform with the following command

```bash
docker run -it --platform linux/amd64 <image>
```

The warning will disappear with this command, and things should work correctly.

If you still have problems running the container like I did

```
$ docker run -it --platform linux/amd64 <image>
exec /bin/bash: exec format error
```

This is because there is still a mismatch in the binary architecture and something else is wrong.

The solution is to make sure that you have `Rosetta 2` installed on your Mac with the following command

```
softwareupdate --install-rosetta
```

Finally, you need to restart Docker, and you should be able to run the command successfully 

```
$ docker run -it --platform linux/amd64 <image>
root#
```
If at this point you omit the platform parameter, the warning will appear again but the command will run correctly this time.