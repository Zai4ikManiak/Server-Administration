### What is `nftables`?

**nftables** is the modern Linux kernel packet classification framework, that replaces the older legacy {ip,ip6,arp,eb}\_tables (xtables) infrastructure.

It is composed of the following elements:
- **family** </br>Abstractisation of multiple networking levels.</br>Note that what traffic/packets are seen and at which point in the network stack dependson the **hook** that is being used.
    - **tables**
        - **chains**
        - **sets**
        - **maps**
        - **flowtables**
        - **stateful objects**
