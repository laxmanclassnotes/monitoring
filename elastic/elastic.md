Create Elastic Cloud account, Monitoring with HeartBeat for Apache Server
-------------------------------------------------------------------

### Create Elastic Cloud account with mail
* [ReferHere](https://cloud.elastic.co/registration) for official docs for login
* ![Preview](./Images/monitor25.png)
* ![Preview](./Images/monitor26.png)
* ![Preview](./Images/monitor27.png)
* In the above download option use to download credentials in our local system
* and wait for five minutes and configure these credentials and click `continue` button
* ![Preview](./Images/monitor28.png)
* Our Elastic Cloud is ready
* Navigate to Stack management and add some data
* Navigate to Alerts & Insights >> connectors >> and conneter is used mailtrap (dummy mail) is used for quick notifications. `(below add mails and config to connectors )` 
* Addittional information to refer our sir daily class notes . The date is 09/may/2023.

### Install apache server on ubuntu
* Connect one ec2 machine 
```bash
sudo apt update
sudo apt install apache2 -y
```
![Preview](./Images/monitor5.png)

### Install HeartBeat 
* Take one ec2 machine install heartbeat on these machine
* [ReferHere](https://www.elastic.co/guide/en/beats/heartbeat/current/heartbeat-installation-configuration.html) for official docs for install `heartBeat`
* [ReferHere](https://www.elastic.co/guide/en/beats/heartbeat/current/setup-repositories.html)for apt installation


```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
sudo apt-get install apt-transport-https
echo "deb https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-8.x.list
sudo apt-get update && sudo apt-get install heartbeat-elastic
sudo systemctl enable heartbeat-elastic

next

cd /etc/heartbeat/
ls
sudo cat heartbeat.yml
``` 
![Preview](./Images/monitor1.png)
* In these below credentials are added in `heartbeat.yml`
* used in `sudo vi heartbeat.ayml`
![Preview](./Images/monitor2.png)
* In these above lines are taken from 
    * login into our elastic cloud
     ![Preview](./Images/monitor3.png)
    * Navigate click the settings button
    * ![Preview](./Images/monitor4.png)
    * And copy these cloud id
  * We can also take cloud.auth  `elastic:2a6tI0v9gy3dDOzOdeFDxEiI`
  * The above cloud.auth is taken from If we creating the `Elastic cloud account` it will gives some id in one file that time we download the file.
  * we also add apache url, id, shedule, type for `monitoring purpose` 
  * ![Preview](./Images/monitor6.png)
#### Create one mail in `mailtrap` cloud
* ![Preview](./Images/monitor10.png)
* ![Preview](./Images/monitor11.png)
Open Elastic cloud 
* Navigate to _Stack Managent_ >> _connectors_ add one connector
* ![Preview](./Images/monitor9.png)
* ![Preview](./Images/monitor12.png) and save it, these credentials are taken from mail trap account
* ![Preview](./Images/monitor8.png)
Navigate to kibana
* ![Preview](./Images/monitor7.png)
* ![Preview](./Images/monitor13.png)
* ![Preview](./Images/monitor14.png)
* ![Preview](./Images/monitor15.png)
* The above Image shows Monitoring our apache server
* Then we check these monitor work are not we use these command 
* ![Preview](./Images/monitor16.png)
* ![Preview](./Images/monitor17.png)
*  we navigate to `Alert & Rules`
*  Navigate to create rule 
* ![Preview](./Images/monitor18.png)
* ![Preview](./Images/monitor19.png) 
* ![Preview](./Images/monitor20.png)
* we apache server stop then the monitoring also down status and colour shown
* ![Preview](./Images/monitor21.png)
* when we create the rule or alert then msg go to our mail (mailtrap) our server is work or down status
* ![Preview](./Images/monitor22.png)
* Then the content shows oue server is down status
* ![Preview](./Images/monitor23.png)
* And we immediatly to check the apache server and start the server use these command ` sudo systemctl start apache2.service` it will goes to up status
* ![Preview](./Images/monitor24.png)


* In these we also add `icmp` type server
* It is also check our config files and monitoring these credentials are also add in `heartbeat.yaml` [ReferHere](https://www.elastic.co/guide/en/beats/heartbeat/current/heartbeat-installation-configuration.html)
* ![Preview](./Images/monitor29.png)
* Use these commands to restart the service `sudo systemctl restart heartbeat-elastic.service` and check the status `sudo systemctl status heartbeat-elastic.service`
* ![Preview](./Images/monitor30.png)
* Navigate to Elastic Cloud  >> Alerts & Rules >> Create rule >> 
* ![Preview](./Images/monitor31.png)
* Navigate to `uptime monitor` and see the below image 
* ![Preview](./Images/monitor32.png)
* Results see in mailtrap
* ![Preview](./Images/monitor33.png)

