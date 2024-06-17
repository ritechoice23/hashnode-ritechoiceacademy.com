---
title: "How to install and update NodeJs in Ubuntu."
datePublished: Fri Jan 12 2024 15:55:01 GMT+0000 (Coordinated Universal Time)
cuid: clratkmb7000y09iabbmu25do
slug: how-to-install-and-update-nodejs-in-ubuntu
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/xbEVM6oJ1Fs/upload/e980ff3a61b3e8620abecd5eaa91498a.jpeg
tags: ubuntu, javascript, nodejs, npm

---

I will share in the short term how you can install and update NodeJs on the Ubuntu machine.

As simple as the concept I will be sharing is, I had a hard time with it some time ago.

## Install NodeJs

```bash
 sudo apt install nodejs
```

now that you have installed NodeJs, you may need to check the version of what you have installed.

### Check Node Version

```bash
node -v
```

### Check NPM Version

```bash
npm -v
```

## Updating NodeJs

there are many ways to do this, but I will explain the simplest and the shortest way.

```bash
sudo npm install -g n
sudo n lts
```

The above command helps you update your version of Node and npm, if you need to read more about updating or installing NodeJs you can [read more here](https://nodejs.org/en/download/package-manager).