---
layout: post
date:   2020-08-22 10:50:00 +0200
title: "Introducing Avatar-CLI"
categories:
    - "Software Engineering"
    - Tooling
tags:
    - "Avatar-CLI"
    - Docker
    - Rust
    - Tooling
---

These past weeks I've been working on a personal project called
[Avatar-CLI](https://gitlab.com/avatar-cli/avatar-cli), a cli tool meant to ease
the usage of other containerized cli programs as if they were native.

![Avatar-CLI Logo](/images/2020/20200822_avatar_logo.png){:height="340px" width="340px" display="inline" align="left" margin="0px 0px"}

Why I felt the need for such kind of tool? Well, this idea came to me around 3
years ago, while I was working in a team where some developers were using Linux,
and others were using Macos. Our development environments were quite
heterogeneous, and it was common to see problems related to each of us having
different versions of the same tools in our systems. If you are interested on
the story, you can watch this
[Youtube video](https://www.youtube.com/watch?v=zHuXnmmATHM) where I explain it.

So, let's fast forward in time to now. Avatar-CLI is cross-platform, and
provides a single statically linked binary for each system that allows us to
pinpoint versions for the software we use in our development environments,
ensuring that all members in a team are using exactly the same software.

Avatar-CLI achieves its goals by relying on Docker. But as you would expect,
Docker is just one part of it. There are a lot of small challenges in order to
achieve a smooth developer experience; file permissions, integration with
`ssh-agent`, shell integration, being able to distinguish between interactive
and non-interactive modes, dealing with package manager caches, taking into
account that docker tags are mutable references...

## Similar projects

Although by the time I came up with the idea of Avatar-CLI there was nothing
like that, I didn't really start working on it after some years, and during that
time some tools with similar purposes appeared.

[Dojo](https://github.com/kudulab/dojo) is probably one of the most known tools
among the potential competitors of Avatar-CLI, and it even appeared in the
[ThoughtWorks Technology Radar](https://www.thoughtworks.com/radar/tools/dojo).
It has been developed in Go, and presents a different set of tradeoffs, more
specifically it imposes more requirements on the OCI images that can be used
with it, but it's more mature on the side of supporting complex setups with
Docker Compose files.

["Toolbox"](ttps://github.com/containers/toolbox) is a project mostly maintained
by RedHat developers which seems to be quite serious. Its main difference with
Avatar-CLI is that it uses a single "big" container that acts as a toolbox, with
everything installed inside; while Avatar-CLI creates different containers for
each program, and uses a non containerized subshell to expose those containers
as if they were native programs.

Another project worth of mention is the
[Nix package manager](https://nixos.org/), it shares our goal of having
predictable and well defined environments (and probably it does that better than
anyone else), but its ecosystem can't compete with Docker's one when it comes to
numbers.

## A brief demo

If you want to see how it works, here there is a screencast I recorded a few
days ago:

<script id="asciicast-353664" src="https://asciinema.org/a/353664.js" async></script>

## How I'm developing Avatar-CLI

There are many aspects that I would like to talk about, but I'll try to
be succint here, and write down those things in other more specific blog posts.

### Rust as the main language

For Avatar-CLI I chose [Rust](https://www.rust-lang.org/), a strongly typed
language that compiles "native" binaries. One of the main reasons was the
ability to generate single statically linked binaries, a property that hugely
simplifies the installation and usage of Avatar-CLI, and decreases the chances
of suffering problems due to missing dependencies.

On that category of options, only C++ and [Golang](https://golang.org/) were
considered as serious contenders, but the lack of memory safety of C++, and the
lack of strong typing of Golang pushed the balance in favour of Rust.

As an unexpected benefit, I discovered that Rust's pattern matching was a very
powerful tool to ensure that I'm taking care of almost all relevant cases, which
helps me a lot to decrease the probability of suffering mysterious bugs.

### Automation

Besides the development of Avatar-CLI itself, I also had to automate many tasks
in the CI/CD pipelines. For that I chose
[Gitlab CI](https://docs.gitlab.com/ee/ci/introduction/) (that allows me to
easily use Docker-in-Docker setups) and
[Typescript](https://www.typescriptlang.org/), that made very easy to write
powerful and flexible scripts to manage the pipelines and write some git hooks.

Version numbering is generated automatically based on commit messages, and once
the code reaches the `main` branch, a new release is generated (this includes
generating Linux binaries, creating a [crates.io](https://crates.io) release and
pushing new OCI images to many registries).

### Documentation

For Avatar-CLI I decided to have a
[specific repository for documentation](https://gitlab.com/avatar-cli/aips),
where AIP (Avatar Improvement Proposal) documents will be written, follwing a
similar process to what Bitcoin has in place with its BIPs.

Right now there isn't too much stuff in there, as I focused almost all my
attention and energy on releasing something usable, but my aim is to be
exhaustive, in order to help new contributors to learn about the project
internals and why some decisions were made.

### The roadmap

Right now there is nothing written in stone, and most tasks are defined for the
near future, but you can see the short term plans in this
[kanban board](https://gitlab.com/avatar-cli/avatar-cli/-/boards).

There are other tasks that I have in mind and are not written there because they
belong to other related projects, like working on the website, or even writing
articles like this one talking about the project.

Having said that, if you want to be involved, please contact me and let me know,
I'm hoping that more people will join soon and transform Avatar-CLI into a
community project :) .