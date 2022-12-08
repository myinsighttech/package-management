#  **<span style="color:green">Insight Tech.</span>**
### **<span style="color:green">Contacts: +19515421057<br> WebSite : <http://www.insighttech.io/></span>**
### **Email: admin@insighttech.io*



## Apache Maven Installation And Setup In AWS EC2 Amazon Linux 2 Instance.
##### Prerequisite
+ AWS Acccount.
+ Create An Amazon Linux 2 EC2 T2.small Instnace with 2GB of RAM.
+ Create Security Group and open Required ports such port 22.
+ Install java 11

### Install Java 11  and other softares (GIT, wget and tree)

``` sh
# install Java 11 as a pre-requisit for maven to run.

sudo hostname maven
cd /opt
sudo yum -y install unzip wget git -y
amazon-linux-extras list
amazon-linux-extras install java-openjdk11 -y
java -version
git --version
```

## 2. Download, extract and Install Maven
``` sh
#Step1) Download the Maven Software
sudo wget https://dlcdn.apache.org/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.zip
sudo unzip apache-maven-3.8.6-bin.zip
sudo rm -rf apache-maven-3.8.6-bin.zip
sudo mv apache-maven-3.8.6/ maven
```
## .#Step3) Set Environmental Variable  - For Specific User eg ec2-user
``` sh
vi ~/.bash_profile  # and add the lines below
export M2_HOME=/opt/maven
export PATH=$PATH:$M2_HOME/bin

#
```
## .#Step4) Refresh the profile file and Verify if maven is running
```sh
source ~/.bash_profile
mvn --version
```

