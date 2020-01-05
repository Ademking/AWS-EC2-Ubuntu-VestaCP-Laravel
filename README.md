# AWS-EC2-Ubuntu-VestaCP-Laravel
How to install VestaCP + Laravel with AWS EC2

1. Launch a new amazon AWS EC2 instance (Ubuntu) 

Must open these ports for vestacp : 

| Type        | Port           | Cool  |
| ------------- |:-------------:| -----:|
| UDP | 80 | 0.0.0.0/0 |
| TCP |  80|  0.0.0.0/0
| TCP | 110|  0.0.0.0/0
| TCP | 8083|  0.0.0.0/0
| TCP | 22|  0.0.0.0/0
| TCP | 21|  0.0.0.0/0
| TCP | 25|  0.0.0.0/0
| TCP | 20|  0.0.0.0/0
| TCP | 143|  0.0.0.0/0
| UDP | 53|  0.0.0.0/0
| TCP | 53|  0.0.0.0/0
| TCP | 443|  0.0.0.0/0

2. Connect using SSH and run :
```
$ sudo su

$ curl -O http://vestacp.com/pub/vst-install.sh

$ bash vst-install.sh — nginx yes — phpfpm yes — apache no — named no — remi yes — vsftpd no — proftpd no — iptables yes — fail2ban yes — quota no — exim yes — dovecot no — spamassassin no — clamav no — softaculous no — mysql yes — postgresql no

```
3. Upload your laravel project to `/home/{{username}}/web/{{domain_name}}/public_html `

(Change {{username}} and {{domain_name}} with yours)

4. After installation, open `/usr/local/vesta/data/templates/web/apache2` folder and add these 2 files

[laravel.tpl](laravel.stpl)

[laravel.stpl](laravel.stpl)

5. restart apache2 and nginx
