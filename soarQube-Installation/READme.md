#  **<span style="color:green">Insight Tech.</span>**
### **<span style="color:green">Contacts: +19515421057<br> WebSite : <http://www.insighttech.io/></span>**
### **Email: admin@insighttech.io*
### ** Download the latest version of sonarqube at sonarqube.org/downloads/ **


## SonarQube Installation And Setup In AWS EC2 Amazon linux 2 Instnace.
##### Prerequisite
+ AWS Acccount.
+ Create Amazon Linux 2 EC2 T2.small Instnace with 2GB RAM.
+ Create Security Group and open Required ports.
   + 9000 ..etc
+ Attach Security Group to EC2 Instance.
+ Install java openJDK 1.8+ for SonarQube version 7.8

## Create sonar user to manage the SonarQube server
```sh
#As a good security practice, SonarQuber Server is not advised to run sonar service as a root user, 
# create a new user called sonar and grant sudo access to manage sonar services as follows

sudo useradd sonar
# Grand sudo access to sonar user
sudo echo "sonar ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/sonar
sudo su - sonar
```

### Install Java 11

``` sh
hostname sonar
cd /opt
sudo yum -y install unzip wget git
amazon-linux-extras list
amazon-linux-extras install java-openjdk11
```
### Download and extract the SonarqQube Server software.
```sh
sudo wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-8.9.10.zip
sudo unzip sonarqube-8.9.10.zip
sudo rm -rf sonarqube-8.9.10.zip
sudo mv sonarqube-8.9.10 sonarqube
```

## Grant permissions for sonar user to start and manage sonarQube
```sh
sudo chown -R sonar:sonar /opt/sonarqube/
sudo chmod -R 775 /opt/sonarqube/
# start sonarQube server
sh /opt/sonarqube/bin/linux-x86-64/sonar.sh start 
sh /opt/sonarqube/bin/linux-x86-64/sonar.sh status
```

