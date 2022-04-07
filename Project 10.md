# LOAD BALANCER SOLUTION WITH NGINX AND SSL/TLS

Create an ubuntu EC2 instance with tcp port 80 and port 443 open

![](images/1.png)

Update etc/hosts file with server names and their private IP adddress 

`sudo vi /etc/hosts`

![](images/2.png)

Update Ubuntu

`sudo apt update`

![](images/3.png)


Install Nginx

`sudo apt install nginx`

![](images/4.png)


Configure Nginx using Web Servers’ names defined in /etc/hosts

`sudo vi /etc/nginx/nginx.conf`

![](images/5.png)

Comment out "include /etc/nginx/sites-enabled/*;"

![](images/6.png)

Restart Nginx

`sudo systemctl restart nginx`

Verify Nginx server is running

`sudo systemctl status nginx`

![](images/7.png)

Assign an Elastic IP to your Nginx LB server 

![](images/22.png)

Registered a domain name ladidevops.xyz

Create a hosted zone and records for domain name

![](images/9.png)

![](images/10.png)

Update domain name in nginx.conf file

`sudo vi /etc/nginx/nginx.conf`

![](images/12.png)

check domain name is active via web browser

![](images/11.png)

## Install certbot and request for an SSL/TLS certificate

Check if snapd service is active and running

`sudo systemctl status snapd`

![](images/13.png)

Install certbot

`sudo snap install --classic certbot`

![](images/14.png)

Request certificate

`sudo ln -s /snap/bin/certbot /usr/bin/certbot`

`sudo certbot --nginx`

![](images/15.png)

![](images/16.png)

Access domain name via https

![](images/17.png)

![](images/18.png)

Set up periodical renewal of your SSL/TLS certificate

`sudo certbot renew --dry-run`

![](images/19.png)

Test configure a cronjob to run the command twice a day

`crontab -e`

![](images/20.png)

add below line

![](images/21.png)
