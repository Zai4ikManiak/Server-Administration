**Verdict statements** alters control flow in the ruleset and issues policy decisions for packets. The valid verdict statements are:

- **accept**:</br>Accept the packet and stop the remain rules evaluation.
- **drop**:</br>Drop the packet adn stop the remain rules evaulation.
- **queue**:</br>Queue the packet to userspace and stop the remain rules evaluation.
- **continue**:</br>Continue the ruleset evaluation with the next rule.
- **reuturn**:</br>Return from the current chain and continue at the next rule of tha last chain. In a base chain it is equivalent to accept.
- **jump <chain>**:</br>Continue at the first rule of <chain>. It will continue at the next rule after a return statement is issued.
- **goto <chain>**:</br>Similar to jump, but after the new cahin the evaluation will contiune at the last chain instead of the one containing the goto statement.
