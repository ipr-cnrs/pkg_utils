# PKG_UTILS

1. [Overview](#overview)
2. [Role Variables](#role-variables)
     * [OS Specific Variables](#os-specific-variables)
3. [Example Playbook](#example-playbook)
4. [Packages](#packages)
    * [New Packages](#new-packages)
    * [Unwanted Packages](#unwanted-packages)
5. [Configuration](#configuration)
    * [Default Editor](#default-editor)
    * [Updatedb](#updatedb)
6. [Development](#development)
7. [License](#license)
8. [Author Information](#author-information)

## Overview

Manage some packages installation and configuration from 'utils' section (Apt).

## Role Variables

* **pkg_utils_new_state** : State of new pkg_utils packages [default : `installed`].
* **pkg_utils_old_manage** : If this role should manage unwanted packages [default : `true`].
* **pkg_utils_old_state** : State of useless pkg_utils [default : `absent`].
* **pkg_utils_default_editor_name** : The default editor name [default : `vim.nox`].
* **pkg_utils_default_editor_path** : The default editor path [default : `/usr/bin/vim.nox`].
* **pkg_utils_default_editor_manage** : If the default editor should be managed [default : `true`].
* **pkg_utils_updatedb_conf_path** : Configuration file for **updatedb** [default : `/etc/updatedb.conf`].
* **pkg_utils_updatedb_conf_tpl** : Template used to generate the previous config file [default : `etc/updatedb.conf.j2`].
* **pkg_utils_updatedb_prune_bind_mounts** : Whether or not bind mounts are scanned [default: `true`].
* **pkg_utils_updatedb_prunenames** : A list of directory names (without paths) which should not be scanned [default: `[.bzr, .git, .hg, .svn]`].
* **pkg_utils_updatedb_prunepaths** : A list of path names of directories which should not be scanned [default: `[/media, /mnt, /tmp, /var/lib/ceph, /var/spool]`].
* **pkg_utils_updatedb_prunefs** : A list of file system types (as used in /etc/mtab) which should not be scanned [default: `[afs, autofs, binfmt_misc, ceph, cifs, coda, curlftpfs, devfs, devpts, devtmpfs, ecryptfs, fuse.glusterfs, fuse.sshfs, fusesmb, iso9660, lustre, lustre_lite, mfs, ncpfs, NFS, nfs, nfs4, proc, rpc_pipefs, shfs, smbfs, sysfs, ftpfs, tmpfs, udf, usbfs]`].

### OS Specific Variables

Please see default value by Operating System file in [vars][vars directory] directory.

* **pkg_utils_new_list** : The list of packages to install to provide `pkg_utils`.
* **pkg_utils_old_list** : The list of unwanted packages to remove.

## Example Playbook

* Use defaults vars :

``` yml
- hosts: serverXYZ
  roles:
    - role: ipr-cnrs.pkg_utils
```

* Don't remove any packages :

``` yml
- hosts: serverXYZ
  roles:
    - role: ipr-cnrs.pkg_utils
      pkg_utils_old_manage: false
```

## Packages

### New Packages
* **apt-transport-https** : https download transport for APT.
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

### Unwanted Packages
* **vim-tiny** : Compact version of vim editor.

## Configuration

### Default Editor

* Set the *pkg_utils_default_editor.name* var [default : `vim.nox`] as the default editor on the system.

### Updatedb

Based on the [Oefenweb module][oefenweb ansible updatedb], thanks !

* Set the default configuration file for *updatedb* and update the database for Mlocate with an handler.
* Ensure to not scan some path, directories and filesystem.

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
