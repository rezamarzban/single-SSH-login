# single-SSH-login
Single SSH login per user

# Instruction guide

Place the `limit.sh` file into `/root` folder, Then add below lines to the end of `/etc/pam.d/sshd` file and restart the service or reboot:
```
account required pam_exec.so /root/limit.sh
auth required pam_exec.so /root/limit.sh
```

To adding an user as limited user run below command:
```
adduser example_user --shell=/bin/false --no-create-home
```
