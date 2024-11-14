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

For better experience (30 seconds ssh inactivity check instead of long time check) add below lines to the `/etc/ssh/sshd_config` file:
```
ClientAliveInterval 10
ClientAliveCountMax 3
```

Or, Quick run:

```
echo "
ClientAliveInterval 10
ClientAliveCountMax 3
" >> /etc/ssh/sshd_config
```

Also you can run below command inorder to better using ssh direct app client:
```
 ufw allow 7300
```
