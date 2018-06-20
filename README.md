**Prerequisite:**

Code will work on centos(RHEL) version 7

Please, make sure that the git and ansible version 2.0 or above should be installed in the system, rest all the required package, for the below 4 applications,  role will install them.

If you are testing this code in AWS/GCP or any other cloud. Please make sure that the inbound traffic is allowed for the port no 8080,8085 and 8161 in a security group.

Check Ansible :

# ansible --version

This code was tested and written in the version 2.5.5, But will work with the other versions too above 2.0.

Scope:

This code contains 4 roles which will be executing together and will install and configure the below applications.

1)	Java Oracle JDK v8 – and will Configure $JAVA_HOME variable for all users
2)	Tomcat v8 (8.5.9) – from a tar.gz and Deploy sample.war to tomcat
3)	Activemq -5.14.0 – from a tar.gz
4)	Nginx


**Execution:**

1) clone the repository with the following command : "git clone https://github.com/monupawan/ansible.git"

    if git in not installed then please install the git first with yum

2)  cd ansible

3) ansible-playbook main.yml


**Verification:**

1)	To verify java please execute java -version command


java -version


java version "1.8.0_131"Java(TM) SE Runtime Environment (build 1.8.0_131-b11)Java HotSpot(TM) 64-Bit Server VM (build 25.131-b11, mixed mode)

              AND

echo $JAVA_HOME
the above command will show the path of java, keeping in mind that the requirement for this variable is set for all users.
if this doesn't show any output then please change the user like sudo su - and then run the command again, you will see the JAVA_HOME or just execute the command source /etc/profile

2)	To verify **Tomcat** please use the below information.

    a)	 Execute the “systemctl status tomcat” command, it will show the tomcat service

    b)	 http://[IP-addr]:8085 :  IP-addr = ip address of your system,
    you will get the below message as we deployed a sample.war file too.

          Sample "Hello, World" Application


3)	To verify **Activemq** please use the below information:

    a)   Execute the “systemctl status activemq” command, it will show the activemq service

    a)	 http://[ip-addr]:8161/admin : username= admin, password= admin

    If you get an ActiveMQ management console then “Great you did a good job” everything is working as expected


4)	To verify **Nginx** please use the below information:

    a)  please type  http://[ip-addr]:8080 in the URL

    b)  Execute the “systemctl status nginx” command, it will show the nginx service
