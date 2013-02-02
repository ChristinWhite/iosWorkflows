# App Store

## Bookmarklet: Search App Store for Selection

```javascript
javascript:location.href='itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(window.getSelection());
```

Note: This bookmarklet doesn't play work on desktop browsers. You can use this instead but it may open iTunes instead of the App Store on iOS devices:

```javascript
javascript:location.href='http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(window.getSelection());
```

## Launch Center Pro: Search App Store for \[prompt\]

    http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=[prompt]

## Bang On Custom URL String

    itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=%@