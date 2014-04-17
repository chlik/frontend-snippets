CSS2 allows you to specify stylesheet for specific media type such as screen or print. Now CSS3 makes it even more efficient by adding media queries. You can add expressions to media type to check for certain conditions and apply different stylesheets. For example, you can have one stylesheet for large displays and a different stylesheet specifically for mobile devices. It is quite powerful because it allows you to tailor to different resolutions and devices without changing the content. Continue on this post to read the tutorial and see some websites that make good use of media queries.

## CSS3 Media Queries

###Media features
width, height, device-width, device-height, orientation, aspect-ratio, device-aspect-ratio, color, color-index, monochrome, , resolution, scan, grid. see http://www.w3.org/TR/css3-mediaqueries/
###Max Width
The following CSS will apply if the viewing area is smaller than 600px.
```css
@media screen and (max-width: 600px) {
  .class {
    background: #ccc;
  }
}
```
If you want to link to a separate stylesheet, put the following line of code in between the <head> tag.
```html
<link rel="stylesheet" media="screen and (max-width: 600px)" href="small.css" />
```
### Min Width
The following CSS will apply if the viewing area is greater than 900px.
```css
@media screen and (min-width: 900px) {
  .class {
    background: #666;
  }
}
```
### Multiple Media Queries
You can combine multiple media queries. The following code will apply if the viewing area is between 600px and 900px.
```css
@media screen and (min-width: 600px) and (max-width: 900px) {
  .class {
    background: #333;
  }
}
```
### Device Width
The following code will apply if the max-device-width is 480px (eg. iPhone display). Note: max-device-width means the actual resolution of the device and max-width means the viewing area resolution.
```css
@media screen and (max-device-width: 480px) {
  .class {
    background: #000;
  }
}
```
### For iPhone 4
The following stylesheet is specifically for iPhone 4.
```html
<link rel="stylesheet" media="only screen and (-webkit-min-device-pixel-ratio: 2)" type="text/css" href="iphone4.css" />
```
### For iPad
You can also use media query to detect orientation (portrait or landscapse) on the iPad.
```html
<link rel="stylesheet" media="all and (orientation:portrait)" href="portrait.css"> 
<link rel="stylesheet" media="all and (orientation:landscape)" href="landscape.css">
```
### Media Queries for Internet Explorer
Unfortunately, media query is not supported in Internet Explorer 8 or older. You can use Javascript to hack around. Below are some solutions:

```html
<link rel="stylesheet" type="text/css" href="main.css" />
<link id="size-stylesheet" rel="stylesheet" type="text/css" href="narrow.css" />
```
```js
function adjustStyle(width) {
    width = parseInt(width);
    if (width < 701) {
        $("#size-stylesheet").attr("href", "css/narrow.css");
    } else if ((width >= 701) && (width < 900)) {
        $("#size-stylesheet").attr("href", "css/medium.css");
    } else {
       $("#size-stylesheet").attr("href", "css/wide.css"); 
    }
}

$(function() {
    adjustStyle($(this).width());
    $(window).resize(function() {
        adjustStyle($(this).width());
    });
});
```

## Referers
* http://webdesignerwall.com/tutorials/css3-media-queries
* http://www.w3.org/TR/CSS2/media.html
* http://www.w3.org/TR/css3-mediaqueries/
