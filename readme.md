1 - Installation of BIND
```
sudo yum install bind bind-utils
```
2 - Modify the named configuration file.
```
sudo vi /etc/named.conf
```
3 - Make sure you have all this information available.
```
options {
    listen-on port 53 { any; };
    directory "/var/named";
    dump-file "/var/named/data/cache_dump.db";
    statistics-file "/var/named/data/named_stats.txt";
    memstatistics-file "/var/named/data/named_mem_stats.txt";
    allow-query { any; };
    recursion yes;
};
zone "nextgentech.fr" {
    type master;
    file "/var/named/your_domain.fr.zone";
};
};
```
4 - Create a zone file for the domain, for example:
```
sudo vi /var/named/your_domain.fr
```
5 - Start named.
```
sudo systemctl start named
```
6 - enable named
```
sudo systemctl enable named
```
