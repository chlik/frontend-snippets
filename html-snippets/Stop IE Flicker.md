##Client-side fix:
Tools  >  Internet Options  
>  'Settings' under Temporary Internet files  
>  Select 'Automatically'  >  OK

##CSS FIX - Insert in your CSS:
```css
html {
  filter: expression(document.execCommand("BackgroundImageCache", false, true));
}
```

##Javascript FIX:
```js
try {
document.execCommand('BackgroundImageCache', false, true);
}
catch(e) {};
```
