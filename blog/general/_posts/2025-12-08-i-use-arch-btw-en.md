---
layout: post
lang: en
title: "I use Arch, btw"
intro: "I finally made time and decided to migrate my whole workflow to Arch. My experience moving to Arch Linux (and Wayland) after 8 years on Debian."
date: 2025-12-08 20:29:02 -0300
categories: general
toc: true
hero: /25-12-08/header.jpg
permalink: /en/blog/general/2025/12/08/i-use-arch-btw.html
translation: /blog/general/2025/12/08/i-use-arch-btw.html
---

## My history with Debian
My Linux story begins with Fedora Core 3 and a bit of Solaris 10 back in
2005. Very soon after, I started distro hopping like everybody else. By 2010 I had settled quite comfortably into Ubuntu for the next 7/8 years.
Over time, I felt the operating system should be more
customized to my taste, without the distributor installing packages I would never
use. Since I had already gained plenty of experience managing
servers, one fine day I decided on a minimal Debian install and adding all the
packages I was actually going to use. From that point on, I started creating scripts,
programs and keyboard shortcuts tailored to my needs.

And just like that, 8 years went by. I only reinstalled once, when I
upgraded the computer.

## Debian's problems
Debian is a super solid system, nobody can argue with that. But that
comes with an inherent problem: the software is generally old too, since the only
way to confirm robustness is, precisely, the passage of time. One way I found to get
the best of both worlds (solidity and up-to-date software) was to
compile from source every program I needed to keep
updated: alacritty, ghostty, tmux, nvim, etc. And for a while, it worked.

I created a repository and, through scripts, automated the whole process _à la_ [OpenBSD
ports](https://www.openbsd.org/faq/ports/ports.html). The problem showed up
with the new demands of artificial intelligence projects. I wanted to try out models or projects and they generally
needed updated system libraries. The alternative I found was
moving to the [unstable branch (Sid)](https://wiki.debian.org/DebianUnstable). But even then,
it sometimes wasn't enough, and other times I actually broke the system. Nothing I couldn't
fix, but it was something that was starting to wear on me.

## Tearing down myths
I have to confess I had my prejudices about Arch. Some of them well-founded (an
unstable system) and others completely unfounded (hard to install). The second
myth is probably what delayed the migration the most, because I don't like wasting time
on things that aren't worth it. I'll talk about stability later on.

After watching a couple of videos about
installing Arch — and [Omarchy](https://omarchy.org) in particular — I realized it isn't very
different from installing Debian. I don't use Omarchy, but the base
installation of the operating system is the same. Here's how to install it in case
you want to give it a try.

<a href="https://youtu.be/6YJImMYKefk" class="lazy-youtube-embed">Omarchy Install</a>

The installation was tremendously easy and fast. As it should be. On a fresh
installation there shouldn't be any kind of problem. In my case, I also have a
Windows 10 install (which auto-magically upgraded itself to 11 🤮)...
But since I've had several bad experiences, I keep the systems
separated on different disks, and the `/home` partition also lives on another
disk. That way, I run no risk of deleting something I shouldn't. So I
guess part of that simplicity comes from having everything neatly organized.

## The Nvidia miracle
What surprised me most about the installation was that it let me install the
proprietary Nvidia drivers directly. Maybe it's because Debian is rather
protective about drivers that aren't open source, but it was always a struggle
for me. DKMS this, kernel headers that, etc, etc... But on Arch it was
extremely easy. Pick the driver model matching my GPU and
done. It installed all the drivers and configured the kernel correctly (chef's
kiss).

## Bye X11, hello fluidity
Ever since I installed the minimal version of Debian, I've been using tiling
window managers. I went through [i3](https://i3wm.org/), [dwm](https://dwm.suckless.org/)
and finally settled on [bspwm](https://wiki.archlinux.org/title/Bspwm).
All of these running on X11. Since I'd also been wanting to see how
Wayland performed for a while, I decided to install [Hyprland](https://hypr.land/).

Honestly, in the time I've been using it, it has blown my mind. Everything runs
much faster. The [Zen browser](https://zen-browser.app/), which had
performance issues on YouTube, suddenly seems like a fork of Chrome (if that
comparison is worth anything). The other thing was screen tearing... After years of fighting
without a favorable outcome against Compton's configuration (an X11 compositor),
videos finally render without a single artifact.

![Zen Browser](https://zen-browser.app/_astro/ComImage.DV0rTSHO_BBUc2.webp)

## Uptime: 100%
The best part of all? The whole installation process took no more than half an
hour one Sunday, and migrating all the shortcuts a few hours more. Only because I
took the time to polish some scripts I had been procrastinating on.

In conclusion: after 3 weeks of sailing into new waters, I feel more at home than
ever. Everything works the way I want and I haven't had a single problem with
anything. I definitely should have made this decision earlier, but hey!
It's never too late.
