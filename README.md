# ⚡Zenko⚡

Pugjs framework to simplify things that SHOULD be simple.

## Tables


---
### TABLE ROW -> `+tr`


#### `+tr` creates `<td>` for each argument inside single `<tr>`:
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
```pugj
+tr('qwe')#asd.zxc
```
```html
<tr class="zxc" id="asd">
    <td>qwe</td>
</tr>
```
---

<!-- ### +tr

Makes `tr` with multiple `td`

<table>
<tr>
<th></th>
<th>Code</th>
<th>Yields</th>
</tr>
<tr>
<td>Creates <code>td</code> for each argument</td>
<td>

```
+tr('qwe','asd')
```

</td>
<td>

```html
<tr>
    <td>qwe</td>
    <td>asd</td>
</tr>
```

</td>
</tr>
<tr>

<td>Supports attributes</td>
<td>

```pugjs
+tr('qwe')#asd.zxc
```

</td>
<td>

```html
<tr class="zxc" id="asd">
    <td>qwe</td>
</tr>
```

</td>


</tr>
</tr>
<tr>

<td>Supports child attributes</td>
<td>

```pugjs
+tr('qwe')
    +_()#asd.zxc
```

</td>
<td>

```html
<tr>
    <td class="zxc" id="asd">qwe</td>
</tr>
```

</td>


</tr>


<td>Tag <code>th</code> can be inserted in block</td>
<td>

```pugjs
+tr('asd')
    th.zxc qwe
```

</td>
<td>

```html
<tr>
    <th class="zxc">qwe</th>
    <td>asd</td>
</tr>
```

</td>


</tr>


<td>Keep in mind that <code>th</code> does not share child attributes</td>
<td>

```pugjs
+tr('asd')
    +_.zxc
    th.rty qwe
```

</td>
<td>

```html
<tr>
    <th class="rty">qwe</th>
    <td class="zxc">asd</td>
</tr>
```

</td>


</tr>




</table>

## +trh
-->
