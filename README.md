# termux-runit
Playground for runit in termux

`servicedir` is the directory under which the
runit scripts are located.

```
servicedir
├── config
├── log
│   ├── config
│   └── run
└── run
```

`servicedir/run`: contains the exec script for the
daemon
`servicedir/config`: contains the environment variables
and is referenced in the `servicedir/run` script
`servicedir/log/run`: contains the logger daemon that
takes in (via pipe) the stdout of the `servicedir/run` process
`servicedir/log/config`: contains the logger daemon's configs (?)
