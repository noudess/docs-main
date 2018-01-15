ConnectNodeToNode.
### Arguments
**Name**|**Type**|**Description**
:---|:---|:---
node1|int|
node2|int|
teleport|int|
doorid||

### Example

```perl
my $node1 = 1;
my $node2 = 1;
my $teleport = 1;
my $doorid = 1;

quest::($node1, $node2, $teleport, $doorid); # Returns void
```