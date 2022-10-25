---
name: "Git Manual"
categories: ["Manual"]
tag: ["Manual"]
---

## username and email

set username and email
```sh
# local
git config user.name "Tim"
git config user.email "tim@gmail.com"

# global
git config --global user.name "Tim"
git config --global user.email "tim@gmail.com"
```
check username and email
```bash
git config user.name
git config user.email
cat .git/config

git config --global user.name
git config --global user.email
cat ~/.gitconfig
```