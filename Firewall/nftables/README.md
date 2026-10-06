### What is `nftables`?

**nftables** is the modern Linux kernel packet classification framework, that replaces the older legacy {ip,ip6,arp,eb}\_tables (xtables) infrastructure.

It is composed of the following elements:
- [families](https://github.com/Zai4ikManiak/Server-Administration/blob/main/Firewall/nftables/Families.md) </br>Abstractisation of multiple networking levels.</br></br>Note that what traffic/packets are seen and at which point in the network stack dependson the [hook](https://wiki.nftables.org/wiki-nftables/index.php/Netfilter_hooks) that is being used.
    - **tables**
        - **chains**
        - **sets**
        - **maps**
        - **flowtables**
        - **stateful objects**
