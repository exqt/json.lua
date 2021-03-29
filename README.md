a fork of [rxi/json.lua](https://github.com/rxi/json.lua)

## What's added
- Pretty `encode`
- Prioritizing keys

## Example
```lua
local json = require 'json'
local level = {
  name = "test level",
  layers = {
    {
      type = "tile",
      width = 5,
      height = 3,
      data = {
        {1, 1, 1, 2, 3},
        {4, 1, 2, 3, 4},
        {3, 4, 5, 1, 3}
      }
    },
    {
      type = "objects",
      data = {
        {
          name = "slime",
          x = 1,
          y = 2,
          opt = {
            color = {1, 0, 0},
            size = 'big'
          }
        },
        {
          name = "bunny",
          x = 3,
          y = 2,
          opt = {
            color = {1, 1, 1},
            size = 'small'
          }
        },
      }
    }
  }
}

local keys = {"type", "name", "x", "y", "width", "height", "layers", "opt", "data"}
print(json.encode(level, {
  pretty = true,
  indent = "  ",
  keys = keys,
}))
```
```json
{
  "name": "test level",
  "layers": [
    {
      "type": "tile",
      "width": 5,
      "height": 3,
      "data": [
        [1,1,1,2,3],
        [4,1,2,3,4],
        [3,4,5,1,3]
      ]
    },
    {
      "type": "objects",
      "data": [
        {
          "name": "slime",
          "x": 1,
          "y": 2,
          "opt": {
            "size": "big",
            "color": [1,0,0]
          }
        },
        {
          "name": "bunny",
          "x": 3,
          "y": 2,
          "opt": {
            "size": "small",
            "color": [1,1,1]
          }
        }
      ]
    }
  ]
}
```

## License
This library is free software; you can redistribute it and/or modify it under
the terms of the MIT license. See [LICENSE](LICENSE) for details.
