# Step-by-Step Configuration Guide

### Objective 

The following deliverables demonstrate how to design, simulate, and implement a basic network. This is achieved by using both virtual tools and physical devices to showcase how different network components connect and interact. This includes diagraming a basic network in Packet Tracer by integrating two LANs, as well as setting up essential network services, like a web server and a DNS server, by using physical Cisco devices. 

### Use Cases for the System

This system can be used in a variety of practical ways within IT and systems administration. 

Below are potential uses for this network:
1. Small Business Network Setup: This design can connect multiple LANs in small to medium-sized businesses by using separate networks for departments such as HR, Marketing, or Finance.
2. LMU: Universities use a LAN network for students and staff to communicate with different networks on campus, wheather that is from the classroom, dorms or office buildings. 
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
* Next repeat a similar step with laptop2, go to 'System Settings', 'Network','Other Services' then select USB 10/100/1000 LAN, pull up the 'TCP/IP' tab then 'Configure' IPv4 selecting the 'Manually' option
* Assign and enter the IP 192.168.0.3 and the subnet mask 255.255.255.192
* Next assign the default gateway by selecting 'Router' and assign the IP of 192.168.0.1

4. Ensure Conectivity between devices
* In laptop1 pull up the Terminal application, and enter "ping 192.168.0.3"
* If the laptop can successfully  communicate with the others we will recieve a reply from the IP address and a 0% loss
* Repeat this step on laptop2, pull up Terminal and enter "ping 192.168.0.2"
* If the connection is successful the replies will not stop running, to stop the application hit control c


### Frequently Asked Questions 

### Retrospective Reflection 

Throughout this project, I had the opportunity to work on the configuration and implementation of a basic network using both virtual and physical networking tools. This process was extremely beneficial to me, I enhanced my technical abilities through hands-on learning and by doing this, developed a deeper understanding of how different network components interact. 

##### Challenges Encountered 




##### New Skills and Insights 

##### Areas for Improvement 

The primary thing I believe I need to do differently to have better retention for this lab is writing down each step as the group went along. I struggled a lot with understanding and remembering the details of the lab when I couldn't go back on my own to redo it. This way, even if I'm not fully grasping why we are doing a certain step in the lab, I can refer back to what it was specifically to ask questions about it. 


##### Conclusion 

Overall, this project challenged me in ways I had not anticipated. But more importantly, it deepened my understanding of network design, simulation, and implementation. The challenges that our group faced with troubleshooting and connectivity issues strengthened our collaboration and teamwork during the lab. We were able to work well as a group together to overcome any issues we faced. Moving forward, I would be sure to take detailed notes of each step and make sure I understood the 'why' behind each configuration step during the lab. I am looking forward to expanding my networking education and experience while applying it to 'real-world' simulations and interviews. 
