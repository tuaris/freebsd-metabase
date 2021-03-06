Metabase for FreeBSD
=====

Metabase for FreeBSD.
http://metabase.com

## Using with Portshaker

Create a file `/usr/local/etc/portshaker.d/metabase` with the following contents.
```
#!/bin/sh
. /usr/local/share/portshaker/portshaker.subr
method="git"
if	[ "$1" != '--' ]; then
	err 1 "Extra arguments"
fi
shift
git_clone_uri="https://github.com/tuaris/freebsd-metabase.git"
git_branch="master"
run_portshaker_command $*
```

Then add **metabase** to your **_merge_from** line in `/usr/local/etc/portshaker.conf`.  For example.

```
#---[ Base directory for mirrored Ports Trees ]---
mirror_base_dir="/var/cache/portshaker"

#---[ Directories where to merge ports ]---
ports_trees="default"

use_zfs="yes"
poudriere_dataset="poudriere/poudriere"
poudriere_ports_mountpoint="/usr/local/poudriere/ports"
default_poudriere_tree="default"
default_merge_from="ports metabase"
```

