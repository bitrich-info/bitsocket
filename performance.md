# Performance

This is the load test of Bitsocket running on low cost (1$ per month) virtual server with following configuration:

- VMware hypervisor
- CPU: 1 vCore
- RAM: 1 GB

## Results

### Latency per clients
First test distributed 1 message per second. Connected clients has been increased by 100 every two minutes. Following graph shows latency for connected clients. 

[![performance results](assets/images/perf1.png "Performance results 1")](assets/images/perf1.png)

If we send 2 messages per second, distribution is working nearly same until 3000 clients. This is the cap for given server configuration.

[![performance results](assets/images/perf2.png "Performance results 2")](assets/images/perf2.png)

Network latencies are not included.

### Latency per messages

TODO