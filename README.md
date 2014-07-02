cloudsync
=========

Sync a linux filesystem incrementel and encrypted with google drive

It uses gpg2 to encrypt and decrypt the file, the filenames and all archived metadata with a passphrase.

Archived metadata are:
- filesize
- modifytime
- createtime 
- gid
- uid
- permissions

Currently only files and folders are supported. Symbolic link support is comming soon.

The filecompare is done by comparing the archived metadata. It uses a local cachefile to speedup the incremental update. The local cachefile is completly restoreable by analysing the serverside archived metadata.

It is configurable to force a cache file rebuild after <x> days.

```
Call: ./cloudsync.php [OPTION]

Required arguments for long options are also required for short options.
    -b, --backup=<path>                            Create or refresh backup of <path>
    -r, --restore=<path>                           Restore backup into <path>
    -c, --clean=<path>                             Repair 'state*.backup' file and put leftover file into <path>

    -n, --name=<name>                              Backup name
        --config=<path>                            Config file path. Default is /etc/cloudsync, ~/.cloudsync.config 
        --nocache                                  Skip 'state*.backup' file (much slower)
        --duplicate=<stop>|<update>|<rename>       Behavior on existing files:
                                                        stop - stop immediately - (default)
                                                        update - replace file
                                                        rename - extend the name with an autoincrement number

    -h, --help                                     Show this help
```
