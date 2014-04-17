

## via media queries
```css
.img1 {
    background-image:url(img1-100x100.png);/* common display */
}

/* ------------- Retina ------------- */
@media only screen and (-o-min-device-pixel-ratio: 2/1), /* Opera */
       only screen and (min--moz-device-pixel-ratio: 2), /* < Firefox 16 */
       only screen and (-webkit-min-device-pixel-ratio: 2), /* Webkit */
       only screen and (min-resolution: 240dpi), /* standard */
       only screen and (min-resolution: 2dppx) /* standard */
{
  .img1 {
      background-image:url(img1-200x200.png);
  }
}
```
