## Networking 
- Network: A group of connected devices that share information.
- IP Address: Unique number assigned to a device (Example: 192.168.1.10).
- DNS (Domain Name System): Converts domain names (google.com)


## What is a network?
- In computing, a network is a collection of two or more computers that can communicate.


## Internet protocol (IP)
- Computers on a network identify themselves and each other with IP addresses, such as 10.0.0.1 or 192.168.0.8
Types of Ip adress
- public IP
- Private IP

## IP Address Classes (Classful Networking)
IPv4 addresses are divided into 5 classes: A, B, C, D, and E.
## IP Address Classes – Summary Table

| Class | First Octet Range | Default Subnet Mask | Purpose / Usage        | Networks  | Hosts per Network |
|-------|--------------------|----------------------|--------------------------|-----------|--------------------|
| **A** | 1 – 126            | 255.0.0.0            | Very large networks      | 128       | ~16 million        |
| **B** | 128 – 191          | 255.255.0.0          | Medium networks          | 16,384    | 65,534             |
| **C** | 192 – 223          | 255.255.255.0        | Small networks           | 2+ million| 254                |
| **D** | 224 – 239          | N/A                  | Multicast groups         | N/A       | N/A                |
| **E** | 240 – 255          | N/A                  | Experimental/Research    | N/A       | N/A                |

### Special Notes
- **0.x.x.x** → Reserved  
- **127.x.x.x** → Loopback (localhost)  

  
## Network Types and Protocols

Types of Networks
- LAN – Local network inside a home/school/office.
- WAN – Large network across regions (Internet).
- MAN – Metropolitan Area Network (city-wide).

Check Network Interfaces
```bash
ifconfig
```
Check Public IP (Internet IP)
```bash
curl ifconfig.me
```


## Difference Between curl and wget
curl
- Used for data transfer between client and server.
- check networks
- Curl is commonly referred to as a non-interactive web browser for the Linux terminal
- curl → Send/receive data

wget
- Used for downloading files from the internet.
- Best for downloading large files, recursive downloads (websites).
- wget → Download file




### AWS-part 
- **Private IP Ranges:**  
  - Class A → 10.0.0.0/8  
  - Class B → 172.16.0.0 – 172.31.0.0/12  
  - Class C → 192.168.0.0/16
