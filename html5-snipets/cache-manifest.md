```html
<!DOCTYPE HTML>
<<html manifest="/cache.manifest">
	<head></head>
	<body>
		
	</body>
</html>
```

.htaccess
```htaccess
AddType text/cache-manifest .manifest
```

cache.manifest
```ini
CACHE MANIFEST
# VERSION 2014-04-14 12:23

NETWORK:

CACHE:

FALLBACK:
/ /offline.html

```
