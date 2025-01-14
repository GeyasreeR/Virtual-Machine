## To deploy website manually on apache2 service on ubuntu server
- **Install required packages**
  ```bash
  apt update
  apt install httpd wget vim unzip zip -y
  systemctl start apache2
  ```
Note: we can also do this through provisioning in vagrant file, if done we can skip this step

- **Get in to root user**
```bash
sudo -i
```

- **get ip address**
```bash
ip addr show
```
now copy the ip public address and paste it in the browser and default apache2 server page should open then we can say apache2 service is up and running

- **Get html template from tooplate**
Change into temp directory and download html template
```bash
cd /tmp/
wget https://www.tooplate.com/zip-templates/2106_soft_landing.zip
ls
unzip 2106_soft_landing.zip
cd 2106_soft_landing.zip
cp -r * /var/www/html
ls /var/www/html
systemctl restart apache2
systemctl enable apache2
```
Now paste the public ip address in browser and you should see the website that've deployed
