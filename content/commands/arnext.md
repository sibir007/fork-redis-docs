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
description: Returns the next index ARINSERT would use.
function: arnextCommand
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
linkTitle: ARNEXT
railroad_diagram: /images/railroad/arnext.svg
reply_schema:
  oneOf:
  - description: The next index ARINSERT would use. Returns 0 for missing keys or
      when no insert happened yet.
    type: integer
  - description: Null when the insertion cursor is exhausted (next insert would overflow).
    type: 'null'
since: 8.8.0
summary: Returns the next index ARINSERT would use.
syntax_fmt: ARNEXT key
title: ARNEXT
---
Returns the next index ARINSERT would use.

## Required arguments

<details open><summary><code>key</code></summary>

The name of the key that holds the array.

</details>

## Examples

{{% redis-cli %}}
ARINSERT myarray "a"
ARINSERT myarray "b"
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

One of the following:
* [Integer reply](../../develop/reference/protocol-spec#integers): The next index ARINSERT would use. Returns 0 for missing keys or when no insert happened yet.
* [Nil reply](../../develop/reference/protocol-spec#null-bulk-strings): Null when the insertion cursor is exhausted (next insert would overflow).

-tab-sep-

One of the following:
* [Integer reply](../../develop/reference/protocol-spec#integers): The next index ARINSERT would use. Returns 0 for missing keys or when no insert happened yet.
* [Null reply](../../develop/reference/protocol-spec#nulls): Null when the insertion cursor is exhausted (next insert would overflow).

{{< /multitabs >}}
