# Please follow this guide after the installation of any VM in your machine with Ubuntu 22.04
#Open the Terminal in the VM.
Tip: CTRL + ALT + T

#Run the first Command
sudo apt update

#It will display an error : "username" not in the sudoers file 
#We need to add the "username" in the sudoers file
#To do that first install vim in your machine, ignore installation of vim, if it is already installed. 

su 
#After "su" it will ask the password, please type the password and hit the enter
#Install the vim 
sudo apt install vim 

/etc#
~#

vi etc/sudoers

chmod 666 etc/sudoers

/usr/lib/jvm/java-11-openjdk-amd64/

sudo apt install maven
sudo apt install ant

sudo apt install postgresql postgresql-contrib
sudo pg_ctlcluster 14 main start
systemctl status postgresql
   groups postgres
   sudo passwd postgres
   su postgres
   psql -c "SHOW SERVER_ENCODING"
exit
cd /etc/postgresql/14/main
ls
sudo vi postgresql.conf
line no. 60 , localhost
sudo vi pg_hba.conf
host dspace dspace 127.0.0.1 255.255.255.255 md5  #Line no. 89
  sudo systemctl restart postgresql
   sudo systemctl status  postgresql
   cd /opt/
 
   ls
   ls -la
   sudo wget https://downloads.apache.org/lucene/solr/8.11.3/solr-8.11.3.zip
   sudo unzip solr-8.11.3.zip
   ls -la
   sudo chown -R dspace:dspace solr-8.11.3
   ls -la
   48  cd solr-8.11.3/
   49  ls
   50  cd bo
   51  cd bin/
   52  ls
   cd solr-8.11.3/bin/

   pwd
   ls -la
 cd
    vi .profile
   /opt/solr-8.11.3/bin/solr start
Open localhost:8983 in browser  
   sudo apt install tomcat9
   cd /lib/systemd/system
   

sudo vi tomcat9.service
after 40 line ....
ReadWritePaths=/dspace/
  cd /
  sudo mkdir /dspace
   ls -la
sudo chown -R dspace:dspace /dspace/
   

sudo vi /etc/environment
JAVA_OPTS="-Xmx512M -Xms64M -Dfile.encoding=UTF-8"

esc :wq
   echo $JAVA_OPTS
source /etc/environment
   echo $JAVA_OPTS
   cd /etc/tomcat9/
   ls
   sudo vi server.xml
   sudo systemctl restart tomcat9.service
#Warning :   daemon-reload
   sudo systemctl daemon-reload
   sudo systemctl restart tomcat9.service
  cd
   sudo apt install git
cd
#https://github.com/DSpace/DSpace/releases/
wget  https://github.com/DSpace/DSpace/archive/refs/tags/dspace-7.6.2.zip

unzip dspace-7.6.2.zip
ls
rm dspace-7.6.2.zip
ls #to check if file is removed
   cd DSpace-dspace-7.6.2/
pwd
su postgres
createuser --username=postgres --no-superuser --pwprompt dspace
createdb --username=postgres --owner=dspace --encoding=UNICODE dspace
psql --username=postgres dspace -c "CREATE EXTENSION pgcrypto;"
exit
   cd DSpace-dspace-7.6.2/

cd dspace/config

cp local.cfg.EXAMPLE local.cfg
sudo vi local.cfg

dspace.server.url = http://localhost:8080/server


Interface.
dspace.ui.url = http://localhost:4000

# Name of the site
dspace.name = DSpace CAD

# Solr server/webapp.
# DSpace uses Solr for all search/browse capability (and for usage statistics).
# Since DSpace 7, SOLR must be installed as a stand-alone service
solr.server = http://localhost:8983/solr

# Database username and password
db.username = dspace
db.password = baadal123

# Default language for metadata values
default.language = en_US


ls /dspace #To see what it has all blank
cd DSpace-dspace-7.6.2/
mvn package

cd DSpace-dspace-7.6.2/dspace/target/dspace-installer/
    ls   #build.xml
    ant fresh_install
    cd /dspace/
    ls
    cd bin/
    ls
     ./dspace database migrate  #./ means current directory
    
Technique A and Technique B

cd ..
   ls
    cd webapps/
   ls
   sudo cp -R /dspace/webapps/* /var/lib/tomcat9/webapps*
     ls -la /var/lib/tomcat9/webapps/
     cd ..
    ls
   cd solr/
   ls
   ls -la /opt/solr-8.11.3/server/solr/configsets/
    cp -R /dspace/solr/* /opt/solr-8.11.3/server/solr/configsets
   cd /opt/
   cd solr-8.11.3/
   cd bin/
    ls
   ./solr restart

#solr search select documentation
   /dspace/bin/dspace create-administrator
   sudo systemctl restart tomcat9.service
   # test, server, oai request verb identity
cd /
    sudo chown -R tomcat:tomcat /dspace
   #nvm github google
 cd
    pwd
#we need to do wget in ~
    wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
#Restart the terminal
   nvm ls-remote
   
   nvm install 16.20.2
   node -v
   npm install --global yarn
   npm install --global pm2
cd
   wget https://github.com/DSpace/dspace-angular/archive/refs/tags/dspace-7.6.2.zip
   unzip dspace-7.6.2.zip
   ls
   rm dspace-7.6.2.zip
   cd dspace-angular-dspace-7.6.2/
   yarn install
   ls
   cd config/
   ls
   cp config.example.yml config.prod.yml
   vi config.prod.yml
   yarn config:check:rest
    cd
   cd dspace-angular-dspace-7.6.2
    cd config/
   ls
   yarn run build:prod
   ls
   cd ..
   61  cd src/
   62  ls
   63  cd ..
   64  vi dspace-ui.json
   65  sudo vi dspace-ui.json
   66  pwd
   67  sudo vi dspace-ui.json

cd /home/dspace/dspace-angular-dspace-7.6.2/
 pm2 start dspace-ui.json

