[![logo](https://i0.wp.com/homesecurity1st.co.za/wp-content/uploads/2017/02/TP-LINK_logo-300x130-1.jpg?fit=300%2C130&ssl=1)](https://www.tp-link.com/common/Spotlight/EAP_controller.html)

TP-Link EAP Controller
==========================


EAP Controller - https://www.tp-link.com/common/Spotlight/EAP_controller.html



Running on the latest Phusion release (ubuntu 18.04), with OMADA SDN Controller v4.4.3
ONLY X86!!!!!


**Pull image**

```
docker pull mace/eap-controller
```

**Run container**

```
docker run -d --net="host" --privileged --name=<container name> -v <path for eap config files>:/config -v /etc/localtime:/etc/localtime:ro mace/eap-controller
```
Please replace all user variables in the above command defined by <> with the correct values.
Use --net="host" or --net="macvlan0"

**Web-UI**

```
http://<host ip>:8088
https://<host ip>:8043
```



**Additional notes**

* For a custom cert, stop the container and put the cert in "/config/cert" it needs to be named "mydomain.p12" and have the password "tplink"
* The owner of the config directory needs sufficent permissions (UUID 99 / GID 100). (For manual configs, backups etc on the host system)
* Mongodb dosent start if "/config" is mapped to an fuse mount, shfs, mergerfs etc...
* Should be run with network "host" or "macvlan", so it can find the AP´s
* Username and password will be linked to controller (if you restore a backup this will only restore AP,SSID,etc... settings, not the base controller username/pass()EAP limitation)
* Always make an backup of your settings before a new release "EAP controller version"(for a reinstall with same version it´s not necessary)
* If it dosen´t start make sure there is just one controller on the same subnet (EAP limitataion)
* This buils is only X86 with TP-Links budeled binaries

**Change notes**
* 2021.05.10
Upgrade to latest Omada SDN Controller (4.4.3)

* 2021.05.10
Upgrade to latest Omada SDN Controller (4.3.5)

* 2021.02.14
Upgrade to latest Omada SDN Controller (4.2.11)

* 2020.12.14
Upgrade to latest Omada SDN Controller (4.2.8)

* 2020.11.17
Upgrade to latest Omada SDN Controller (4.2.4)

* 2020.06.14
Upgrade to latest Omada SDN Controller (4.1.5)

* 2020.04.20
Upgrade to latest EAP-Controller (3.2.10)

* 2020.04.15
Upgrade to latest EAP-Controller (3.2.9)

* 2020.01.28
Upgrade to latest EAP-Controller (3.2.6)

* 2019.11.08
Upgrade to latest EAP-Controller (3.2.4)

* 2019.07.26
Upgrade to latest EAP-Controller (3.2.1)

* 2019.05.28
Upgrade to latest EAP-Controller (3.1.13)

* 2019.03.25
Upgrade to latest EAP-Controller (3.1.4)

* 2018.11.08
Upgrade to latest EAP-Controller (3.0.5)

* 2018.09.24
Upgrade to latest EAP-Controller (3.0.2)
Remove startup from build(greatly reduces build time)

* 2018.06.19
Add keystore to config for custom certs

* 2018.02.16
Initial release
