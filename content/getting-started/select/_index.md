---
title: Select
weight: 0
toc : true
type: index

---

This tutorial uses examples of the basis usage of `SELECT` statement

## Example 

```js
  let x = select x, y from source()
```

Transpilled

```js
let x = From(source())
        .Select((row, index)=> {
            return {'x': row.x}
        })
```