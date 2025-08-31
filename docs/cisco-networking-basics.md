# Cisco Networking Basics

## Module 1: Communication in a Connected World

### 1.1. Network Types

Who Owns "The Internet" - No one

Local Network doesn't mean 'small' network. They come in all sizes. Networks installed in small offices, or homes and home offices are referred to as small office/home office (_SOHO_).

### 1.2. Data Transmission

There are severel types of data:

- **Volunteer data:** It is the data that you offer and you are aware of that this data is being collected, stored or shared. And also you are agree with it.
- **Inferred data:** This is the data thay you generate by your activities.
- **Observed data:** As the name explains itself it is the data that is observed and collected. For example, your location. Your phone always keep track of it.

### 1.3. Bandwidth and Throughput

The rate of data transfer is usually discussed in terms of bandwidth and throughput:

**Bandwidth** is the capacity of a medium to carry data. Bandwidth is typically measured in the number of bits that (theoretically) can be sent accross the media in a second.

| Unit of Bandwidth   | Abbreviation | Equivalence                               |
| ------------------- | ------------ | ----------------------------------------- |
| Bits per second     | bps          | 1 bps = fundamental unit of bandwidth     |
| Kilobits per second | Kbps         | 1 Kbps = 1,000 bps = 125 bytes per second |
| ...                 | ...          | ...                                       |

**Throughput** is the measure of the transfer of bits accross the media over a given period of time. However, due to a number of factors, throughput does not usually match the specified bandwidth. Those factors are:

- The amount of data being transmitted over the connection
- The types of data being sent
- The latency created by the number of network devices encountered between source and destination

In an internetwork or network with multiple segments, throughput cannot be faster than the slowest link of the path from sending device to the receiving device. Even if all or most of the segments have high bandwidth, it will only take one segment in the path with lower bandwidth to create a slowdown of the throughput of the entire network.
