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



