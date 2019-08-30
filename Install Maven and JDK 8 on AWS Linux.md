
### To Install Apache Maven and Java 8 on your EC2 instance
<em>https://docs.aws.amazon.com/neptune/latest/userguide/iam-auth-connect-prerq.html</em>

#### Enter the following to add a repository with a Maven package.
```
<em>sudo wget https://repos.fedorapeople.org/repos/dchen/apache-maven/epel-apache-maven.repo -O /etc/yum.repos.d/epel-apache-maven.repo</em>
```
#### Enter the following to set the version number for the packages.
```
<em>sudo sed -i s/\$releasever/6/g /etc/yum.repos.d/epel-apache-maven.repo</em>
```
#### Use yum to install Maven.
```
<em>sudo yum install -y apache-maven</em>
```
#### Enter the following to install Java 8 on your EC2 instance.
```
<em>sudo yum install java-1.8.0-devel</em>
```
#### Enter the following to set Java 8 as the default runtime on your EC2 instance.
```
<em>sudo /usr/sbin/alternatives --config java</em>
```
#### When prompted, enter the number for Java 8.

#### Enter the following to set Java 8 as the default compiler on your EC2 instance.
```
<em>sudo /usr/sbin/alternatives --config javac</em>
```
#### When prompted, enter the number for Java 8.
