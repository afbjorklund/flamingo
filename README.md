# Flamingo

[![Travis Widget]][Travis] [![Coverage Widget]][Coverage] [![Documentation Widget]][Documentation] [![Waffle Widget]][Waffle]

[Travis Widget]: https://travis-ci.org/tmrts/flamingo.svg?branch=master
[Travis]: http://travis-ci.org/tmrts/flamingo
[Coverage Widget]: https://coveralls.io/repos/tmrts/flamingo/badge.svg?branch=master&service=github
[Coverage]: https://coveralls.io/github/tmrts/flamingo?branch=master
[Documentation Widget]: https://godoc.org/github.com/tmrts/flamingo?status.png
[Documentation]: https://godoc.orgp/github.com/tmrts/flamingo
[Waffle Widget]: https://badge.waffle.io/tmrts/flamingo.png?label=ready&title=Ready
[Waffle]: https://waffle.io/tmrts/flamingo

![Flamingo Logo](/logo.png)

*Flamingo* is a lightweight contextualization tool that aims to handle
initialization of cloud instances.

It is meant to be a replacement for [cloud-init] in [Atomic Host], a lightweight
operating system designed to run applications in Docker containers with
orchestration capabilities ([Kubernetes]). It has 3 different
flavors; [Fedora], [RHEL], and [CentOS].

For more details please check [Introducing Flamingo]

# Goals
The aim of this project is to create a **fast**, **extensible**, **documented**
tool to use

## Why not use cloud-init?

- In order for an image to be built with cloud-init as its contextualization tool,
 it needs to contain the python interpreter, it's dependencies and the dependencies of
 cloud-init. It fattens up the image and increases complexity for the distributions.
- Due to the dynamic nature of scripting languages they are slow. In an I/O boud
application this is not a big problem however initializing VM images, is different.
- The documentation is lacking at best. The tests are inadequate and it is a big chunk
of initialization scripts. Making it hard to work with cloud-init as a developer and
maintainer.

## Solution

- Golang excels at building big applications (e.g. distributed computing).
  It provides the necessary tooling for the job. It doesn't have long
  dependency chains like interpreted languages and it is fast.

- *Flamingo* will essentially be a single binary coupled with all of its
  dependencies. In addition, cloud images will be smaller as well.

- Testability, Documentation and Extensibility is heavily emphasized in *Flamingo*.

## Installation

You can find the latest source `RPM` releases [here](https://github.com/tmrts/flamingo/releases/latest)

For **fedora**, you can also use the `copr` repository
``` bash
dnf copr enable tamertas/flamingo
dnf install flamingo
```

## Configuration

`Flamingo` supports configuration through `cloud-config` files similar to
`cloud-init`.

It supports a subset of `cloud-init` `cloud-config`.

## Discussions
If you'd like to contribute, learn more, or share your opinions
please feel free to open an issue, mail to [centos-devel], [atomic],
user-list or come to [#atomic](irc://irc.freenode.net/#atomic-devel) and [#centos-devel](irc://irc.freenode.net/#centos-devel) irc channels to have a chat.

[Introducing Flamingo]: http://tmrts.com/blog/flamingo-a-lightweight-cloud-instance-contextualization-tool/
[cloud-init]: http://cloudinit.readthedocs.org/en/latest/
[Kubernetes]: http://kubernetes.io
[Atomic Host]: http://projectatomic.io
[Fedora]: http://www.projectatomic.io/download/
[CentOS]: http://www.projectatomic.io/download/
[RHEL]: http://www.projectatomic.io/download/
[centos-devel]: https://lists.centos.org/mailman/listinfo/centos-devel
[atomic]: https://lists.projectatomic.io/mailman/listinfo/atomic
