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
         - From the HQ Router, as you can see from our HQ Router, the packet went through the Main IPSEC Tunnel
           <img width="691" height="697" alt="image" src="https://github.com/user-attachments/assets/1d316fc2-38c5-417a-a1cf-02367965ad4c" />
         - Same as well with Branch Router, the return traffic also traverse via the Main IPSEC Tunnel
            <img width="688" height="678" alt="image" src="https://github.com/user-attachments/assets/5e30c735-d4f0-452e-af74-5bc1869e744a" />
         - As you can see, the Backup IPSEC Tunnel, did not encrypt any packet since it will just work as the Main IPSEC Tunnel goes down
            <img width="671" height="607" alt="image" src="https://github.com/user-attachments/assets/f5a04ec5-6e7c-4c8e-a820-da4f0665324b" />
      B. Test for IPSEC Tunnel (Backup)
         - To test our back up ipsec tunnel, we need to perform a continuous ping from our host computer to the DHCP Server (or any host in the Server Vlan in the Branch Office, since in our network policy (any host from              HQ Office can only ping and access the servers in the Server Vlan in Branch Office)
            <img width="684" height="696" alt="image" src="https://github.com/user-attachments/assets/73b37268-3ff6-4501-8427-8f08434e3b32" />
         - After that, we need to shutdown the ISP Main to shut all its links, just click the power button to turn off the device
            <img width="833" height="512" alt="image" src="https://github.com/user-attachments/assets/a4e646c5-9431-4435-bca5-2896d6c8b923" />
         - Then we need to verify from our host computer where we performed a continuous ping
            <img width="659" height="664" alt="image" src="https://github.com/user-attachments/assets/421d8017-feb0-4339-9b00-ff2f5172d93b" />
         - As you can see at the photo below, the ping timed out (as we turn off the ISP Main Router, the MAIN IPSEC Tunnel went down as well) and ping went back after (as the traffic failover in the Backup IPSEC Tunnel)
            <img width="565" height="535" alt="image" src="https://github.com/user-attachments/assets/1707af71-bb94-4904-9ddb-951e1276add7" />
         - As a further verification, the Backup IPSEC Tunnel packets encryption increment proving that the traffic really failover on it
            <img width="684" height="648" alt="image" src="https://github.com/user-attachments/assets/2fd1cdac-3262-42cd-bb0e-60c8276ee18e" />

      B. Test for NAT/PAT
         - To test NAT/PAT, traffic from any of our host computers are being NAT'ed only if they are going to the internet (For our topology, for example is 9.9.9.9)
         - From any host computer, we need to ping the address 9.9.9.9
            <img width="1441" height="801" alt="image" src="https://github.com/user-attachments/assets/e1aa2fea-63de-4141-bcf8-07b1764b471c" />
         - Then we need to go to the HQ Router, to verify if our privated IPV4 Address is NAT'ed
         - As you can see, our private IPV4 address 192.168.10.6 was translated to a public ip address 105.16.0.1 (public ip of any host in HQ Router)
            <img width="669" height="121" alt="image" src="https://github.com/user-attachments/assets/86472a74-ef40-4464-b91a-e72a58bd0841" />

      C. Test for ACL
         - You can 
