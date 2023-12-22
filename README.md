# ⚡Zenko⚡

Pugjs framework to simplify things that SHOULD be simple.

---
## Installation
---

### Copy `zenko.pug` file to your project directory and extend you base temlate with it:
```pug
extends zenko
block html
    doctype html
    .
    .
    .
```
### Or include it just in chosen pug file:
```pug
include zenko
```


---
## Headers
---

---
### HEADER GROUP -> `+hg`


#### `+hg` creates `<h#>`:
```pug
<!-- code -->
+hg('qwe')
```
```html
<!-- output -->
<h1>qwe</h1>
```

#### `+hg` is virtual wrapper for elements logically connected to `<h#>`:
```pug
<!-- code -->
+hg('qwe')
    p asd
    p zxc
```
```html
<!-- output -->
<h1>qwe</h1>
<p>asd</p>
<p>zxc</p>
```

#### Level of `<h#>` depends on number of parent `+hg`:
```pug
<!-- code -->
+hg('qwe')
    +hg('zxc')
        +hg('rty')
+hg('fgh')
    +hg('vbn')
        +hg('fgh')
```
```html
<!-- output -->
<h1>qwe</h1>
<h2>zxc</h2>
<h3>rty</h3>
<h1>fgh</h1>
<h2>vbn</h2>
<h3>fgh</h3>
```

#### So you no longer have to worry about level of `<h#>` in your imports/extends:
```pug
<!-- file1 code -->
+hg('qwe')
    block asd
```
```pug
<!-- code -->
extends file1
block asd
    +hg('zxc')
```
```html
<!-- output -->
<h1>qwe</h1>
<h2>zxc</h2>
```

#### Maximum Level of `<h#>` is 6:
```pug
<!-- code -->
+hg('qwe')
    +hg('zxc')
        +hg('rty')
            +hg('fgh')
                +hg('vbn')
                    +hg('fgh')
                        +hg('uio')
                    +hg('jkl')
```
```html
<!-- output -->
<h1>qwe</h1>
<h2>zxc</h2>
<h3>rty</h3>
<h4>fgh</h4>
<h5>vbn</h5>
<h6>fgh</h6>
<h6>uio</h6>
<h6>jkl</h6>
```

#### `+hg` supports Pug attributes:
```pug
<!-- code -->
+hg('qwe')#asd.zxc
```
```html
<!-- output -->
<h1 class="zxc" id="asd">qwe</h1>
```




---
## Tables
---

---
### TABLE ROW -> `+tr`


#### `+tr` creates `<td>` for each argument, inside single `<tr>`:
```pug
<!-- code -->
+tr('qwe','asd')
```
```html
<!-- output -->
<tr>
    <td>qwe</td>
    <td>asd</td>
</tr>
```


#### `+tr` supports Pug attributes:
```pug
<!-- code -->
+tr('qwe')#asd.zxc
```
```html
<!-- output -->
<tr class="zxc" id="asd">
    <td>qwe</td>
</tr>
```


#### `+tr` supports child attributes
```pug
<!-- code -->
+tr('qwe')
    +_()#asd.zxc
```
```html
<!-- output -->
<tr>
    <td class="zxc" id="asd">qwe</td>
</tr>
```
#### Tag `th` can be inserted in block of `tr`:
```pug
<!-- code -->
+tr('asd')
    th.zxc qwe
```
```html
<!-- output -->
<tr>
    <th class="zxc">qwe</th>
    <td>asd</td>
</tr>
```
#### Keep in mind, `th` does not share child attributes:
```pug
<!-- code -->
+tr('asd')
    +_.zxc
    th.rty qwe
```
```html
<!-- output -->
<tr>
    <th class="rty">qwe</th>
    <td class="zxc">asd</td>
</tr>
```
---
---
### TABLE ROW WITH HEADERS -> `+trh`
---
#### `+trh` is identical to `+tr`, except each child cell is `<th>`:
```pug
<!-- code -->
+trh('qwe','asd').zxc
    +_.rty
```
```html
<!-- code -->
<tr class="zxc">
    <th class="rty">qwe</th>
    <th class="rty">asd</th>
</tr>
```
