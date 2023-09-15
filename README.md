# Deployment 2 Documentation
## Purpose
The purpose of deployment 2 was to set up Jenkins within our AWS EC2 instances and to manually deploy it to Elastic Beanstalk. Previously, we would have Jenkins Build and Test our application from Github and once it passed, we would download the zip files from Github and manually deploy it into AWS Elastic Beanstalk. For this deployment, we installed a plugin that allows Jenkins to download the zip files once it finishes the Build and Test Phrase. Once we get that zip file created by Jenkin, I will upload that into the AWS Elastic Beanstalk.

## Steps:
1. Before starting this deployment, I downloaded this repository from Kura Labs and uploaded it to my Github.
2. Launch an EC2 instance with Ubuntu as the OS and download Jenkins onto it
   - Within the EC2 instance I download Jenkins with the following commands.
       - `curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \/usr/share/keyrings/jenkins-keyring.asc >/dev/null`
         - Gets Jenkins package repository GPG key form URL and pipes the output to /dev/null
       - `echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \https://pkg.jenkins.io/debian binary/ | sudo tee \/etc/apt/sources.list.d/jenkins.list > /dev/null`
         - Output an APT source entry repository. The entry point to Jenkins specifies where the key is located. The pipe the output to dev/null
       - `  sudo apt-get install fontconfig openjdk-17-jre`
         - Installing a Jave Runtime Environment since Jenkins is Java-based
       - `sudo apt-get install jenkins`
         - Install the Jenkins Package along with its necessary dependencies.
      - `sudo apt-get update`
         - Download information from all configured sources. Get info in updated version of packages/ dependencies
3. Open up Jenkins and set up Pipeline Utility Steps
     - Since this is a new Jenkins, I when in and set up everything (Username, Password, etc.). Once, I was in I went to Available Plugin to download the Pipeline Utility Steps add-on. From there, I ran my application through Jenkins.
     - Finding the files Jenkins created/Uploaded to Elastic Beanstalk
     -Thankfully, my application ran with no error, however during the Packaging of the output files stage I had to click continue as this was mentioned in the Jenkin file.
     -Once, I got that I had to look for the zip file Jenkin created. Once, I found that I sent it over to my local PC and uploaded the AWS Elastic Beanstalk.

## System Design Diagram:
To view the System Design Diagram, click [here](https://github.com/auzhangLABS/Installing-Jenkins/blob/main/diagram.png)

## Issues/ Troubleshooting:
1. The first issue, I had was finding the Jenkins zip file it created. Upon looking within my EC2 and searching online, I soon figured out that Jenkins has it in its logs.

![image](https://github.com/auzhangLABS/Installing-Jenkins/assets/138344000/435fe75b-cba5-4172-b607-5cf429377356)

2. The second issue, I had was trying to send files from my EC2 over to my local computer. I figured this out by doing research and coming to a solution. First, I would give access to my EC2 to access my local computer. Then, I would send it over via ssh on my local computer. However, I did find many ways to do this but I found this to be simpler and easier for me.

![image](https://github.com/auzhangLABS/Installing-Jenkins/assets/138344000/1f120ff7-62e8-42e2-91d1-154a228dc6f3)

## Optimization:
I would optimize this deployment by creating a bash SCP script that would make sending files from local to remote/ remote to local easier.
