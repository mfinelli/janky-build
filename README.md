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

## Vagrant Usage

A somewhat better approach is to run your janky build inside a vagrant box.
This is helpful if anything needs to be compiled as you can be sure that
everything will be linked against the same libraries.

Unfortunately, there is a hard requirment on folder sharing which means if
you want to use Debian Jessie you need to use the "contrib" version.
(`debian/contrib-jessie64`).

The vagrant build behaves in similar manner to the normal janky build but adds
a few extra steps. It starts by making a fresh clone of the project on the
host machine (this let's us avoid pesky issues with agent-forwarding and many
ssh identities) and copy an archive into the project root. From there we copy
the build script into the project root and launch the vagrant box. Then, just
like the normal build we run `make`, tar up the goodies and copy that archive
back to the shared folder where it will remain after clean up.

```shell
$ /path/to/janky-build/vagrant name-of-archive
```
