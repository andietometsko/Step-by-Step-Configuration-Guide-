# Step-by-Step Configuration Guide

### Objective 

The following deliverables demonstrate how to design, simulate, and implement a basic network. This is achieved by using both virtual tools and physical devices to showcase how different network components connect and interact. This includes diagraming a basic network in Packet Tracer by integrating two LANs, as well as setting up essential network services, like a web server and a DNS server, by using physical Cisco devices. 

### Use Cases for the System

This system can be used in a variety of practical ways within IT and systems administration. 

Below are potential uses for this network:
1. Small Business Network Setup: This design can connect multiple LANs in small to medium-sized businesses by using separate networks for departments such as HR, Marketing, or Finance.
2. LMU: Universities use a LAN network for students and staff to communicate with different networks on campus, whether that is from the classroom, dorms, or office buildings. 
3. Internal Company Network for Web Hosting: This system can be used to host internal websites that employees need access to for daily operations. 
4. Testing for Application Development: Developers can use this network to simulate real-world scenarios where applications are hosted on DNS and web servers that need to be tested in a controlled LAN environment. 
5. Network Troubleshooting and Cybersecurity Practice: This network can be used as a safe environment for security testers to simulate attacks, identify vulnerabilities, and test security configurations.

### Step-by-Step Configuration 

1. Collect Cisco physical hardware and other system devices 
* Cisco catalyst 3750 series 24-port switch (WS-C3750-25TS-S)
* Cisco 2911/K9 Router
* Four ethernet cables
* Two USB C adapters
* Two networked laptops
* One serial console cable
* Download and install NAMO and MAMP (not MAMP Pro) software onto each of the networked laptops as well as Terminal 

2. Configure the physical hardware 
* Attach an ethernet cable from the router to the switch, by plugging in the cable to the ethernet ports
* Turn on the ethernet switch. Note, it may take 2-3 mins for the Cisco devices to start up
* From the switch take 2 ethernet cables and plug them into two ports
* Attach the two USB C addapters to the other end of the ethernet cables and plug each of those cables into the networked laptops
  

3. Assign IPs to networked laptops
* First we will configure an IP on laptop1, go to 'System Settings', 'Network','Other Services' then select USB 10/100/1000 LAN, pull up the 'TCP/IP' tab then 'Configure' IPv4 selecting the 'Manually' option
* Assign and enter the IP 192.168.0.2 and the subnet mask 255.255.255.192
* Next assign the default gateway by selecting 'Router' and assign the IP of 192.168.0.1 this will ensure that our LANs can be connected across the network 
* Next repeat a similar step with laptop2, go to 'System Settings', 'Network','Other Services' then select USB 10/100/1000 LAN, pull up the 'TCP/IP' tab then 'Configure' IPv4 select the 'Manually' option
* Assign and enter the IP 192.168.0.3 and the subnet mask 255.255.255.192
* Next assign the default gateway by selecting 'Router' and assign the IP of 192.168.0.1

4. Ensure Conectivity between devices
* In laptop1 pull up the Terminal application, and enter "ping 192.168.0.3"
* If the laptop can successfully  communicate with the others we will receive a reply from the IP address and a 0% loss
* Repeat this step on laptop2, pull up Terminal and enter "ping 192.168.0.2"
* If the connection is successful the replies will not stop running, to stop the application hit control c

5. Set up the Webserver on Laptop1
* Using laptop 1, open the MAMP application, select Nginx, go into preferences and select the port to edit the Nginx port to 80
* Start running the server by hitting the start button
* Next, we want to create an index.html do this by opening the MAMP application, clicking htdocs then index.html
* Open TextEdit application select the same index.html file and write "Welcome to Capstone Consulting"
* Now to test our page, laptop2 should search HTTP:/192.168.0.2 into their browser and ensure the message we put in TextEdit appears

6. Set up the DNS server 
* The DNS, or domain name system server will translate domain names into IP addresses, this allows us to look up a more human-friendly domain instead of an IP address
* Taking laptop2, open the NAMO application, create a new host by hitting the +, and add the new hostname by entering capstoneconsulting.com
* Assign IP address to the MAMP server 192.168.0.2, the address of laptop1. This was the DNS server that would send requests for capstoneconsulting.com to that IP
* In laptop1 go to webserver device System Settings, 'Network', 'Configuration Details', go to DNS servers and if there are IPs currently there, make sure to delete and clear them, now input the laptop2 IP address 192.168.0.3
* What we did ensure that all requests for capstoneconsulting.com will go through our DNS server, which will then translate the domain name into the webservers IP address that directs the browser to the webpage hosted on that IP address

7. Connect the network to the router
* Check that the two ethernet cables from the switch are plugged into ports g0/0 and g0/1
* Connect a serial console cable from the router to one of the networked laptops
* Next, we need to configure the default gateway on each LAN on the router
* Input two IPs addresses, one for each LAN. The first IP is 192.168.0.1 with a subnet mask 255.255.255.192 this is the deafult gateway for the LAN we configured. The second LANs IP address is 172.16.0.1 with a subnet mask 255.255.255.0, this is the default gateway for our second LAN
* Using the networked laptop that has the serial console cable plugged in,
   Open Terminal to input the following commands:
  1. router enable - allowing changes to be made in EXEC mode
  2. configure terminal - this should be input after Router#
  3. hostname router01
  4. interface gigabitEthernet 0/0
  5. ip address 192.168.0.1 255.255.255.192
  6. description ##to switch 01## - to show the connection we are creating from the router to switch
  7. no shutdown - this turns port status on
  8. exit - to leave this configuration
  9. wr - will write this configuration into the system's memory
  10. show startup-config - confirm that this configuration has been permanently saved
* Repeat this process on the other LANs IP

8. Confirm connectivity to the other LAN
* Now that our router is configured and we have assigned a default gateway we need to ping the other LAN
* Open terminal in laptop1 and ping 172.16.0.2, if the ping replies our configuration was successful 

### Frequently Asked Questions 

1. Laptop1 cannot communicate with Laptop2?
* Check connectivity by pinging the other laptop through the IP address
* If there is no response, ensure there are no typos, or missing, IP address assignments and subnet masks
* Check that ethernet cables are plugged securely and that the switch is on

2. Is the firewall interfering with my webpage?
* When configuring this network it is possible that the firewall can interfere with your DNS and webserver
* When creating and utilizing this network temporarily disable all firewalls

3. Laptop cannot communicate across the network to a different LAN?
* It is most likely that there is a missing default gateway
* Check that all configurations of the router are correct

4. How do I expand this network?
* Follow the steps outlined with a new network by assigning new IPs and a default gateway to the LAN

5. How can I practice building this network if I don't have the physical hardware?
* The Cisco packet tracer application and go through the online simulation to become familiar with the configurations
* This way you can also ensure that the devices you are trying to connect will work and respond to each other before you need to incorporate it into real-world application 

### Retrospective Reflection 

Throughout this project, I had the opportunity to work on the configuration and implementation of a basic network using both virtual and physical networking tools. This process was extremely beneficial to me, I enhanced my technical abilities through hands-on learning and by doing this, developed a deeper understanding of how different network components interact. 

##### Challenges Encountered 

The challenges we faced while building this network primarily stemmed from configuring the DNS server. We had trouble getting our "Welcome to Capstone Consulting" message to appear. We were able to combat this issue by reviewing all configurations and then disabling our firewall. It turned out that it was the firewall interfering with our server. Our team worked very well together and were able to get through any problems that we encountered efficiently. Most of the challenges with this project that I encountered were personal. I feel I now know what I need to do differently to ensure my success in upcoming projects. For me, that means taking detailed notes in class and during the lab. I believe one of the most important things I need to do in the future is work with and collaborate with my peers when studying and for questions I have about any projects. This also means scheduling office hours if I ever feel myself not fully grasping a concept or if I am overwhelmed by the material. 

##### New Skills and Insights 

I have gained a plethora of new skills while going through this lab and project. Before starting this class, I knew little to nothing about building a network or how we accessed the internet or web pages. After this experience, I can say I know how to configure a DNS and web server. In addition, I can set up my own network using physical hardware. Through this lab I feel that I learned a lot of new information very quickly and was able to get a solid foundation into my understanding of networking. 


##### Areas for Improvement 

The primary thing I believe I need to do differently to have better retention for this lab is writing down each step as the group went along. I struggled a lot with understanding and remembering the details of the lab when I couldn't go back on my own to redo it. This way, even if I'm not fully grasping why we are doing a certain step in the lab, I can refer back to what it was specifically to ask questions about it. 


##### Conclusion 

Overall, this project challenged me in ways I had not anticipated. But more importantly, it deepened my understanding of network design, simulation, and implementation. The challenges that our group faced with troubleshooting and connectivity issues strengthened our collaboration and teamwork during the lab. We were able to work well as a group together to overcome any issues we faced. Moving forward, I would be sure to take detailed notes of each step and make sure I understood the 'why' behind each configuration step during the lab. I am looking forward to expanding my networking education and experience while applying it to 'real-world' simulations and interviews. 
