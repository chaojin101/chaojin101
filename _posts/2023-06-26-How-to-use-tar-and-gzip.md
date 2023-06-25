---
title: How to use tar and gzip
categories: ["howto"]
tags: ["linux"]
---

# gzip

## gzip compress file

```sh
touch test.txt
gzip test.txt
```

it will make `test.txt` to `test.txt.gz`

## gzip decompress file

```sh
gzip -d test.txt.gz
```

it will make `test.txt.gz` to `test.txt`

# tar

## tar compress file or folder

```sh
mkdir t
touch t/test.txt
tar -zcvf test.tar.gz test.txt
```

-z -gzip: filter the archive through gzip
-c -create: create a new archive
it will generate `test.tar.gz` file

## tar decompress file or folder

```sh
tar -zxvf test.tar.gz
```

-x -extract: extract files from an archive
it will generate `t/test.txt` file
