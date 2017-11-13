# One-liner Linux Gems
A list of one-liner linux command line gems  

## TCP Dump

Retrieve HTTP Headers and a human-readable format 

```
sudo tcpdump -A -s 10240 'tcp port 80 and (((ip[2:2] - ((ip[0]&0xf)<<2)) - ((tcp[12]&0xf0)>>2)) != 0)' | egrep --line-buffered "^........(GET |HTTP\/|POST |HEAD )|^[A-Za-z0-9-]+: " | sed -r 's/^........(GET |HTTP\/|POST |HEAD )/\n\1/g'
```

## Disk Usage

Find top 10 largest directories sorted in descending order by bytes 

```
du -a / | sort -n -r | head -n 10
```
