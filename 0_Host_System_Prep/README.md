# Part 0 -- Host System Preparations
#### Pre-build steps for ease of use


```
apt-get update && apt-get install -y vim lnav openssh-server linux-generic-hwe-18.04
ssh-import-id lp:katamo
```
```
sed -i 's/#HandleLidSwitch=suspend/HandleLidSwitch=ignore/g' /etc/systemd/logind.conf
sed -i 's/#HandleLidSwitchDocked=ignore/HandleLidSwitchDocked=ignore/g' /etc/systemd/logind.conf
sed -i 's/^#PermitRootLogin.*/PermitRootLogin prohibit-password/g' /etc/ssh/sshd_config
sed -i 's/^ChallengeResponseAuthentication.*/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config
sed -i 's/^#ChallengeResponseAuthentication.*/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config
```
```
cp -f /etc/skel/.bashrc /root/.bashrc
systemctl set-default multi-user.target
```
```
mkdir /etc/default/grub.d
wget -P /etc/default/grub.d/ https://raw.githubusercontent.com/KathrynMorgan/mini-stack/master/0_Host_System_Prep/aux/libvirt-grub.cfg
update-grub
```
```
reboot
```
