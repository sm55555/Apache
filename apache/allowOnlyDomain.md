# Allow Only Domaing Access

### httpd.conf

#### 80,443 port

```
<VirtualHost *:80>
    ServerName ~~~IP~~~
    <Location />
        Order allow,deny
        Deny from all
    </Location>
</VirtualHost>
```

```
<VirtualHost *:443>
    ServerName ~~~IP~~~
    <Location />
        Order allow,deny
        Deny from all
    </Location>
</VirtualHost>
```


```
systemctl restart httpd
```
