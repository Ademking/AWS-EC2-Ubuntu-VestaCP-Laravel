# AWS-EC2-Ubuntu-VestaCP-Laravel
How to install VestaCP + Laravel with AWS EC2

1. Launch a new amazon AWS EC2 instance (Ubuntu) 

Must open these ports for vestacp : 

| Type        | Port           | Source  |
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

# How to add domain in VestaCP (OVH domain)

OVH :
1. Log in to your OVH account manager

2. Go to DNS server

3. Add nameserver: 

ns1.yourdomain.com ---> 111.111.111.111 (ip of vestacp server)

ns2.yourdomain.com ---> 111.111.111.111 (ip of vestacp server)

4. Go to DNS zone and add

demo.yourdomain.com.    A   18.188.148.200
	
demo.yourdomain.com.    NS    ns1.yourdomain.com.	
	
demo.yourdomain.com.    NS    ns2.yourdomain.com.

-------------

Vesta CP

Once the private nameservers registration is complete, you need to configure Vesta Control Panel.

1. Add domain yourdomain.com (leave DNS Support mark checked)
2. Go to DNS menu
3. Click on edit under yourdomain.com
4. Change template to child-ns
5. Go to Packages menu
6. Edit package called default
7. Set ns1.yourdomain.com and ns2.yourdomain.com as nameservers

After you have done all steps, you can now set all of your domain names to use ns1.yourdomain.com and ns2.yourdomain.com. Please note that it may take up to 24 hours while dns records will start working.


# How to add SSL
run: 
source /etc/profile
PATH=$PATH:/usr/local/vesta/bin && export PATH
then
Video : https://www.youtube.com/watch?v=T29GPpLbvvs
