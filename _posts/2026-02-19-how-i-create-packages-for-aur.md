---
layout: post
title: "How I set up packages for AUR"
---

Recently, I often found myself maintaining packages in AUR. That's why I made
my mind to write down a blog post about how the process goes.

## Table of contents
- [Quick review](#quick-review)
- [Finding packages](#finding-packages)
- [Creating the PKGBUILD](#creating-the-pkgbuild)
- [Testing locally](#testing-locally)
- [Uploading to AUR](#uploading-to-aur)
- [Conclusion](#conclusion)

## [Quick review](#quick-review)

For those who don’t know, AUR (Arch User Repository) is a community-driven
repository for Arch Linux users. It allows anyone to contribute PKGBUILDs —
scripts that automate building and installing packages. Maintaining AUR packages
is a way to share software that isn’t in the official repos and also helps you
learn a lot about Linux packaging.

## [Finding packages](#finding-packages)

The first step is deciding which software to package. I usually browse GitHub or
other repositories to see projects that are not actively maintained or lack
Arch packages. I often find small utilities, CLI tools, or interesting software
that could benefit from an AUR package.

## [Creating the PKGBUILD](#creating-the-pkgbuild)

The PKGBUILD is the heart of any AUR package. It defines metadata, sources,
dependencies, and instructions for building the software. When creating one,
I usually start by looking at similar packages in AUR to see how others have
structured theirs — it gives me a solid reference and saves time.

I also rely heavily on ArchWiki[^1] and related blog posts. Their examples and
guides are incredibly detailed and often guide me step by step, especially
when handling tricky build steps or uncommon dependencies.

[^1]: Here are useful ones: [PKGBUILD - ArchWiki](https://wiki.archlinux.org/title/PKGBUILD), [Creating packages - ArchWiki](https://wiki.archlinux.org/title/Creating_packages)

Tools like `namcap` are great to check the PKGBUILD for common errors and warnings.

## [Testing locally](#testing-locally)

Before uploading, I always build and install the package locally using:

```bash
makepkg -si
```

This ensures the package installs correctly and works as expected.


## [Uploading to AUR](#uploading-to-aur)

Once the package is ready, uploading it to AUR is straightforward.

Since I have already added my SSH public key to my AUR account, pushing
changes is very convenient and secure. I don’t need to enter my credentials
every time — Git handles authentication through SSH.

The usual workflow looks like this:

```bash
git clone aur@aur.archlinux.org:<pkgname>.git
cd <pkgname>
makepkg --printsrcinfo > .SRCINFO
git add PKGBUILD .SRCINFO
git commit -m "feat: init"
git push
```

## [Conclusion](#conclusion)

Maintaining AUR packages has been a great learning experience. Not only does it
help me and other Arch users, but it also gives insight into Linux packaging,
version control, and software distribution. If you are an Arch user interested
in contributing, starting your own AUR package is a great way to dive in.

