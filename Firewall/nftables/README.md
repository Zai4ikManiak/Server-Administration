### What is `nftables`?

**nftables** is the modern Linux kernel packet classification framework, that replaces the older legacy {ip,ip6,arp,eb}\_tables (xtables) infrastructure.

It is composed of the following elements:
- **family** </br>Abstractisation of multiple networking levels.
    - **tables**
        - **chains**
        - **sets**
        - **maps**
        - **flowtables**
        - **stateful objects**
