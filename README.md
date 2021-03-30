a fork of [rxi/json.lua](https://github.com/rxi/json.lua)

## What's added
- Pretty `encode`
- Prioritizing & sorting keys

## Example
```lua
local o = { d = 4, c = 2, first = 1, a = '123', second = 2}
print(json.encode(o, {
  pretty = true,
  keys = {'first', 'second'}
}))
```
```json
{
  "first": 1,
  "second": 2,
  "a": "123",
  "c": 2,
  "d": 4
}
```
```lua
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
            "color": [1,0,0],
            "size": "big"
          }
        },
        {
          "name": "bunny",
          "x": 3,
          "y": 2,
          "opt": {
            "color": [1,1,1],
            "size": "small"
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
