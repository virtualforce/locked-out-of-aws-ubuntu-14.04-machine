# AWS EC2 with Magento installation on Ubuntu 14.04 **Locked out**, services not running, restart didnt help and **no way to get in**

So here we are again, with yet another DevOps issue. Our AWS EC2 instance running one of our Magento based solution for our client started misbehaving. Apparent sign of misbehaviour was running out of diskspace for temp folder while the disk was not completely filled. Here are our specifics

 * Ubuntu 14.04
 * Magento 1.9.*
 * AWS EC2
 * Ports properly configured
 * Gateway, Routing Tables etc. properly configured
 * Suddenly the web server, ssh etc are not working
 * and the best part: no recent db backup available to completely recover the transactions (Transactional backups not available)
 * EC2 server logs suggest there is a diskspace issue but junior devops guy says he is sure the disk had plenty of free diskspace available as of this morning
 * So we must recover our EC2 box, in order to recover data completely
 
## The Ordeal
The first thing we did was to: 
* Check the EC2 monitor stats on AWS console
* Select your instance > Actions > Instance Settings > Get System Logs - Nothing alarming here

Next we tried to see if someone else faced similar issues? Our initial lookups on google suggested that it is a pretty common issue and it may be solvable using [AWS troubleshooting guide](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/TroubleshootingInstancesConnecting.html). So we checked out our specific area related to [_Connection Timeout_](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/TroubleshootingInstancesConnecting.html#TroubleshootingInstancesConnectionTimeout) when trying through SSH, WinSCP etc.

Our quick assessment was that 
* inbound and outbound ports are configured correctly :+1:
* Gateway is configured properly :+1:
* Routing tables are configured properly :+1:
* It is not a simple lockout issue, our web services are also down so something more serious is going on :-1:

### So what could it be? 
When viewing the EC2 logs for the instance we could see an error logged which would say it is a diskspace issue so in order to rule out the diskspace issue, we increased the disksize following the wonderful post by

(To be continued...)


### Stuff used to make this:

 * [Online markdown editor](https://jbt.github.io/markdown-editor)
 * [AWS troubleshooting guide](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/TroubleshootingInstancesConnecting.htm)
