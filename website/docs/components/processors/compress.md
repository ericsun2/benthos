---
title: compress
type: processor
---

<!--
     THIS FILE IS AUTOGENERATED!

     To make changes please edit the contents of:
     lib/processor/compress.go
-->


Compresses messages according to the selected algorithm. Supported compression
algorithms are: gzip, zlib, flate.


import Tabs from '@theme/Tabs';

<Tabs defaultValue="common" values={[
  { label: 'Common', value: 'common', },
  { label: 'Advanced', value: 'advanced', },
]}>

import TabItem from '@theme/TabItem';

<TabItem value="common">

```yaml
# Common config fields, showing default values
compress:
  algorithm: gzip
  level: -1
```

</TabItem>
<TabItem value="advanced">

```yaml
# All config fields, showing default values
compress:
  algorithm: gzip
  level: -1
  parts: []
```

</TabItem>
</Tabs>

The 'level' field might not apply to all algorithms.

## Fields

### `algorithm`

The compression algorithm to use.


Type: `string`  
Default: `"gzip"`  
Options: `gzip`, `zlib`, `flate`.

### `level`

The level of compression to use. May not be applicable to all algorithms.


Type: `number`  
Default: `-1`  

### `parts`

An optional array of message indexes of a batch that the processor should apply to.
If left empty all messages are processed. This field is only applicable when
batching messages [at the input level](/docs/configuration/batching).

Indexes can be negative, and if so the part will be selected from the end
counting backwards starting from -1.


Type: `array`  
Default: `[]`  

