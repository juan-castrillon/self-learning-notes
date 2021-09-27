---
title:  Backup and Compressing
parent: Files
grand_parent: Linux
---

# Backing Up

- To back up data, it can be done simply with `cp` or with more robust tools like `rsync`

## `rsync`
- Only copies files if they were modified
- Only copies modified part(very fast)
- Can be used to store in remote machines
- Using the `-r` flag, directories can be copied recursively
  
Recommended is for example
```sh
rsync --progress -avrxH  --delete sourcedir destdir
```

## `dd`
- Can be used for copying raw disk data or making copies or raw disk space
- Is very powerful and should be used carefully


# Compressing

Made in order to reduce filesize (disk and faster over network)

## `gzip`
- Most used in linux
- Examples:
```bash
gzip * #Compresses every file in the pwd. Same name + .gz
gzip -r folder #Compresses everything in folder and adds it to folder.gz
gunzip a #Decompresses a found in a.gz
gzip -d a #Same as above
``` 

## `bzip2`
- Produces smaller files than `gzip` but takes longer
- Used for big files
- Is now **Deprecated**, and `xz` should be used instead
- Examples
```bash
bzip2 * #Every file in the pwd with the .bz2 extension
bunzip2 a.bz2 #Decompresses a in a.bz2
bzip2 -d *.bz2 #Same as above
```

## `xz`
- Most space efficient compression utility used in Linux
- Used for kernel files
- Examples:
```bash
xz * #Every file in the pwd, replaced with a .xz
xz foo #Compresses foo into foo.xz and deletes foo if successful
xz -dk foo.xz #Decompresses foo.xz and keeps the file
```

## `zip`
- Not very used in Linux
- Used mostly when receiving/sending files to windows
- Examples
```bash
zip backup * #All files in pwd into backup.zip
zip -r backup.zip ~ #Stores home directory into backup.zip recursively
unzip backup.zip #Extracts all files and puts them in pwd 
```

## `tar`
- Using for putting together (or extracting) for archive files or "tarballs"
- Compressing/Decompressing can be done at the same time
- Examples:
```bash
tar -xvf dir.tar #Extracts files from dir.tar into dir
tar -zcvf mydir.tar.gz mydir #Create a tarball and compress it with gzip
tar -jcvf mydir.tar.bz2 mydir #Create a tarball and compress it with bz2
tar -Jcvf mydir.tar.xz mydir #Create a tarball and compress it with xz
tar -xvf mydir.tar.gz #Extract files into the mydir directory
```