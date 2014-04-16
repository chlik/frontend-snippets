Otherwise known as Fajax (fake ajax). For example, when submitting a form and the next page is mostly similar to the new page, the entire page isn't whited out and redrawn, it blends smoothly to the next (IE only).
```html
<!--[if IE]>
<meta http-equiv="Page-Enter" content="blendTrans(duration=0)" />
<meta http-equiv="Page-Exit" content="blendTrans(duration=0)" />
<![endif]-->
```
