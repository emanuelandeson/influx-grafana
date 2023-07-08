# influx-grafana
InfluxDB logging + Grafana 

# Install InfluxDB 2.0

# We need a few things for this
apt install gpg apt-transport-https -y

# Load GPG fingerprint and debian repo from Influx
# influxdata-archive_compat.key GPG fingerprint:
#     9D53 9D90 D332 8DC7 D6C8 D3B9 D8FF 8E1F 7DF8 B07E
wget -q https://repos.influxdata.com/influxdata-archive_compat.key
echo '393e8779c89ac8d958f81f942f9ad7fb82a25e133faddaf92e15b16e6ac9ce4c influxdata-archive_compat.key' | sha256sum -c
cat influxdata-archive_compat.key | gpg --dearmor > /etc/apt/trusted.gpg.d/influxdata-archive_compat.gpg
echo 'deb [signed-by=/etc/apt/trusted.gpg.d/influxdata-archive_compat.gpg] https://repos.influxdata.com/debian stable main' > /etc/apt/sources.list.d/influxdata.list

#Actually update install (or update)
apt update && apt install influxdb2 -y

#Start the servyce
systemctl enable --now influxdb

If you want to check it, run systemctl status influxdb.

Now login to the host at port 8086 and initialize. I set the password to DimuscoCluster

API token YKcaraowz5pFvVSkZ4w6nJrHUJr5AfujU3eDLMXJdWfgUEJuyyKs5Sv-8YqipOlW3yEvcQRDWkm0gTH5u0u5pA==

#Install Grafana

#Install the signing key
wget -q -O /usr/share/keyrings/grafana.key https://apt.grafana.com/gpg.key

#Add repository
echo "deb [signed-by=/usr/share/keyrings/grafana.key] https://apt.grafana.com stable main" > /etc/apt/sources.list.d/grafana.list

#Update and install
apt update && apt install grafana -y

#Start the server
systemctl enable --now grafana-server

Now we can login with admin/admin and I set it to ‘Grafana’





src: https://www.apalrd.net/posts/2023/pve_influx/
