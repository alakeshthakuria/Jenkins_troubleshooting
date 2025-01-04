# Jenkins_troubleshooting

## Why does the Jenkins page load very slowly in the browser after restarting an AWS Free Tier EC2 instance hosting Jenkins?

This resolution specifically applies when using an AWS Free Tier EC2 instance, as the Free Tier does not provide an Elastic IP address. Each time the instance is restarted, its public IP address changes. To address this issue, navigate to the instance and go to the directory /var/lib/jenkins. Change the permissions of the file jenkins.model.JenkinsLocationConfiguration.xml to 777. Open the file and locate the <jenkinsUrl>http://x.x.x.x:8080</jenkinsUrl> section. Update the public IP address of the EC2 instance from the old one to the new one, and then restart the Jenkins service `sudo service jenkins restart`.


## Reset the Jenkins administrator password
- Log in to your Jenkins controller
- Stop the Jenkins process. You may use this command: `sudo systemctl stop jenkins`
- go to this directory: `cd var/lib/jenkins` and then change the permission of the file `config.xml` to 777.
- Edit the `config.xml`, look for useSecurity and change it from true to false manually.
- Save your file and close it.
- Restart the Jenkins service to apply your changes. You may use this command: `sudo systemctl start jenkins`.
- After restarting Jenkins, navigate to your controller and sign in.
- On the dashboard, select Manage Jenkins in the navigation pane on the left side of the page. On the Manage Jenkins page, under the Security section, Under Security Realm, select Jenkins' own user database from the dropdown menu. Ensure the option Allow users to sign up is unchecked and save your changes. This redirects you to the Manage Jenkins page.
- On the Manage Jenkins page, select Users.
- Will see a list showing User IDs. Select the User ID that need to change the password for.
- Select Configure using the gear icon or the dropdown menu from the User ID. Locate the Security section to change your password.
