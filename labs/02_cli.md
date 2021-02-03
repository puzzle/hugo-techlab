# Lab 2: Install the Hugo CLI

As the client is written in Go, you can run the single binary on the following Operating Systems:

- Linux
- MacOS
- Windows

## Download `hugo`

The easiest way to install Hugo is by [downloading the binary from Github](https://github.com/gohugoio/hugo/releases) and moving it into `~/bin`. Pick the release for your operating system. You probably have 64bit.

However there are also [other ways of installing Hugo](https://gohugo.io/getting-started/installing).

### Set the the right file modes on Linux and MacOS

If you downloaded the binary from Github, then make sure it is executable:

```
cd ~/bin
chmod +x hugo
```

## Verify installation

The `hugo` binary should now be correctly installed. Check by running the following command:

```
$ hugo version
```

The shown output should look similar to this:

```
Hugo Static Site Generator v0.74.2 linux/amd64 BuildDate: unknown
```

If you don't see a similar output, possibly there are issues with the set PATH variable. Try moving Hugo to `/usr/local/bin`:

```
sudo mv hugo /usr/local/bin
```
If that still does not work check `echo $PATH` or run with `./hugo`.


---

## bash completion (optional)

On most linux systems you have to install the bash-completion packet to make the completion work.

Ubuntu:
```
sudo apt install bash-completion
```

Activate bash completion by running the following command:
```
$ sudo hugo gen autocomplete
```

zsh is currently not supported.


---

**End of lab 2**

<p width="100px" align="right"><a href="03_first_steps.md">First steps in the lab environment →</a></p>

[← back to the overview](../README.md)
