---
acl_categories:
- '@write'
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
- write
- fast
complexity: O(1)
description: Sets the ARINSERT / ARRING cursor to a specific index.
function: arseekCommand
group: array
hidden: false
key_specs:
- RW: true
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
  update: true
linkTitle: ARSEEK
railroad_diagram: /images/railroad/arseek.svg
reply_schema:
  description: 1 if the cursor was set, 0 if the key does not exist.
  type: integer
since: 8.8.0
summary: Sets the ARINSERT / ARRING cursor to a specific index.
syntax_fmt: ARSEEK key index
title: ARSEEK
---
Sets the ARINSERT / ARRING cursor to a specific index.

## Required arguments

<details open><summary><code>key</code></summary>

The name of the key that holds the array.

</details>

<details open><summary><code>index</code></summary>

The zero-based integer index to set as the new insert cursor position for subsequent [`ARINSERT`]({{< relref "/commands/arinsert" >}}) calls.

</details>

## Examples

{{% redis-cli %}}
ARINSERT myarray "a"
ARINSERT myarray "b"
ARNEXT myarray
ARSEEK myarray 10
ARINSERT myarray "c"
ARNEXT myarray
{{% /redis-cli %}}

## Redis Software and Redis Cloud compatibility

| Redis<br />Software | Redis<br />Cloud | <span style="min-width: 9em; display: table-cell">Notes</span> |
|:----------------------|:-----------------|:------|
| <span title="Not supported">&#x274c; Standard</span><br /><span title="Not supported"><nobr>&#x274c; Active-Active</nobr></span> | <span title="Not supported">&#x274c; Standard</span><br /><span title="Not supported"><nobr>&#x274c; Active-Active</nobr></span> |  |

## Return information

{{< multitabs id="return-info"
    tab1="RESP2"
    tab2="RESP3" >}}

[Integer reply](../../develop/reference/protocol-spec#integers): 1 if the cursor was set, 0 if the key does not exist.

-tab-sep-

[Integer reply](../../develop/reference/protocol-spec#integers): 1 if the cursor was set, 0 if the key does not exist.

{{< /multitabs >}}
