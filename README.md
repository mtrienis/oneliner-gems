# One-liner command line gems
A list of one-liner command line gems  

## TCP Dump

Retrieve HTTP Headers and a human-readable format 

```
sudo tcpdump -A -s 10240 'tcp port 80 and (((ip[2:2] - ((ip[0]&0xf)<<2)) - ((tcp[12]&0xf0)>>2)) != 0)' | egrep --line-buffered "^........(GET |HTTP\/|POST |HEAD )|^[A-Za-z0-9-]+: " | sed -r 's/^........(GET |HTTP\/|POST |HEAD )/\n\1/g'
```

Running wireshark on your host machine against a Kubernetes Pod 

```
kubectl exec <pod> -- tcpdump -i eth0 -w - | wireshark -k -i -
```

## Disk Usage

Find top 10 largest directories sorted in descending order by bytes 

```
du -a /var | sort -n -r | head -n 10
```

```
1008372 /var
313236  /var/www
253964  /var/log
192544  /var/lib
152628  /var/spool
152508  /var/spool/squid
136524  /var/spool/squid/00
95736   /var/log/mrtg.log
74688   /var/log/squid
62544   /var/cache
```
