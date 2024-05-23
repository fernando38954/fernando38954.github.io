## New Error of Debian Packaging

Today I deleted everything I had done before and started Debian packaging again from scratch.

Surprisingly, the previously reported error disappeared but now new errors appeared:
```
  E: libperl-critic-plicease-perl: dir-or-file-in-home [home/hagisf/]
  N:
  N:   Debian packages should not install into /home, because it is reserved for
  N:   users.
  N:
  N:   Visibility: error
  N:   Show-Always: no
  N:   Check: files/hierarchy/standard
  N:
  N:
  E: libperl-critic-plicease-perl: dir-or-file-in-home [home/hagisf/perl5/]
  N:
  E: libperl-critic-plicease-perl: dir-or-file-in-home [home/hagisf/perl5/lib/]
  N:
  E: libperl-critic-plicease-perl: dir-or-file-in-home ... use "--tag-display-limi
  t 0" to see all (or pipe to a file/program)
```
 And when I ignored it proceding in nexts steps, the codes
 ```
  mk-sbuild sid
  autopkgtest . -- schroot sid-amd64
```
Returns error
```
  autopkgtest . - schroot sid-amd64
  autopkgtest [20:45:01]: starting date and time: 2024-05-22 20:45:01-0300
  autopkgtest [20:45:01]: version 5.34
  autopkgtest [20:45:01]: host debian; command line: /usr/bin/autopkgtest . -- schroot sid-amd64
  ['schroot', '--config', '--chroot', 'sid-amd64'] failed (exit status 1, stderr
  W: No chroots are defined in /etc/schroot/schroot.conf' or '/etc/schroot/chroot
  .d'\nE: sid-amd64: Chroot not found\n')
  autopkgtest [20:45:01]: ERROR: testbed failure: unexpected eof from the testbed
```
So seaching from solutions... Again...
