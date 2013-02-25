# netcond

This is a simple bash script to help you simulate real network conditions with tc (iproute2).
Profiles are based on those from Apple's Network Link Conditioner tool.

It's been tested on Ubuntu 12.x.

## Usage
```
netcond start [interface] [profile]
netcond stop [interface]
netcond stats

Where  [interface] := the network interface to use e.g. lo, eth0 or wlan0
       [profile] := the profile to use (must exist in the profiles directory)

Note   You will probably need to run this with sudo
```

## Example
```
# simulate a wifi network that is unstable on eth0
sudo ./netcond start eth0 wifi-lossy

# view some tc statistics
sudo ./netcond stats

# stop the simulation and clean up
sudo ./netcond stop eth0
```

## Future enhancements

- [ ] make ingress and egress traffic shaping separately configurable to simulate asymetric upload and download

## References

* http://www.lartc.org/
* http://lartc.org/lartc.html#LARTC.QDISC
* http://lartc.org/wondershaper/
* http://www.linuxfoundation.org/collaborate/workgroups/networking/netem
* http://www.linuxfoundation.org/collaborate/workgroups/networking/ifb
* https://gist.github.com/bradoaks/940616
* https://github.com/rfrail3/misc/blob/master/tc/traffic-control.sh
* http://www.cyberciti.biz/faq/linux-traffic-shaping-using-tc-to-control-http-traffic/
* http://serverfault.com/questions/350023/tc-ingress-policing-and-ifb-mirroring