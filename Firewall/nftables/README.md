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

---
# Families

Abstractisation of multiple networking levels.

>[!NOTE]
> What traffic/packets are seen and at which point in the network stack dependson the [hook](https://wiki.nftables.org/wiki-nftables/index.php/Netfilter_hooks) that is being used.

## Current nftables families:

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

---
# Tables

Tables are the top-level containers within an nftables ruleset   

Each table belongs to exactly one family. So your ruleset requires at least one table for each family you want to filter. 
 
## Syntax:

```bash
nft list tables [<family>]
nft [-n] [-a] list table [<family>] <name>
nft (add | delete | flush) table [<family>] <name>

# [-n] -> shows the addresses and other information that use names in numeric format.
# [-a] -> used to display each rule's handle (i.e., a numeric identifier).
```

---
# Chains

As in {ip, ip6}\_tables, chains are containers that store the rules.

There are 2 types of chains:
- **Basic chains**:
Base chains are directly attached to Netfilter hooks, allowing them to process packets as they flow through the network stack.</br>
**Characteristics**:</br>
    - <ins>Processing</ins>: They evaluate packets directly and can accept or drop them based on defined rules.
    - <ins>Hooks</ins>: Must be linked to specific hooks such as input, output, or forward.
    - <ins>Priority</ins>: Each base chain has a priority that determines the order of processing among multiple chains at the same hook.
- **Regular chains**:
</br>Regular chains are not attached to any Netfilter hooks and do not process packets directly. Instead, they are called from base chains.</br>
**Characteristics**:</br>
    - <ins>Usage</ins>: Primarily used for organizing rules and can be invoked using jump or goto commands from base chains.
    - <ins>No Direct Processing</ins>: They do not see packets unless called by a base chain.

## Syntax

Command line syntax

```bash
# Shell mode
nft (add | create) chain [<family>] <table> <name> [ '{ type <type> hook <hook> [device <device>] priority <priority> \; [policy <policy> \;] }' ]
nft (delete | list | flush) chain [<family>] <table> <name>
nft rename chain [<family>] <table> <name> <newname>'

# Interactive mode
nft -i

add chain [<family>] <table_name> <chain_name> { type <type> hook <hook> [device <device>] priority <priority> ; [policy <policy> ;] [comment <comment> ;] }
```

### Base Chain Types

| Chain Types | Description | Supported Families | 
| :---: | :--- |
| `filter` | Used to filter packets. | `ip`</br>`ip6`</br>`inet` |
| `route` | Used to reroute packets if any relevant IP header field or the packet mark is modified.</br></br>If you are familiar with *iptables*, this chain type provides equivalent semantics to the *mangle* table but only for *output* hook (for other hooks use type *filter* instead).| `ip`</br>`ip6`</br>`inet` |
| `nat` | Used to perform Networking Address Translation (NAT).</br></br>Only the first packet of a given flow hits this chain; subsequent packets bypass it.</br>Therefore, never use this chain for filtering. | `ip`</br>`ip6`</br>`inet` |

### Base Chain Hooks

| Hooks | Description |
| :---: | :--- |
| `ingress` | Sees packets immediately after they are passed up from the NIC driver, before even prerouting.</br></br>An alternative to `tc` |
| `prerouting` | Sees all incoming packets, before any routing decision has been made.</br></br>Packets may be addressed to the local or remote systems. |
| `input` | Sees incoming that are addressed to and have now been routed to the local system and processes running there. |
| `forward` | Sees incoming packets that are not addressed to the local system. |
| `output` | Sees packets that originated from processes in the local machine. |
| `postrouting` | Sees all packets after routing, just before they leave the local system. |

### Base Chain Priority

Each nftables base chain is assigned a [priority](https://wiki.nftables.org/wiki-nftables/index.php/Netfilter_hooks#Priority_within_hook:~:text=Priority%20within%20hook) that defines its ordering among other base chains flowtables, and Netfilter internal operations at the same hook.

> [!NOTE]
> If a packet is accepted and there is another chain, bearing the same hook type and with a later priority, then the packet will subsequently traverse this other chain. Hence, an accept verdict - be it by way of a rule or the default chain policy - isn't necessarily final. However, the same is not true of packets that are subjected to a drop verdict. Instead, drops take immediate effect, with no further rules or chains being evaluated.

### Base Chain Policy
