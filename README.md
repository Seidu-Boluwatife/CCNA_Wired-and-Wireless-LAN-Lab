# CCNA_Wired-and-Wireless-LAN-Lab
This Lab shows Device Configuration ,Selection of proper cables based on Configuration, Connection of Devices 
Lab 4.6.5 — Connect a Wired and Wireless LAN

**Device Configuration**

Selected the proper cable based on device configuration
Connected devices
Explored the physical view of the network

**Cabling decisions:**

Cloud → Router (Ethernet port to FastEthernet port): Copper straight-through cable
Cloud (Coaxial7) → Cable Modem (Port 0): Coaxial cable
Router0 → Router1: Serial DCE connector (Data Circuit-Terminating Equipment / Data Communication Equipment)
Router0 → NetAcad.pka Server (F0/1 to F0): Copper crossover cable — needed because routers and computers traditionally transmit on the same pins (1,2) and receive on the same pins (3,6). Modern NICs can auto-sense which pair transmits/receives (Auto-MDIX), but this setup did not have auto-sensing enabled.
Router0 → Configuration Terminal: Console (rollover) cable — from the router's console port to the RS-232 port on the terminal, to allow configuration of Router0
Router2 → Switch1: Multi-mode fiber optic cable — assumed distance under 550 meters
Wireless Router → Family PC (FastEthernet port): Copper straight-through cable
Cable Modem → Wireless Router (Internet port): Copper straight-through cable

**Verification:**

Pinged NetAcad.pka server to confirm connectivity, then opened it in a browser via https://netacad.pka
Pinged Switch1 from the Home PC — first request timed out (ARP delay), retry returned all 4 echo replies successfully
Checked interface statuses on Router0 in privileged EXEC mode

**Lessons Learned**
Cable selection depends on both the device types being connected and their physical layer requirements (copper vs. fiber vs. coaxial vs. serial).
Auto-MDIX matters: without it, using the wrong cable type (straight-through vs. crossover) between similar or dissimilar devices will prevent the link from coming up.
On serial WAN links, only one side (DCE) needs a clock rate — this is a common point of confusion when configuring router-to-router links in Packet Tracer.
Initial ping timeouts are often normal (ARP resolution) rather than a sign of misconfiguration; retrying is a valid troubleshooting step before assuming a deeper issue.


