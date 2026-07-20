---
acl_categories:
- '@read'
- '@array'
- '@fast'
arguments:
- display_text: key
  key_spec_index: 0
  name: key
  type: key
arity: 2
bannerText: Array is a new data type that is currently in preview and may be subject
  to change.
categories:
- docs
- develop
- stack
- oss
- rs
- rc
- oss
- kubernetes
- clients
command_flags:
- readonly
- fast
complexity: O(1)
description: Returns the length of an array (max index + 1).
function: arlenCommand
group: array
hidden: false
key_specs:
- RO: true
  access: true
  begin_search:
    spec:
      index: 1
    type: index
  find_keys:
    spec:
      keystep: 1
      lastkey: 0
      limit: 0
    type: range
linkTitle: ARLEN
railroad_diagram: /images/railroad/arlen.svg
reply_schema:
  description: The length of the array (max index + 1), or 0 if key does not exist.
  type: integer
since: 8.8.0
summary: Returns the length of an array (max index + 1).
syntax_fmt: ARLEN key
title: ARLEN
---
Returns the length of an array (max index + 1).

## Required arguments

<details open><summary><code>key</code></summary>

The name of the key that holds the array.

</details>

## Examples

{{% redis-cli %}}
ARSET myarray 0 "a"
ARSET myarray 5 "b"
ARLEN myarray
ARCOUNT myarray
{{% /redis-cli %}}

## Redis Software and Redis Cloud compatibility

| Redis<br />Software | Redis<br />Cloud | <span style="min-width: 9em; display: table-cell">Notes</span> |
|:----------------------|:-----------------|:------|
| <span title="Not supported">&#x274c; Standard</span><br /><span title="Not supported"><nobr>&#x274c; Active-Active</nobr></span> | <span title="Not supported">&#x274c; Standard</span><br /><span title="Not supported"><nobr>&#x274c; Active-Active</nobr></span> |  |

## Return information

{{< multitabs id="return-info"
    tab1="RESP2"
    tab2="RESP3" >}}

[Integer reply](../../develop/reference/protocol-spec#integers): The length of the array (max index + 1), or 0 if key does not exist.

-tab-sep-

[Integer reply](../../develop/reference/protocol-spec#integers): The length of the array (max index + 1), or 0 if key does not exist.

{{< /multitabs >}}
