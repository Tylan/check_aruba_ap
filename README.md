# check_aruba_ap
Checks Aruba AP Information by connecting to Aruba Controller

**AP Up/Down Status**

[TO BE ADDED]

**AP RX/TX/Radio Utilization**

[TO BE ADDED]

**AP Traffic Utilization**

[TO BE ADDED]

**AP User Count**

[TO BE ADDED]

## Getting Started

These instructions assume your Icinga2 is installed on a RHEL/CentOS system.  You may need to modify slightly to work with other systems.

### Prerequisites

Net-SNMP (http://www.net-snmp.org/)

Nagios plugins installed and located in /usr/lib64/nagios/plugins


### Installing

Download and install Net-SNMP.  If you choose to build from source use the following line:
```
./configure --with-perl-modules --with-mibdirs --enable-shared
```

Copy check_aruba_ap into your plugin directory and give it executable writes:

```
sudo cp ./check_aruba_ap /usr/lib64/nagios/plugins/
chmod a+x /usr/lib64/nagios/plugins/check_aruba_ap
```

Copy aruba-ap.conf into plugins-contrib.d folder:

```
sudo cp ./aruba-ap.conf /usr/share/icinga2/include/plugins-contrib.d/
```
Append services-aruba-ap.conf to the end of your Icinga2 services.conf:

```
cat ./services-aruba-ap.conf >> /etc/icinga2/conf.d/services.conf
```

Set proper MIB folder permissions:

```
sudo chown -R root:icinga /usr/share/snmp/mibs
sudo chmod -R ug+rw /usr/share/snmp/mibs
```

Restore SELINUX permissions:

```
sudo restorecon -R -v /usr/lib64/nagios/plugins/
sudo restorecon -R -v /usr/share/snmp/mibs
```

If using Graphite, copy graphite templates to Icinga2 Graphite template folder:

```
[TO BE ADDED]
```

Restart Icinga2:

```
sudo systemctl restart icinga2
```
