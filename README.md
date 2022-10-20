sudo timedatectl set-timezone Europe/London
sudo apt update
sudo apt install chrony -y
sudo systemctl enable chronyd
sudo systemctl start chronyd
sudo nano /etc/chrony/chrony.conf
Set pool to use multiple UK time sources

0.uk.pool.ntp.org
1.uk.pool.ntp.org
2.uk.pool.ntp.org
3.uk.pool.ntp.org

At the end of the chrony.conf file set subnets/ip’s for HF’s allowed to get time from DS

Allow 100.100.100.0/24
Allow 150.150.150.0/24

Save the file and restart chrony

sudo systemctl restart chronyd
Check the server is syncing properly to external NTP provider
chrony sources -v
Once clients are configured you can validate our connections using the command shown below
chronyc clients
