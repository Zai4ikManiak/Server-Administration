# Descriptions of current nftables families:

| Family | Description | Equivalent tool |
| :---: | :--- | :--- |
| `ip` | Tables of this family see IPv4 traffic/packets. | `iptables` is the legacy x\_tables equivalent. |
| `ip6` | Tables of this family see IPv6 traffic/packets. | `ip6tables` is the legacy x\_tables equivalent. |
| `inet` | Tables of this family see both IPv4 and IPv6 traffic/packets, simplifying dual stack support.</br></br>Rules for L4 do not affect simultaneously both IPv4 and IPv6 packets. Rules for both L3 protocols affect both.</br></br>Use `meta l4proto` to match on the L4 protocol, regardless of whether is IPv4 or IPv6.| |
| `arp` | Tables of this family see ARP-level traffic befor any L3 handling is done by the kernel. | `arptables` is the legacy x\_tables equivalent. |
| `bridge` | Tables of this family see traffic/packets traversing bridges (i.e. switching). No assumptions are made about L3 protocols.</br></br>Note that there is no `nf_conntrack` integration for the nftables bridge family. | `ebtables` is the legacy x\_tables equivalent. |
| `netdev` | Used to create base chains attached to a **single network interface**.</br></br> Such base chains see **all network traffic on the specified interface**, with no assumptions about L2 or L3 protocols. Therefore ARP traffic can be filtered from here.</br></br>The principal use for this family is for base chains using the ingress hook. Such *ingress chains* see network packets just after teh NIC driver passes them up to the networking stack.</br>This is very effective against DDoS attacks.</br></br>Can be aslo used for load balancing, including Direct Server Return(DSR). | |
