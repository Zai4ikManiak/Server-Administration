### What is `nftables`?

**nftables** is the modern Linux kernel packet classification framework, that replaces the older legacy {ip,ip6,arp,eb}\_tables (xtables) infrastructure.

It is composed of the following elements:
- **family**
    - **tables**
        - **chains**
        - **sets**
        - **maps**
        - **flowtables**
        - **stateful objects**

```mermaid
---
config:
    treeView:
        showIcons: false
---
treeView-beta
    family ## Abstractisation of multiple networking levels.
        tables ## Top-level containers within nftables ruleset.
            chains
            sets
            maps
            flowtables
            stateful onjects
```
