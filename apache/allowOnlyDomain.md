# Allow Only Domaing Access

httpd.conf

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
systemctl restart httpd
```
