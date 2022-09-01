---
recall: header
---


### What are the prefix powers from `kilo` through `exa`?

**Prefix**|**Power**
:-----:|:-----:
exa|10<sup>18</sup>
peta|10<sup>15</sup>
tera|10<sup>12</sup>
giga|10<sup>9</sup>
mega|10<sup>6</sup>
kilo|10<sup>3</sup>


### What is the Compression Speed of Zippy/Snappy?

0.003 ms per 1 KB


### How long does it take to transmit 1 KB over a 1 Gbps line?

0.01 ms


### How many MB can be handled by a 1 Gbps line?

125 MB = 1 Gb


### How long does it take to read 4 MB, stored sequentially, on:
 
* RAM
* SSD
* HDD

**Storage**|**Read Time**
:-----:|:-----:
RAM|1 ms
SSD|20 ms
HDD|80 ms


### How long is a single disk seek?

10 ms


### Roughly how much Bandwidth exists between Data Centers?

±100 Gbps


### What is the Roundtrip Time between Data Centers?

150 ms


### How large is the Average Video (in storage per time)?

10 MB per minute


### How much RAM can exist on a modern-day server?

256 GB


### What is the Optimum Storage Capacity per Cassandra Node?

1-2 TB


### How many Requests can be handled per Cassandra Node?

10,000 - 15,000 requests per second
 
(grows linearly with the number of nodes)


### What are the Storage and Bandwidth requirements for 480p - 4k Video?
 
(with storage measured in MB per minute of content)

**Resolution**|**Storage/Minute**|**Bandwidth**
:-----:|:-----:|:-----:
480p|2 MB|500 Kbps
720p|5 MB|1 Mbps
1080p|20 MB|5 Mbps
4k|84 MB|20 Mbps
 
[source](https://www.cablecompare.com/blog/how-much-internet-bandwidth-do-i-need)


### What is the average rate of HDD death in a Data Center?

1 death per day per 10,000 drives


### In base64, how many bits does a character represent?

Each character encodes 6 bits


### How many bits are needed per character for ASCII?

Each character requires 1 byte (8 bits)


### What is the max number of bytes that a unicode character will consume?

Unicode will consume 1-3 bytes per character.
 
(It is a variable length encoding).


### What is the avg and max size of a "pastebin" document?

Avg = 10 KB
 
Max = 10 MB


### What is an assumed size of a photo?

200 KB


### What is an assumed ceiling for number of connections a web server can have open?

500


### What is the size of the following in a database?
 
* UserID
* DateTime
* Name
* Email
* URL/S3-Key

**Column**|**Size**
:-----:|:-----:
UserID|4 bytes
DateTime|4 bytes
Name|20 bytes
Email|32 bytes
URL/S3-Key|256 bytes


### How much RAM can a high-end commercial server have?

144 GB


### What is an assumed size of the average text message?

100 bytes
