# suricata

SIEMonster Suricata Integration

Installation
```
apt-get update
apt-get -y install libpcre3 libpcre3-dbg libpcre3-dev build-essential autoconf automake libtool libpcap-dev libnet1-dev libyaml-0-2 libyaml-dev zlib1g zlib1g-dev libcap-ng-dev libcap-ng0
apt-get -y install libmagic-dev pkg-config libjansson4 libjansson-dev
mkdir suricata
cd suricata
git clone git://phalanx.openinfosecfoundation.org/oisf.git
cd oisf
git clone https://github.com/OISF/libhtp
./autogen.sh
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make install-full
```
Logrotate

```
nano /etc/logrotate.d/suricata

/var/log/suricata/eve.json {
        daily
        size 50M
        rotate 0
        missingok
        compress
        postrotate
                killall -HUP suricata
        endscript
}
```
Service

```
nano /etc/init/suricata.conf

# suricata
description "Intruder Detection System Daemon"
start on runlevel [2345]
stop on runlevel [!2345]
expect fork
exec suricata -D --pidfile /var/run/suricata.pid -c /etc/suricata/suricata.yaml -i eth0
```
Rules Update

```
apt-get install oinkmaster
nano /etc/oinkmaster.conf
Add the following line
url=http://rules.emergingthreats.net/open/suricata/emerging.rules.tar.gz

cd /etc
oinkmaster -C /etc/oinkmaster.conf -o /etc/suricata/rules
```




