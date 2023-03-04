# TFTP Setup

Source : https://www.makeuseof.com/set-up-tftp-server-on-linux/

- Create a directory to act as the root of the tftp server file system. Example: `~/tftp_dir`
- Install tftp-hpa package
    - `sudo apt-get install tftpd-hpa`
- This should create a file `/etc/default/tftpd-hpa`. 
- Edit entry `TFTP_DIRECTORY` and place your folder there.
- It should look something like this
```
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/home/sharan/work_projects/tftp_dir"
TFTP_ADDRESS=":69"
TFTP_OPTIONS="--secure"
```
- Restart tftp service
    - `sudo systemctl restart tftpd-hpa.service`
- Check the status
    - `sudo systemctl status tftpd-hpa.service`