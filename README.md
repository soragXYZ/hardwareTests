# Hardware Tests

## Global
```
sudo dmidecode
```

## Network

```
curl -s https://packagecloud.io/install/repositories/ookla/speedtest-cli/script.deb.sh | sudo bash
sudo apt install speedtest
speedtest
```

## Disks
Sequential Write
```
dd if=/dev/zero of=tmpfile bs=1M count=1024 conv=fdatasync
```

Sequential Read
```
sudo /sbin/sysctl -w vm.drop_caches=3
dd if=tmpfile of=/dev/null bs=1M count=1024
rm tmpfile
```

## CPU

```
lscpu
```

Quicktest for comparison
```
dd if=/dev/zero bs=1M count=1024 | md5sum
```

```
sysbench --test=cpu --cpu-max-prime=20000 run
```

Geekbench
```
wget -qO- http://cdn.geekbench.com/Geekbench-6.0.3-Linux.tar.gz | tar -xz
cd Geekbench-6.0.3-Linux && ./geekbench6
```

## RAM

Basic
```
sudo lshw -short -C memory
```

Test
```
sudo apt install sysbench -y
```

Write
```
sysbench memory --memory-block-size=1G --memory-total-size=20G --memory-oper=write run
```

Read
```
sysbench memory --memory-block-size=1G --memory-total-size=20G --memory-oper=read run
```

