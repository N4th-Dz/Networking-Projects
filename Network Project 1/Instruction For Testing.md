######################################################
######### NOTE: CREDENTIALS OF EACH DEVICES ##########
######################################################

<h3> All Network Devices </h3>

Line Console Credentials
username: nath
password: cisco

Enable Credentials
password: cisco

SSH Remote Access Credentials
username: nath
password: cisco

###################################################
Instruction:

1. First, open the .pkt file in Cisco Packet Tracer


2. Verify first if all host did get an ip address from the DHCP
   To verify:
     A. First, click any host computer in the topology (in the picture below, I clicked the CSR Department Host computer, and another window will pop-up)
          <img width="1564" height="789" alt="image" src="https://github.com/user-attachments/assets/6c1b50e4-0ef4-42cd-a956-f1fa58d3fa4f" />
     B. Second, click the Config, then click FastEthernet0
         -  Under the Ip configuration, you should see IP Address from its own network/subnet (refer to the Network Information.txt file that is included in this github repo)
         - For our example, since we use a host computer on CSR Department, we are expecting to have ip address under the network/subnet 192.168.10.0/24
          <img width="1387" height="774" alt="image" src="https://github.com/user-attachments/assets/f8536008-4ae0-45e9-8356-31aa17f25b34" />
     C. Sometimes, when devices that are used is still booting up, sometimes our host computer cant establish a connection with the DHCP (this is a problem with the emulator like cisco packet tracer), so what you can do is           to just reset the port by clicking the Port Status on to off to on, then under ip configuration click static then back to dhcp (in this way it will reset the port)
         <img width="946" height="531" alt="image" src="https://github.com/user-attachments/assets/d854438a-1745-4e19-bac8-6dd452d588cf" />
3. After verifying that all host computers in all VLANs has their own IPV4 address already we can now test other things
     A. Test for IPSEC Tunnel (Main)
         - From the host computer of CSR Department, we need to click the Desktop, then Command Prompt
           <img width="934" height="531" alt="image" src="https://github.com/user-attachments/assets/53510595-1c83-4eca-92f6-e7321984dade" />
         - We can ping the DHCP Server (172.16.17.4) from our host computer, and if ping is successful, to verify if the packet traverse via the IPSEC Tunnel is we need to access the HQ Router 
           <img width="686" height="691" alt="image" src="https://github.com/user-attachments/assets/c1117e9c-bedc-43f5-96c6-504bce2fd167" />
         - From the HQ Router, as you can see from our HQ Router, the packet went through the IPSEC Tunnel
           <img width="691" height="697" alt="image" src="https://github.com/user-attachments/assets/1d316fc2-38c5-417a-a1cf-02367965ad4c" />
