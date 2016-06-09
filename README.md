# i40e-netmap
i40e drivers from e1000.sf.net with netmap patches

## how to use

1.Clone netmap
```
git clone https://github.com/luigirizzo/netmap
cd netmap/LINUX
```

2.Create override file for i40e. Example is provided in this repository:
```
i40e-src := <whatever-the-path-is>/i40e/i40e-1.5.16/src
i40e-patch := <whatever-the-path-is>/i40e/i40e-1.5.16.patched.diff
```
3.Configure netmap to use your override file:
```
./configure --drivers=i40e --override=./i40e-override
```
4.`make && make install` as usual. Note that it won't update your initrd so on next reboot default driver will be loaded. Make sure you're running correct one like this:
```
modinfo i40e|egrep '^version|netmap'
version:        1.5.16
depends:        netmap,ptp,vxlan
```
