## cache.html
If you do not want to cache the current page, you can use a proxy iframe page references.
```html
<!DOCTYPE HTML>
<<html manifest="/cache.manifest">
	<head></head>
	<body>
		
	</body>
</html>
```

##cache.manifest

```ini
CACHE MANIFEST
# VERSION 2014-04-14 12:23

NETWORK:

CACHE:

FALLBACK:
/ /offline.html

```

## need add mime type `text/cache-manifest` in server

###.htaccess
```htaccess
AddType text/cache-manifest .manifest
```
