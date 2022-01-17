# NEEO/Meta-plus solution for Ziggo-Next settop box (STB)
## Description
This solution adds support for controlling a Ziggo-Next settop box.
It is based for 95% on the excellent work of basst85 (https://github.com/basst85/NextRemoteJs).
The idea to use the work of basst85 came from Jacques v Z. I reworked the solution to remove the need for Node-Red. 

## Installation
We're assuming you are using Meta in /opt/meta 

 1. Login to your meta-system.
 2. Goto /opt directory (cd /opt)
 3. Download the NextRemote package from Github containing the listener: 
    git clone https://github.com/basst85/NextRemoteJs.git 
 4. Goto directory where NextRemote is installed: cd /opt/NextRemoteJs/
 5. Configure the variables in config.json: fill in your Ziggo-username and password (the one you use to login to the ziggo-site) AND change webPort from 8080 into 5385!!!!
 6. Install package: npm install
 7. Start NextRemote (and keep it running when you close your terminal session): 
    nohup node index.js 
 7. Now download the Meta driver to your meta-system:
    a. cd /opt/meta/active
    b. wget https://raw.githubusercontent.com/Ton-O/Meta_ZiggoNext/master/ZiggoNext.json
 8. Restart meta, install ZiggoNext and you're done.

## Note
a. You may want to change the startup step of NextRemote (step 7) so it will autostart after reboot. That can be done by using pm2: pm2 start --name ZiggoNext /opt/NextRemoteJs/index.js
followed by pm2 save
b. The support for playing radio that I added is based on simulating key presses; though it works 95% of the time, it may fail sometimes because of slow responses from Ziggo MQTT-servers.
Simply pressing Radio again on your remote once more will solve the issue. 
c. The external NextRemoteJs driver used in this solution, is maintained by someone else, so changes into hat driver may (not likely) introduce problems in the future. I have a saved version of current driver (that also has suport for Radio in it) so fallback to hat one is always on option.
