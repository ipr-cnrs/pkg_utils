# PKG_UTILS

1. [Overview](#overview)
2. [Role Variables](#role-variables)
     * [OS Specific Variables](#os-specific-variables)
3. [Example Playbook](#example-playbook)
4. [Packages](#packages)
5. [Development](#development)
5. [License](#license)
6. [Author Information](#author-information)

## Overview

Manage some packages from 'utils' section (Apt).

## Role Variables

* **pkg_utils_new_state** : State of new pkg_utils packages [default : `latest`].

### OS Specific Variables

Please see default value by Operating System file in [vars][vars directory] directory.

* **pkg_utils_new_list** : The list of packages to install to provide `pkg_utils`.

## Example Playbook

* Use defaults vars :

``` yml
- hosts: serverXYZ
  roles:
    - role: ipr-cnrs.pkg_utils
```

## Packages

### New Packages
* **bdsmainutils** : Collection of more utilities from FreeBSD.
* **colordiff** : Tool to colorize 'diff' output.
* **cpio** : GNU cpio; a program to manage archives of files.
* **debian-goodies** : Small toolbox-style utilities for Debian systems.
  * Show which installed packages occupy the most place :

``` sh
dpigs
```

* **htop** : Interactive processes viewer.
* **lsof** : Utility to list open files (eg. useful to redirect stdout).
* **lzip** : Lossless data compressor based on the LZMA algorithm.
* **mlocate** : Quickly find files on the filesystem based on their name.
* **moreutils** : Additionnal Unix utilities.
  * `vidir` : Edit directory content as a file with vim
* **multitail** : View multiple logfiles windowed on console :

``` sh
sudo multitail /var/log/auth.log /var/log/syslog
sudo multitail -s 2 /var/log/auth.log /var/log/syslog /var/log/mail.log
```

* **tmux** : Terminal multiplexer.
* **tree** : Displays an indented directory tree,in color.
* **unrar** : Unarchiver for .rar files (non-free version).
* **unzip** : De-archiver for .zip files.
* **vim-nox** : Vi IMproved - enhanced vi editor - with scripting languages support.
* **vim-doc** : Vi IMproved - HTML documentation.
* **vim-scripts** : Plugins for vim, adding bells and whistles.
* **zip** : Archiver for .zip files.
* **zsh** : Shell with lots of features.

## Development

This source code comes from our [Gogs instance][pkg_utils source] and the [Github repo][pkg_utils github] exist just to be able to send the role to Ansible Galaxy…

But feel free to send issue/PR here :)

Thanks to this [hook][gogs to github hook], Github automatically got updates from our [Gogs instance][pkg_utils source] :)

## License

[WTFPL][wtfpl website]

## Author Information

Jérémy Gardais
* Source : [on IPR's Gogs][pkg_utils source]
* [IPR][ipr website] (Institut de Physique de Rennes)

[vars directory]: ./vars
[gogs to github hook]: https://stackoverflow.com/a/21998477
[pkg_utils source]: https://git.ipr.univ-rennes1.fr/cellinfo/ansible.pkg_utils
[pkg_utils github]: https://github.com/ipr-cnrs/pkg_utils
[wtfpl website]: http://www.wtfpl.net/about/
[ipr website]: https://ipr.univ-rennes1.fr/
