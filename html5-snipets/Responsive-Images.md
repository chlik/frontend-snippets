## via Media Queries
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
## Image Set
### The syntax for image-set() is:
```
image-set() = image-set( [ <image-set-decl>, ]* [ <image-set-decl> | <color>] )
<image-set-decl> = [ <image> | <string> ] <resolution>
```
### Example 1
```css
background-image: image-set( "foo.png" 1x,
                               "foo-2x.png" 2x,
                               "foo-print.png" 600dpi );
```
```css
background-image:url(img1.png);/* common display */
background-image: -webkit-image-set(
    url(img1-100x100.png) 1x,
    url(img1-200x200.png) 2x);/* Retina */
```
                               

## Related
* Optimizing Web Experiences for High Resolution Screens: http://bradfrostweb.com/blog/mobile/hi-res-optimization/ 
* Responsive Images Community Group: http://www.w3.org/community/respimg/ 
* Media Query & Asset Downloading Tests: http://timkadlec.com/2012/02/media-query-asset-downloading-tests/ 
* ResponsiveImages: http://responsiveimages.org/ 
* w3c: http://dev.w3.org/csswg/css-images/ 
