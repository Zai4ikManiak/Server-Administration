# What is `nftables`?

**nftables** is the modern Linux kernel packet classification framework, that replaces the older legacy {ip,ip6,arp,eb}\_tables (xtables) infrastructure.

It is composed of the following elements:
- **families**
    - **tables**
        - **chains**
        - **sets**
        - **maps**
        - **flowtables**
        - **stateful objects**

## Families

Abstractisation of multiple networking levels.

>[!NOTE]
> What traffic/packets are seen and at which point in the network stack dependson the [hook](https://wiki.nftables.org/wiki-nftables/index.php/Netfilter_hooks) that is being used.

### Current nftables families:

| Family | Description | Equivalent tool |
| :---: | :--- | :--- |
| `ip` | Tables of this family see IPv4 traffic/packets. | `iptables` is the legacy x\_tables equivalent. |
| `ip6` | Tables of this family see IPv6 traffic/packets. | `ip6tables` is the legacy x\_tables equivalent. |
| `inet` | Tables of this family see both IPv4 and IPv6 traffic/packets, simplifying dual stack support.</br></br>Rules for L4 do not affect simultaneously
 both IPv4 and IPv6 packets. Rules for both L3 protocols affect both.</br></br>Use `meta l4proto` to match on the L4 protocol, regardless of whether is IPv
4 or IPv6.| |
| `arp` | Tables of this family see ARP-level traffic befor any L3 handling is done by the kernel. | `arptables` is the legacy x\_tables equivalent. |
| `bridge` | Tables of this family see traffic/packets traversing bridges (i.e. switching). No assumptions are made about L3 protocols.</br></br>Note that 
there is no `nf_conntrack` integration for the nftables bridge family. | `ebtables` is the legacy x\_tables equivalent. |
| `netdev` | Used to create base chains attached to a **single network interface**.</br></br> Such base chains see **all network traffic on the specified i
nterface**, with no assumptions about L2 or L3 protocols. Therefore ARP traffic can be filtered from here.</br></br>The principal use for this family is fo
r base chains using the [ingress hook](https://wiki.nftables.org/wiki-nftables/index.php/Netfilter_hooks). | |

## Tables

Tables are the top-level containers within an nftables ruleset   

Each table belongs to exactly one family. So your ruleset requires at least one table for each family you want to filter. 
 
### Syntax:

```bash
nft list tables [<family>]
nft [-n] [-a] list table [<family>] <name>
nft (add | delete | flush) table [<family>] <name>

# [-n] -> shows the addresses and other information that use names in numeric format.
# [-a] -> used to display each rule's handle (i.e., a numeric identifier).
```

## Chains
    
### Syntax

```bash
nft (add | create) chain [<family>] <table> <name> [ \{ type <type> hook <hook> [device <device>] priority <priority> \; [policy <policy> \;] \} ]
nft (delete | list | flush) chain [<family>] <table> <name>
nft rename chain [<family>] <table> <name> <newname>
```
