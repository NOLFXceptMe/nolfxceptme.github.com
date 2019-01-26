---
permalink: /notes/jq
title: jq
layout: note
---
### Remove keys present in another file
<br>

```shell
$ cat excluded.keys
"green"
"blue"

$ cat color-map.json
{
  "map": [
    {
      "color": "red",
      "value": "#f00"
    },
    {
      "color": "green",
      "value": "#0f0"
    },
    {
      "color": "blue",
      "value": "#00f"
    },
    {
      "color": "cyan",
      "value": "#0ff"
    }
  ]
}

$ jq --slurpfile excluded excluded.keys '{ "map" : [.map[] | select([.color] | inside($excluded) | not)]}' color-map.json
{
  "map": [
    {
      "color": "red",
      "value": "#f00"
    },
    {
      "color": "cyan",
      "value": "#0ff"
    }
  ]
}
```
