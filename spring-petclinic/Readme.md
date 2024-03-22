# List of manual steps
* steps
```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
cd /tmp/
wget https://khajareferenceapps.s3.ap-south-1.amazonaws.com/spring-petclinic-3.2.0-SNAPSHOT.jar
java -jar spring-petclinic-3.2.0-SNAPSHOT.jar
ls
cd ~
sudo adduser spc
sudo mkdir /usr/share/spc
sudo mv /tmp/spring-petclinic-3.2.0-SNAPSHOT.jar /usr/share/spc/
ls /usr/share/spc/
sudo chown spc:spc /usr/share/spc/
sudo chown -R spc:spc /usr/share/spc/
ls -al /usr/share/spc/
sudo vi /etc/systemd/system/spc.service
sudo systemctl daemon-reload
sudo systemctl enable spc.service
sudo systemctl start spc.service
sudo systemctl status spc.service
sudo systemctl stop spc.service
history
```

* Sample Service file
```
[Unit]
Description=A Spring Boot application
After=syslog.target

[Service]
User=spc
ExecStart=java -jar /usr/share/spc/spring-petclinic-3.2.0-SNAPSHOT.jar SuccessExitStatus=143 

[Install] 
WantedBy=multi-user.target
```
