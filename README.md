# server-course
On this Markdown document i'll be putting the notes and commands for the basic course of servers
## Class 1: Networks & protocols
First class, in this day you learn how to diagnose the network to get everything up and running, also to understand some important concepts like how the machines comunicate with each other

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

## Some practice to see the communication
To see the connectivity you can use a VM or another machine in your LAN
```bash
nc -l 8080 #in the pc 1
curl http://ip-destino:8080 #in the pc2
#With these commands, you can see how communication works: a program exposes a service through a specific port
```


## Class 2: Apache HTTP Server
## Class 3: Nginx
## Class 4: Firewalls and rules
## Class 5: Https & ssl
## Class 6: Optimization & Logs
