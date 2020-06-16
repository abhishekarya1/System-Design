# Step 1: Scalability lecture at Harvard
[CS75 Lecture Video](https://youtu.be/-W9F__D3oY4)
<br>
[Lecture Slides](http://cdn.cs75.net/2012/summer/lectures/9/lecture9.pdf)

## Topics covered
- **Verical Scaling:** Throwing more resources in, equivalent to throwing money at the problem. Can't scale well on a single machine.
- **Horizontal Scaling:** Get a bunch of cheaper machines instead of upgrading just one. 
- **Load Balancing:** Install a *load balancer* in between clients and backend servers. This way we just have access to the *load balancer* which serves requests and routes data between client and servers.
- **Caching:** DNS records (containing IP address of one of the DNS servers) are cached on a machine often and pose a serious problem of overloading servers that they're "bound" to because multiple machines can cache the same DNS server over time. This is solved by TTL (Time To Live), the DNS record cache is cleared after TTL is expired and machine requests a new one.
- **Shared Session State:** Cookies and sessions (like in PHP) break this model, as different servers have different session data about the same user now. Put storage on the *load balancer* (it's a central server now) and store session data on it. But now, it is the single point of failure (SPOF). 
- **RAID:** ("Redundant Array of Inexpensive Disks" or "Redundant Array of Independent Disks"). RAID 0 to 10. [Standard levels - 0 to 6](https://www.prepressure.com/library/technology/raid).
- **Shared Storage Technology:** or use MySQL DB, NFS (Network File System) - A protocol to share data over multiple serveres, etc... 
- **Database Replication:** Copy data to multiple servers to avoid SPOF and synchronize them periodically.
- **Load Balancing Technology:** It is costly for enterprise but same ideas can be setup by your own quite readily these days for free like *HAProxy*.
- **Session Affinity:** Store ID of the server in a cookie on the client's browser. Index it usng PHP, with a indexing table on *load balancer*.
- **In-memory Caching:** 
  - MySQL query cache: after it is enabled, it caches results of queries.
  - PHP memchache: software that runs alongside the main server software, it stores data in indexed tables rather than a database.  
- **Data Replication:** 
  - *active:passive* - *master* is "active", *slaves* copy/replicate data on them from the *master*.
  - *active:active* - multiple *masters* connected to each other, each *master* has further *slaves*.
- **Partitioning:** Partition the database and replicate data to all partitions, but data transfer overhead can be a bottleneck.
- **Data Center Redundancy:** Protection against physical damage to the data center can be avoided by cloud computing like AWS EC2 where servers are physically quarantined from each other completely. 
- **Security:** Encrypt the link with HTTPS (443), allow only certain ports, install firewalls, etc...  

### Extras
- **Storage drives speeds:** PATA/IDE < SATA < SAS < SSD (SATA) < SSD (SAS) 
  - **PATA:** Parellel ATA
  - **SATA:** Serial ATA (typically 7.2 rpm)
  - **SAS:** Serial Attached SCSI (SCSI Stands for Small Computer System Interface, typically pronounced as "scuzzy")(upto 15k rpm)
  - **SSD:** Solid-State Drive
