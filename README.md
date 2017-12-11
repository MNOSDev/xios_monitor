# xios-monitor

PHP script designed to monitor several XIOSd nodes on Ubuntu

# Caution

I DONT WANT YOU TO LOSE YOUR COINS ! 

This is not a secure web app please be carefull with shell_exec command trough apache !

# Requirements

XIOSd compiled in /root/xios/src/

Apache2 and php running :

<pre>apt-get install apache2 php</pre>

# Install

As root :

<pre>cd
git clone https://github.com/dirtyak/xios-monitor
cp -r xios-monitor/* /var/www/html/.
rm -r xios-monitor
rm -r /var/www/html/index.html</pre>

Add www-data to sudoers file for shell_exec function.

<pre>www-data ALL=(ALL) NOPASSWD:ALL</pre>

# Config

Please edit config.php to match with your vps parameters
<pre>$xios_name = "XIOS";       # Name to show for each node
$xios_dir = "/root/.XIOS"; # Directory where config files stored
$xios_ip = localhost;      # XIOSd is running local
$xios_port = 9000;         # port used by first XIOSd
$xios_count = 3;           # How many XIOSd to monitor ?</pre>

In this default config XIOSd ports must be 9000, 9001, 9002 for XIOS1, XIOS2, XIOS3 to work

# Example 

You can try it at : http://45.77.53.110/

Hosted by Vultr : https://www.vultr.com/?ref=7280492

# Fix 

If you already setup your wallet with config files in .XIOS copy it to .XIOS1.

<pre>cp -r $home/.XIOS $home/.XIOS1
$home/src/xios/XIOSd stop</pre>

Now use this script to get your node(s) online (every time) :

<pre>/root/xios/src/XIOSd -datadir=/root/.XIOS1 -config=/root/.XIOS1/XIOS.conf -daemon
#/root/xios/src/XIOSd -datadir=/root/.XIOS2 -config=/root/.XIOS2/XIOS.conf -daemon
#/root/xios/src/XIOSd -datadir=/root/.XIOS3 -config=/root/.XIOS3/XIOS.conf -daemon
</pre>
