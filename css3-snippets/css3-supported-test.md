
```js
/**
 * 判断浏览器是否支持某一个CSS3属性
 * @param  {String} 属性名称
 * @return {Boolean} true/false
 * @version 1.0
 * @author ydr.me
 * 2014年4月4日14:47:19
 */
 
function supportCss3(style) {
	var prefix = ['webkit', 'Moz', 'ms', 'o'],
		i,
		humpString = [],
		htmlStyle = document.documentElement.style,
		_toHumb = function (string) {
			return string.replace(/-(\w)/g, function ($0, $1) {
				return $1.toUpperCase();
			});
		};
 
	for (i in prefix)
		humpString.push(_toHumb(prefix[i] + '-' + style));
 
	humpString.push(_toHumb(style));
 
	for (i in humpString)
		if (humpString[i] in htmlStyle) return true;
 
	return false;
}

alert(supportCss3('animation-play-state'));

```

* IE: http://msdn.microsoft.com/en-us/library/ms533055(v=VS.85).aspx
* Firefox: https://developer.mozilla.org/en/DOM:CSS
* Opera: http://www.opera.com/docs/specs/opera8/js/dom/css/ 
