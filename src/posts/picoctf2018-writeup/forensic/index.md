---
date: 2019-09-21 10:52:00
title: PicoCTF 2018 Writeup Forensic.
description: Grab your pipe and your coat cuz we are going to do some investigation.
keyword:
    - ctf
    - hacking
    - forensic
---


## Forensic Warmup 1.
Just do what the game ask you to do. Unzip it, open the picture file and key in the flag.

---

## Forensic Warmup 2.
The file is named flag.png, but in fact it is a jpeg file. If you are on a Unix OS, just open the file normally, because on these OSes they don't infer the file type from the extension name. But if you are on Windows, rename it into flag.jpg and you can open it normally

---

## Recovering from the snap
The problem starts with a .dd file. Running `bash~file` on it reveals that the file is a raw disk image. You can mount it to see what's there. On Mac OS it's really simple, just change the extension into .dmg and open it normally, and I think it will just takes a few commands on Linux.

Anyway, if you take a look in the disk, nothing of interest will shows up. However, the hint says that some files have been deleted, so we may find the solution if we can restore these deleted files. There's a command made specifically to do this, it's called foremost. Installed it, then run the following command on the disk image file.

```bash
    foremost -t jpg -i animals.dd
```

You can learn more about `bash~foremost` by running `bash~man foremost`
The command will generate a folder called output right where you run it, which contains every image files in can recover from the disk. The flag resides in one of these images.

## 