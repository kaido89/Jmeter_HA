<h1>Jmeter-HA Project</h1>

One of the problems, that may occur in huge website is load balacing problem.<br> This errros may occur in bigger environment.
So in the <b>I</b>nformation <b>T</b>echnology world there is a free open source tool.<br>
Named <b>Apache Jmeter</b>, citing from their website: <br>"<i>100% pure Java application designed to load test functional behavior and measure performance.<br> 
It was originally designed for testing Web Applications but has since expanded to other test functions.</i>"<br>

<h3>Initial Requirements:</h3>
<ul>
<li>Master PC (In my case: Centos)<br></li>
<li>Two Slaves PC (In my case: 2 Centos)<br></li>
<li>Apache Jmeter (In my case: Jmeter 3.2v)<br></li>
<li>Gitlab Repositories<br></li>
<li>Jenkins on all machines<br></li>
</ul>

<h4>Instalation Steps:</h4>

<h5>Installation of Jenkins on all PCS</h5>
-<a href="https://jenkins.io/download/">Download Jenkins</a> (In my case it was jenkins-2.7.4-1.1.noarch.rpm)<br>
-Install on Master, Slave 1 and Slave the jenkins<br>
    
```
# sudo rpm -Uvh jenkins-2.7.4-1.1.noarch.rpm
# sudo yum update
# sudo systemctl enable jenkins
# sudo systemctl start jenkins
```
-Open the Jenkins on the Browser (Chrome/Firefox)<br>
--Browser URL:localhost:8080<br>
--In terminal copy text<br>
```
sh sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
--Paste the previous content on the Browser [Appears on Screen Unlock Jenkins] and Continue on.</br>
--Click on the close "x" button, near "Getting Started" text</br>
--Click on Start using Jenkins</br>
--Select admin text on top right corner</br>
--Click on configure left menu</br>
--Change "Full Name" and "Password" and Click Save</br>

<h5>Installation of Gitlab on one of the PCS (In my case: on Slave 2 Centos)</br></h5>
-Before this change the jenkins port 8080 to 8081(In my case: on Slave 2 Centos)</br>
```
# sudo systemctl stop jenkins
# sudo vi /etc/sysconfig/jenkins
```
-On line 56 change "JENKINS_PORT="8080" to "JENKINS_PORT="8081"</li>
```
# sudo systemctl start jenkins
```
	<li>Follow Gitlab installation guide on this <a href="https://about.gitlab.com/installation/#centos">Link</a> or the instructions bellow>:</li>
	<li>Install and configure necessary dependencies</li>
```
		# sudo yum install curl policycoreutils openssh-server openssh-clients
		# sudo systemctl enable sshd
		# sudo systemctl start sshd
		# sudo yum install postfix
		# sudo systemctl enable postfix
		# sudo systemctl start postfix
		# sudo firewall-cmd --permanent --add-service=http
		# sudo systemctl reload firewalld
```
	<li>Add the GitLab package server and install the package:</li>
		# curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.rpm.sh | sudo bash
		# sudo yum install gitlab-ce
	<li>Configure and start GitLab</li>
		# sudo gitlab-ctl reconfigure
	<li>Open the Browser on http:localhost</li>
	<li>Change the Password</li>
	<li>Login with user "root" and the "new Password"</li>
	</ol>
</ol>
