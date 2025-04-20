## Continuing Debian Packaging

As mentined before, we continued and finished the first tutorial of Debian Packaging and starts the second part:

1. [Tutorial de empacotamento Debian - Parte 2](https://joenio.me/tutorial-pacote-debian-parte2/)

In this part we need to choose one of lit goes alribraries and repeat what we have doned in this new library.

First of all I have choosed the ```Devel::AssertOS```, but when generating the files, it hasn't the debian directory for some reason, so I need to choose another one.

Then I tried for ```Prima```, but when I finished the startup for it, another person have already signed on it so i need to find another library, again.

Finaly, I have proceeded in the ```Perl::Critic::Plicease```.

It goes alright in the change of files and logs, but when I try to build the package, it returns this error:

```
Warning: git-pbuilder should be run via 'gbp buildpackage'
Building with pbuilder for distribution sid
W: /home/hagisf/.pbuilderrc does not exist
I: using pbuilder as pbuilder
dh clean
   dh_clean
dpkg-source: info: using source format '3.0 (quilt)'
dpkg-source: info: building libperl-critic-plicease-perl using existing ./libperl-critic-plicease-perl_0.06.orig.tar.gz
dpkg-source: error: cannot represent change to libperl-critic-plicease-perl_0.06.orig.tar.gz.delta: binary file contents changed
dpkg-source: error: add libperl-critic-plicease-perl_0.06.orig.tar.gz.delta in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: unrepresentable changes to source
```

So I need to find solution for this before next Tuesday to proceed the workshop.
