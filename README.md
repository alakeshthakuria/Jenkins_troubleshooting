# Jenkins_troubleshooting

## Why does the Jenkins page load very slowly in the browser after restarting an AWS Free Tier EC2 instance hosting Jenkins?

This resolution specifically applies when using an AWS Free Tier EC2 instance, as the Free Tier does not provide an Elastic IP address. Each time the instance is restarted, its public IP address changes. To address this issue, navigate to the instance and go to the directory /var/lib/jenkins. Change the permissions of the file jenkins.model.JenkinsLocationConfiguration.xml to 777. Open the file and locate the <jenkinsUrl>http://x.x.x.x:8080</jenkinsUrl> section. Update the public IP address of the EC2 instance from the old one to the new one, and then restart the Jenkins service `sudo service jenkins restart`.
