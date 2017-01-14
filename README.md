# Janky Build

When you can't afford a real server but need some build artifacts.

## Simple usage

Clone the `jnaky-build` repository somewhere on your local machine. Then,
run the `build` command passing the desired name of the final archive:

```shell
$ /path/to/janky-build/build name-of-archive
```

This will clone the repository (`origin` remote) and runs `make`. It will
automatically remove the `.git` directory and then `tar` and `gzip` the
resulting directory and copy the archive back into the starting directory
before cleaning the temporary files up.
