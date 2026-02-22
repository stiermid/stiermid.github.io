---
layout: post
title: "How I set up packages for AUR"
---

Recently, I often found myself maintaining packages in AUR. That's why I made
my mind to write down a blog post about how the process goes.

## Quick review

For those who don’t know, **AUR** *(Arch User Repository)* is a community-driven
repository for Arch Linux users. It allows anyone to contribute **PKGBUILD**s —
scripts that automate building and installing packages. Maintaining **AUR** packages
is a way to share software that isn’t in the official repos and also helps you
learn a lot about Linux packaging.

## The process

As it is described [here](https://wiki.archlinux.org/title/Creating_packages#Summary), 
the things we need to accomplish are basically:

1. Download the source tarball of the software to package.
1. Try compiling the package and installing it into an arbitrary directory.
1. Copy over the prototype **/usr/share/pacman/PKGBUILD.proto** and rename it to 
**PKGBUILD** in a temporary working directory.
1. Edit the **PKGBUILD** according to the needs of your package.
1. Run makepkg and check whether the package builds correctly.
1. If not, repeat the previous two steps.


## Creating the PKGBUILD

**Arch Linux** is also famous for its rich and well-documented wiki. It's hard to
overstate how overstate until you've actually had to rely on it for complex
packaging tasks.

Especially, articles such as
[PKGBUILD - ArchWiki](https://wiki.archlinux.org/title/PKGBUILD), 
[Creating packages - ArchWiki](https://wiki.archlinux.org/title/Creating_packages) 
assists the creating of package a lot.

## Testing the package

Before pushing **PKGBUILD** to the **AUR**, we have to ensure our package is working
correctly, I mean built correctly. To do so, I often do

```bash
makepkg -si
```

This builds and installs the package with its dependencies.

Tools like [namcap](https://man.archlinux.org/man/namcap.1.en.txt) and 
[pkgctl](https://man.archlinux.org/man/pkgctl.1.en.txt) are also very handy.

- **namcap** - basically checks for the syntax issues in the PKGBUILD file.
- **pkgctl** is a bit interesting. Using **pkgctl**, we are able to test out package
for build and dependency issues in sandboxed environment.

## Publishing

Once the package is ready, uploading it to **AUR** is straightforward.

Since I have already added my SSH public key to my AUR account, pushing
changes is very convenient and secure. I don’t need to enter my credentials
every time — Git handles authentication through SSH.

```bash
git clone aur@aur.archlinux.org:<pkgname>.git
cd <pkgname>
makepkg --printsrcinfo > .SRCINFO
git add PKGBUILD .SRCINFO
git commit -m "feat: init"
git push
```

## Summary

Maintaining AUR packages has been a great learning experience. Not only does it
help me and other Arch users, but it also gives insight into Linux packaging,
version control, and software distribution. If you are an Arch user interested
in contributing, starting your own AUR package is a great way to dive in.
