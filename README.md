# server-course
On this Markdown document i'll be putting the notes and commands for the basic course of servers
## Class 1: Networks & protocols
First class, on this day you learn how to diagnose the network to get everything up and running, also to understand some important concepts like how the machines comunicate with each other

Concepts you have to know
- DNS: translate ip addresses to domains
- TCP/IP: Communication Protocol, it is seccure and reliable but not so fast
- UDP: Another Communication Protocol, its faster than TCP but less reliable

Commands of the day:
```bash
ip addr #shows all the interfaces do you have included the localhost or local ip
ping -c 4 8.8.8.8 #to try connectivy outside
traceroute google.com #to see the jumps that a package do to arrive 
dlg google #to consult DNS records

# to inspect the ports
ss -tulpn ## most important command to do it
- parameters
	-t : TCP
	-u : UDP
	-l : Listening
	-p : Shows process(require sudo)
	-n : To show ports number directly(Not resolve names)
nmap localhost #to see which services are exposed locally
nmap ip-de-algun-sitio

#Client Simulation
curl -I http://google.com #to see the headers of the http response
curl -v http://google.com #Verbose mode. To see all the package exchange
wget http://google.com #download a resource to try if the server can be outside to internet
```

### Some practice to see the communication
To see the connectivity you can use a VM or another machine in your LAN
```bash
nc -l 8080 #in the pc 1
curl http://ip-destino:8080 #in the pc2
#With these commands, you can see how communication works: a program exposes a service through a specific port
```

## Class 2: Apache HTTP Server
Second class, on this day you will learn how to create a server for the first time to the world

Concepts
- Web server: a program that allow to listen on port 80, receive a request & search in his files to send back

Commands of the day:
```bash
#install
sudo apt install apache2 -y
#confirm the installation
sudo systemctl status apache2

#now automaticly apache serve a webpage 

you can use "curl localhost" or the ip of the pc
```

### Virtual host
1. Create a file in '/etc/apache2/sites-available/misitio.conf'
```bash
<VirtualHost *:80>
    DocumentRoot /var/www/misitio
    ServerName misitio.local

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
2. Create the folder: 'sudo mkdir /var/www/misitio'
3. Create a file HTML inside
4. Enable the site: 'sudo a2ensite misitio.conf'
5. Reload: sudo systemctl reload apache2

6. (optional) To see the logs: 'sudo tail -f /var/log/apache2/access.log'

> Note: if you dont have a domain you can use local "hosts"

```bash
sudo nano /etc/hosts
```

then you can add this line
127.0.0.1	misitio.local
## Class 3: Nginx
## Class 4: Firewalls and rules
## Class 5: Https & ssl
## Class 6: Optimization & Logs
