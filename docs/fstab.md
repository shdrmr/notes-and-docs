# Sample fstab

```
/dev/root            /                    auto       defaults              1  1
proc                 /proc                proc       defaults              0  0
devpts               /dev/pts             devpts     mode=0620,gid=5       0  0
tmpfs                /run                 tmpfs      mode=0755,nodev,nosuid,strictatime 0  0
tmpfs                /var/volatile        tmpfs      defaults              0  0

# user data partition
/dev/mmcblk1p< partition num > /userdata  ext4    rw,suid,dev,exec,auto,nouser,sync       0       0
```

### Make rootfs readonly
- Run command:
    - `sed -i '/root/{s/\bdefaults\b/ro/}' /etc/fstab`
    - basically change keyword `defaults` to `ro`

### Make rootfs readwrite
- Run command
    - `sed -i '/root/{s/\bro\b/defaults/}' /etc/fstab`
    - basically change keyworkd `ro` to `defaults`