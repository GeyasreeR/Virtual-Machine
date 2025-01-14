# Tomcat Installation and Configuration on CentOS

This guide explains how to install and configure Apache Tomcat on a CentOS server. It also demonstrates how to configure Tomcat as a service that will automatically start after a reboot.

## Prerequisites

- CentOS server with root access.
- Basic knowledge of Linux commands.

## Steps to Install and Configure Tomcat

### Step 1: Install Required Dependencies

First, install `wget` using `yum` if it's not already installed:

```bash
yum install wget -y
```
### Step 2: Download Apache Tomcat
Download the latest version of Apache Tomcat (version 10.1.34 at the time of writing):
```
bash

wget https://dlcdn.apache.org/tomcat/tomcat-10/v10.1.34/bin/apache-tomcat-10.1.34.tar.gz
```

### Step 3: Extract the Tomcat Archive
Once the download is complete, extract the Tomcat tar.gz file:
```bash
tar xzvf apache-tomcat-10.1.34.tar.gz
```
### Step 4: Start Tomcat
Navigate to the Tomcat directory and start Tomcat:

```bash
cd apache-tomcat-10.1.34
bin/startup.sh
```

At this point, you should be able to access the Tomcat server in your browser by navigating to http://<your-server-ip>:8080.

### Configure Tomcat to Run as a Service
By default, Tomcat doesn't start automatically after a reboot. To configure Tomcat as a service and run it as a non-root user, follow the steps below.

### Step 5: Kill Running Tomcat Process
If Tomcat is already running, stop it by first identifying the process and killing it:

Find the running Tomcat process:
```
bash

ps -ef | grep tomcat
```

### Copy the process ID (PID) of the running Tomcat process.

Kill the process:

```bash
kill <process_id>
```
### Step 6: Create a Non-Root User for Tomcat
Tomcat should not run as the root user. Create a new user to run Tomcat:

```bash
useradd --home-dir /opt/tomcat --shell /sbin/nologin tomcat
```
### Step 7: Move Tomcat to the /opt/tomcat Directory
Copy the Tomcat files to the new directory:
```
bash
cp -r apache-tomcat-10.1.34/* /opt/tomcat
```
### Change the ownership of the /opt/tomcat directory to the tomcat user:
```
bash
chown -R tomcat.tomcat /opt/tomcat
```

### Step 8: Create a Systemd Service for Tomcat
Now, create a systemd service file to manage Tomcat. Open a new service file in vim or your preferred text editor:
```
bash
vim /etc/systemd/system/tomcat.service
```
Add the following content to the file:

[Unit]
Description=Tomcat
After=network.target

[Service]
Type=forking
User=tomcat
Group=tomcat

WorkingDirectory=/opt/tomcat
Environment=JAVA_HOME=/usr/lib/jvm/jre
Environment=CATALINA_HOME=/opt/tomcat
Environment=CATALINA_BASE=/opt/tomcat

ExecStart=/opt/tomcat/bin/startup.sh
ExecStop=/opt/tomcat/bin/shutdown.sh

[Install]
WantedBy=multi-user.target
Save and close the file.

### Step 9: Reload Systemd and Start Tomcat
Reload systemd to recognize the new service:
```
bash
systemctl daemon-reload
```

### Start the Tomcat service:
```
bash
systemctl start tomcat
```
### Enable the Tomcat service to start automatically on boot:

```bash

systemctl enable tomcat
```
### Step 10: Verify the Tomcat Service
Finally, verify that Tomcat is running:
```
bash
ps -ef | grep tomcat
```
You should see the Tomcat process running. You can also access the Tomcat server at http://<your-server-ip>:8080.

### Conclusion
You have now successfully installed Apache Tomcat on CentOS and configured it to run as a service that starts automatically after a reboot.
