# ActiveDirectoryLab

## Description:
    This purpose of this lab is to gain experience creating a virtual network as well as gain
    experience penetration testing with Kali Linux. The virtual network will consist of one Domain
    Controller and two User Machines. The Domain Controller will be running Windows Server 2019
    and the User machines will be running Windows 10. The machine I will be using to attack this
    network will be running Kali Linux.

## Attack Vectors:
    - LLMNR / NBT-NS Poisoning
    - SMB Relay Attacks
    - IPv6 DNS Takeover Attack
    - Pass-the-Password
    - Pass-the-Hash
    - Token Impersonation
    - Kerberoasting
    - Golden Ticket
    - PowerView / Bloodhound
    - Credential Dumping with Mimikatz

## LLMNR / NBT-NS Poisioning:
    Link-Local Multicast Name Resolution and NetNIOS Name
    Service are name resolution services that Windows
    uses to identify host addresses on a network when
    DNS resolution fails. Using this fact we will be
    setting up our Kali Linux Machine on the network and
    have it listening for these broadcasts using Responder.
    When Responder pickups these broadcasts, it will take
    the users password hash and then we will use another
    package called John-The-Ripper to crack the password
    hash.
    The first step was to setup the network and load responder on the Kali machine.

![Setting up Responder](https://i.imgur.com/gJ2dkBd.jpg)
*Responder Setup*

    From that point I had to look up a file on a user machine with a typo, this simulates an activity that could happen on any network when a user mistypes a domain or file location. Once this happens Responder will listen for the broadcast and capture it.

![Responder listening for Hash](https://i.imgur.com/aMfjqC9.jpg)
*Responder Listening for Broadcasts*

    Once the hash is captured we can then use John to crack the password.

![Using John The Ripper to crack hash](https://i.imgur.com/HWkzXgt.jpg)
*Using John to crack hash*

    Since this was a pen testing lab I did not choose complex passwords, so John had no issues cracking the hash and giving me the user and their password.




