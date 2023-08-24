# Deployment 2 Documentation
## Purpose
The purpose of deployment 2 was to set up Jenkins within our AWS EC2 instances and to manually deploy it to Elastic Beanstalk. Previously, we would have Jenkins Build and Test our application from Github and once it passed, we would download the zip files from Github and manually deploy it into AWS Elastic Beanstalk. For this deployment, we installed a plugin that allows Jenkins to download the zip files once it finishes the Build and Test Phrase. Once we get that zip file created by Jenkin, I will upload that into the AWS Elastic Beanstalk.

## Steps:
1. Before starting this deployment, I downloaded this repository from Kura Labs and uploaded it to my Github.
2. Launch an EC2 instance with Ubuntu as the OS and download Jenkins onto it
   - Within the EC2 instance I download Jenkins with the following commands.
       - `sudo apt-get update`
       - `curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \/usr/share/keyrings/jenkins-keyring.asc >/dev/null`
       - `echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \https://pkg.jenkins.io/debian binary/ | sudo tee \/etc/apt/sources.list.d/jenkins.list > /dev/null`
       - `  sudo apt-get install fontconfig openjdk-17-jre`
       - `sudo apt-get install jenkins`
3. Open up Jenkins and set up Pipeline Utility Steps
  - Since this is a new Jenkins, I when in and set up everything (Username, Password, etc.). Once, I was in I went to Available Plugin to download the Pipeline Utility Steps add-on. From there, I ran my application through Jenkins.
4. Finding the files Jenkins created/Uploaded to Elastic Beanstalk
  -Thankfully, my application ran with no error, however during the Packaging of the output files stage I had to click continue as this was mentioned in the Jenkin file.
  -Once, I got that I had to look for the zip file Jenkin created. Once, I found that I sent it over to my local PC and uploaded the AWS Elastic Beanstalk.

## System Design Diagram:
To view the System Design Diagram, click ![here!]
