# Example of running Python script on CUED cluster

This directory holds a simple numpy Python program and associated job script
demonstrating the use of Python on the fear cluster. The job simply calculates
the mean of 100 normally distributed samples.

> **IMPORTANT**: Read the documentation on the [CUED wiki](http://divf.eng.cam.ac.uk/w/Main/GridEngineDocs) first.

## "Installing"

There's no installation *per se*. Simply clone:

```console
user@machine$ ssh fear
user@fear$ cd # make sure we're in the home directory
user@fear$ git -c http.sslVerify=false clone https://github.com/rjw57/fear-python-example
```

> NOTE: fear seems to have no CA certificates installed so one needs the
> insecure ``http.sslVerify=false`` option.

## Running

The ``qsub`` command submits the job:

```console
user@fear$ cd ~/fear-python-example
user@fear$ pwd # where are we?
/some/path/to/home/user/fear-python-example
user@fear$ qsub ./run_gaussianmean.sh
```

The ``qstat`` command can be used to discover when your job finishes running. At
that point you should have some files named like:
``run_gaussianmean.sh.[oe]XXXXXX``.

```console
user@fear$ qstat # no output == no jobs left to run
user@fear$ pwd # where are we?
/some/path/to/home/user/fear-python-example
user@fear$ for i in *.sh.[oe]*; do echo "$i:"; cat "$i"; done
run_gaussianmean.sh.oXXXXXXX:
<output>
run_gaussianmean.sh.eXXXXXXX:
```
