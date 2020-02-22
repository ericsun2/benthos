---
title: jmespath
type: processor
---

<!--
     THIS FILE IS AUTOGENERATED!

     To make changes please edit the contents of:
     lib/processor/jmespath.go
-->


Parses a message as a JSON document and attempts to apply a JMESPath expression
to it, replacing the contents of the part with the result. Please refer to the
[JMESPath website](http://jmespath.org/) for information and tutorials regarding
the syntax of expressions.


import Tabs from '@theme/Tabs';

<Tabs defaultValue="common" values={[
  { label: 'Common', value: 'common', },
  { label: 'Advanced', value: 'advanced', },
]}>

import TabItem from '@theme/TabItem';

<TabItem value="common">

```yaml
# Common config fields, showing default values
jmespath:
  query: ""
```

</TabItem>
<TabItem value="advanced">

```yaml
# All config fields, showing default values
jmespath:
  query: ""
  parts: []
```

</TabItem>
</Tabs>

For example, with the following config:

``` yaml
jmespath:
  query: locations[?state == 'WA'].name | sort(@) | {Cities: join(', ', @)}
```

If the initial contents of a message were:

``` json
{
  "locations": [
    {"name": "Seattle", "state": "WA"},
    {"name": "New York", "state": "NY"},
    {"name": "Bellevue", "state": "WA"},
    {"name": "Olympia", "state": "WA"}
  ]
}
```

Then the resulting contents would be:

``` json
{"Cities": "Bellevue, Olympia, Seattle"}
```

It is possible to create boolean queries with JMESPath, in order to filter
messages with boolean queries please instead use the
[`jmespath`](/docs/components/conditions/jmespath) condition.

## Fields

### `query`

The JMESPath query to apply to messages.


Type: `string`  
Default: `""`  

### `parts`

An optional array of message indexes of a batch that the processor should apply to.
If left empty all messages are processed. This field is only applicable when
batching messages [at the input level](/docs/configuration/batching).

Indexes can be negative, and if so the part will be selected from the end
counting backwards starting from -1.


Type: `array`  
Default: `[]`  

