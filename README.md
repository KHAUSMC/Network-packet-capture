# Network Packet Capture and Analysis


## Task 1: Identify Network Interfaces

In this task, I will identify the network interfaces that can be used to capture network packet data.

To list the available network interfaces, I use:

```bash
sudo ifconfig
```

![Insert Picture Here](https://i.imgur.com/IzRVKkT.png)

The Ethernet network interface is identified by the entry with the `eth` prefix.

To identify available network interfaces for packet capture, I use:

```bash
sudo tcpdump -D
```

![Insert Picture Here](https://i.imgur.com/y88yfPM.png)

This command will display all available network interfaces and is useful on systems that do not include the `ifconfig` command.

## Task 2: Inspect Network Traffic with tcpdump

In this task, I will use `tcpdump` to filter live network packet traffic on an interface.

To filter live network packet data from the `eth0` interface, I run:

```bash
sudo tcpdump -i eth0 -v -c5
```

### Command Breakdown:
- `-i eth0`: Captures data from the `eth0` interface.
- `-v`: Displays detailed packet data.
- `-c5`: Captures 5 packets of data.

![Insert Picture Here](https://i.imgur.com/IJO3DA6.png)

## Task 3: Capture Network Traffic with tcpdump

Now, I will capture network data and save it to a file.

To capture packet data into a file named `capture.pcap`, I run:

```bash
sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap &
```

### Command Breakdown:
- `-i eth0`: Captures data from the `eth0` interface.
- `-nn`: Disables IP address and port resolution.
- `-c9`: Captures 9 packets before stopping.
- `port 80`: Filters only HTTP traffic.
- `-w capture.pcap`: Saves the captured data to a file.
- `&`: Runs the process in the background.
 
To generate HTTP traffic, I use:

```bash
curl opensource.google.com
```

To verify that packet data has been captured, I run:

```bash
ls -l capture.pcap
```

![Insert Picture Here](https://i.imgur.com/nXiYAnt.png)

## Task 4: Filter Captured Packet Data

I will now filter and analyze the captured data.

To filter packet headers from `capture.pcap`, I use:

```bash
sudo tcpdump -nn -r capture.pcap -v
```
![Insert Picture Here](https://i.imgur.com/hJd2r1f.png)

### Command Breakdown:
- `-nn`: Disables IP and port resolution.
- `-r capture.pcap`: Reads data from the saved file.
- `-v`: Displays detailed packet data.

To display extended packet data with hexadecimal and ASCII format, I run:

```bash
sudo tcpdump -nn -r capture.pcap -X
```

![Insert Picture Here](https://i.imgur.com/uLCu6xw.png)

This helps in forensic and malware analysis by allowing security analysts to detect patterns or anomalies.

---

With these steps, I can successfully identify network interfaces, inspect live network traffic, capture packets, and filter stored data using `tcpdump`. 🚀
