# termux-runit
Playground for runit in termux

`testrunit` is the directory under which the
runit scripts are located.

```
testrunit
├── run
├── conf
└── log
    └── run
```

`testrunit/run`: contains the exec script for the
daemon.
That file must be executable (aka, `$ chmod +x ./run`)
Also, if this file is going to call another script,
as it does in this repo, that script, too, must be executable.

`testrunit/conf`: contains the environment variables
that are referenced in the `testrunit/run` script.

`testrunit/log/run`: contains the logger daemon that
takes in (via pipe) the stdout of the `testrunit/run` process.
Like the `testrunit/run` file, this file, too, must be executable.


## Where to place the directory

You should first copy the `testrunit` dir to your termux.
You can do this via ssh+rsync, or via using USB-drive between
your computer and your phone, or any other method you are comfortable
with.

Once the `testrunit` dir is on your termux, move that to `~/.config/sv/`
directory.

## How to enable the service

After that, create symbolic links to $SVDIR:

$ ln -s ${HOME}/.config/sv/testrunit ${PREFIX}/var/service/
$ sv-enable testrunit

## How to manage the service

Check its status

$ sv status testrunit

Stop the service

$ sv stop testrunit

Start the service

$ sv start testrunit

Remove the service 

$ unlink ${PREFIX}/var/service/testrunit
