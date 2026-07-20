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
- display_text: index
  name: index
  type: integer
arity: 3
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
description: Gets the value at an index in an array.
function: argetCommand
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
linkTitle: ARGET
railroad_diagram: /images/railroad/arget.svg
reply_schema:
  oneOf:
  - description: The value at the given index.
    type: string
  - description: Null reply if key or index does not exist.
    type: 'null'
since: 8.8.0
summary: Gets the value at an index in an array.
syntax_fmt: ARGET key index
title: ARGET
---
Gets the value at an index in an array.

## Required arguments

<details open><summary><code>key</code></summary>

The name of the key that holds the array.

</details>

<details open><summary><code>index</code></summary>

The zero-based integer index of the element to retrieve.

</details>

## Examples

{{% redis-cli %}}
ARSET myarray 0 "hello"
ARGET myarray 0
ARGET myarray 1
{{% /redis-cli %}}

## Redis Software and Redis Cloud compatibility

| Redis<br />Software | Redis<br />Cloud | <span style="min-width: 9em; display: table-cell">Notes</span> |
|:----------------------|:-----------------|:------|
| <span title="Not supported">&#x274c; Standard</span><br /><span title="Not supported"><nobr>&#x274c; Active-Active</nobr></span> | <span title="Not supported">&#x274c; Standard</span><br /><span title="Not supported"><nobr>&#x274c; Active-Active</nobr></span> |  |

## Return information

{{< multitabs id="return-info"
    tab1="RESP2"
    tab2="RESP3" >}}

One of the following:
* [Bulk string reply](../../develop/reference/protocol-spec#bulk-strings): The value at the given index.
* [Nil reply](../../develop/reference/protocol-spec#null-bulk-strings): Null reply if key or index does not exist.

-tab-sep-

One of the following:
* [Bulk string reply](../../develop/reference/protocol-spec#bulk-strings): The value at the given index.
* [Null reply](../../develop/reference/protocol-spec#nulls): Null reply if key or index does not exist.

{{< /multitabs >}}
