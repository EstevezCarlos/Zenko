# ⚡Zenko⚡

Pugjs framework to simplify things that SHOULD be simple.

---
## Installation
---

Copy `zenko.pug` file to your project directory and include it to your pug file:
```pug
include zenko
```

---
## Headers
---

---
### HEADER GROUP -> `+hg`




#### `+hg` creates `<hX>`:
```pug
+hg('qwe')
```
```html
<h1>qwe</h1>
```



#### `+hg` is virtual wrapper for elements logically connected to `<hX>`:
```pug
+hg('qwe')
    p asd
    p zxc
```
```html
<h1>qwe</h1>
<p>asd</p>
<p>zxc</p>
```



#### Level of `<hX>` depends on number of parent `+hg`:
```pug
+hg('qwe')
    +hg('zxc')
        +hg('rty')
+hg('fgh')
    +hg('vbn')
        +hg('fgh')
```
```html
<h1>qwe</h1>
<h2>zxc</h2>
<h3>rty</h3>
<h1>fgh</h1>
<h2>vbn</h2>
<h3>fgh</h3>
```



#### Maximum Level of `<hX>` is 6:
```pug
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
+hg('qwe')#asd.zxc
```
```html
<h1 class="zxc" id="asd">qwe</h1>
```




---
## Tables
---

---
### TABLE ROW -> `+tr`


#### `+tr` creates `<td>` for each argument, inside single `<tr>`:
```pug
+tr('qwe','asd')
```
```html
<tr>
    <td>qwe</td>
    <td>asd</td>
</tr>
```


#### `+tr` supports Pug attributes:
```pug
+tr('qwe')#asd.zxc
```
```html
<tr class="zxc" id="asd">
    <td>qwe</td>
</tr>
```


#### `+tr` supports child attributes
```pug
+tr('qwe')
    +_()#asd.zxc
```
```html
<tr>
    <td class="zxc" id="asd">qwe</td>
</tr>
```
#### Tag `th` can be inserted in block of `tr`:
```pug
+tr('asd')
    th.zxc qwe
```
```html
<tr>
    <th class="zxc">qwe</th>
    <td>asd</td>
</tr>
```
#### Keep in mind, `th` does not share child attributes:
```pug
+tr('asd')
    +_.zxc
    th.rty qwe
```
```html
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
+trh('qwe','asd').zxc
    +_.rty
```
```html
<tr class="zxc">
    <th class="rty">qwe</th>
    <th class="rty">asd</th>
</tr>
```
