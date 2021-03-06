<p align="center">
  <img src="http://www.witheve.com/logo.png" alt="Eve logo" width="10%" />
</p>

---

Eve is a set of tools to help us think. Currently, these tools include: a temporal query language, a compiler, and a database.

<p align="center">
  <img src="https://github.com/witheve/assets/blob/master/images/eveclock.gif?raw=true" alt="Eve Clock" width="80%"/>
</p>

## Installation

### A Note for Windows Users

Currently, Eve only installs natively on OSX and Linux. However, Windows 10 users have two options: first, you can run Eve via Docker. To do this, follow the instructions below. The second way to run Eve on Windows 10 is via [Ubuntu on Windows](https://msdn.microsoft.com/en-us/commandline/wsl/about). Follow the linked instructions and then in a command line run `bash`. This will start a bash environment in the command line. From there, follow the rest of the Eve installation instructions as if you were installing under Ubuntu.

Unfortunately, users of earlier verision of Windows will not be able to run Eve at this time.

### From Source

Before you can install Eve you'll need need gcc, make, python, and LuaJIT.

First install gcc, make, and python using your operating system's standard channels. Chances are you already have these. Install LuaJIT by downloading [LuaJIT-2.1.0-beta2](http://luajit.org/download.html) and then in the extracted directory:

```
make
make install
```

By default, LuaJIT is not added to your path, so you'll need to do that as well:

```
ln -sf luajit-2.1.0-beta2 /usr/local/bin/luajit
```

Next you'll need to download the Eve source, either by cloning our repository

```
git clone https://github.com/witheve/Eve.git
```

or downloading the source [directly](https://github.com/witheve/Eve/archive/master.zip).

To build Eve, execute `make` in the `eve/build` directory.

### Docker

Eve is also on [Docker Hub](https://hub.docker.com/r/witheve/eve/). You can get our container with the following command:

```
docker pull witheve/eve
```

Windows Users - Docker for Windows requires Microsoft Hyper-V, which requires Windows 10. For users of earlier Windows versions, binaries are forthcoming.

## [Running](https://github.com/witheve/docs/blob/master/src/handbook/running.md)

### Native

To run Eve, execute the following command in the `eve/build` directory:

`./eve`

This command launches a server hosted at `http://localhost:8080`. You can access the Eve editor by directing your browser to that address. We recommend using Chrome, since we haven't tested on other browsers. You can configure the port with the `--port` flag e.g. `./eve --port 1234`.

If you want to compile an existing program, use the `-e` flag and provide a path to a `*.eve` file e.g. `./eve -e ../examples/tic-tac-toe.eve`. As you make changes in the editor, they will be reflected back into this file.

### Docker

To run the Docker container, execute:

```
docker run -p [port]:8080 witheve/eve [eve_file]
```

`[port]` is an available port on your local machine. It can be `8080` or any other port you would like. Then direct your browser to `http://localhost:[port]` to access the editor.

`[eve_file]` is a path to a `*.eve` file you would like to build. The working directory of the container is `eve/build`, so to run a program in the `eve/examples` directory, you need to provide a relative path e.g. 

```
docker run -p 8080:8080 witheve/eve ../examples/clock.eve
```

To pass Eve files on your local machine into the container, you'll need to mount a [docker volume](https://docs.docker.com/engine/tutorials/dockervolumes/). 

## How to use Eve

You can learn about Eve through the following resources:

- [Eve Quick Start Tutorial](https://github.com/witheve/docs/blob/master/src/guides/quickstart.md) (draft)
- [Syntax Quick Reference](https://witheve.github.io/assets/docs/SyntaxReference.pdf) (draft)
- [Eve Language Handbook](https://github.com/witheve/docs/blob/master/src/handbook/contents.md) (draft)

*Please let us know what kind of documents would be the most helpful as you begin your journey with Eve*. We want our documentation to be a highlight of the Eve experience, so any suggestions are greatly appreciated.

## Get Involved

### Join the Community

The Eve community is small but constantly growing, and everyone is welcome!

- Join our [mailing list](https://groups.google.com/forum/#!forum/eve-talk) and get involved with the latest discussions on Eve.
- Impact the future of Eve by getting involved with our [Request for Comments](https://github.com/witheve/rfcs) process.
- Read our [development diary](http://incidentalcomplexity.com/).
- Follow us on [twitter](https://twitter.com/with_eve).

### How to Contribute

The best way to contribute right now is to write Eve code and report your experiences. Let us know what kind of programs you’re trying to write, what barriers your are facing in writing code (both mental and technological), and any errors you encounter along the way. Also, let us know what you love! What features are your favorite?

Another way to really help us is to host your `*.eve` files on Github, so we can get Eve recognized as an official language in the eyes of Github. Be sure to also send us a link to your repo!

### How to File an Issue

Please file any issues in this repository. Before you file an issue, please take a look to see if the issue already exists. When you file an issue, please include:

1. The steps needed to reproduce the bug
2. Your operating system and browser.
3. If applicable, the .*eve file that causes the bug.

## License

Eve is licensed under the Apache 2.0 license, see [LICENSE](https://github.com/witheve/eve/blob/master/LICENSE) for details.

## Disclaimer

Eve is currently at a very early, "pre-alpha" stage of development. This means the language, tools, and docs are largely incomplete, but undergoing rapid and continuous development. If you encounter errors while using Eve, don't worry: it's likely our fault. Please bring the problem to our attention by [filing an issue](https://github.com/witheve/eve#how-to-file-an-issue).

As always, with pre-release software, don’t use this for anything important. We are continuously pushing to this codebase, so you can expect very rapid changes. At this time, we’re not prepared make the commitment that our changes will not break your code, but we’ll do our best to [update you](https://groups.google.com/forum/#!forum/eve-talk) on the biggest changes.
