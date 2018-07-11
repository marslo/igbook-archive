## Change Interface Name

### [temporary](http://kernelpanik.net/rename-a-linux-network-interface-without-udev/)
```
sudo ifconfig <ORIGINAL_INTERFACE_NAME> down
sudo ip link set <ORIGINAL_INTERFACE_NAME> name <NEW_INTERFACE_NAME>
sudo ifconfig <NEW_INTERFACE_NAME>
```

E.g.:
```
$ nmcli dev
DEVICE        TYPE      STATE         CONNECTION
wlp2s0        wifi      connected     WLAN-PUB
cni0          bridge    connected     cni0
enp0s31f6     ethernet  connected     Wired connection 1
docker0       bridge    connected     docker0
flannel.1     vxlan     disconnected  --
veth1890b284  ethernet  unmanaged     --
veth5145289b  ethernet  unmanaged     --
vetha9ee773c  ethernet  unmanaged     --
vethf5a48bb2  ethernet  unmanaged     --
lo            loopback  unmanaged     --

$ nmcli connection
NAME                UUID                                  TYPE      DEVICE
WLAN-PUB            2cde1f25-8c28-4318-9781-b9fcdabd985d  wifi      wlp2s0
Wired connection 1  f72d569d-065b-3bc8-98ae-e07f8bf46945  ethernet  enp0s31f6
cni0                dcfc10c6-5421-4405-9d56-b3bb595780f5  bridge    cni0
docker0             29822e8f-772f-4e67-8052-55b9e6c9e298  bridge    docker0

$ sudo ifconfig enp0s31f6 down; sudo ip link set enp0s31f6 name eth0; sudo ifconfig eth0 up

$ nmcli dev
DEVICE        TYPE      STATE         CONNECTION
wlp2s0        wifi      connected     WLAN-PUB
cni0          bridge    connected     cni0
docker0       bridge    connected     docker0
eth0          ethernet  connected     Wired connection 1
flannel.1     vxlan     disconnected  --
veth1890b284  ethernet  unmanaged     --
veth5145289b  ethernet  unmanaged     --
vetha9ee773c  ethernet  unmanaged     --
vethf5a48bb2  ethernet  unmanaged     --
lo            loopback  unmanaged     --

$ nmcli connection
NAME                UUID                                  TYPE      DEVICE
WLAN-PUB            2cde1f25-8c28-4318-9781-b9fcdabd985d  wifi      wlp2s0
Wired connection 1  f72d569d-065b-3bc8-98ae-e07f8bf46945  ethernet  eth0
cni0                e557e9bc-754e-4dc9-b9db-4519a7b15c33  bridge    cni0
docker0             47c195b8-4867-40d3-acec-c28223e2b013  bridge    docker0

```

