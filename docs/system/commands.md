# Set of useful commands on Linux

## systemctl
- To start/stop/restart/disable/enable/ a service
    - ```systemctl <cmd> <service_name>```
    - eg : ```systemctl disable tftp-hpa.service```

## git
### git remote
- list remotes : `git remote -v`
- add remote : `git remote add <remote name> <url>`
- push/pull/fetch to a remote : 
    - `git push/pull/fetch <remote> <branch>` 
    - eg `git push shdrmr test-branch`

## Misc
#### Find path of binary
`which <binary name>`
#### Find size of directory
- Run `du -sh <dir>`
- To get size in megabytes/kilobytes/byte:
    - `du -shm <dir>`
    - `du -shk <dir>`
    - `du -shb <dir>`

