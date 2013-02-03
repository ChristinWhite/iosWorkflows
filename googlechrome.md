# Google Chrome

## URL Scheme

http:

    googlechrome://
    googlechrome://www.google.com
    googlechrome://http://www.google.com

https:
 
    googlechromes://
    googlechromes://www.google.com

x-callback-url:
  
    googlechrome-x-callback://
    googlechrome-x-callback://x-callback-url/open/?url=http%3A%2F%2Fwww.google.com
    googlechrome-x-callback://x-callback-url/open/?x-source=MyApp&x-success=com.myapp.callback%3A%2F%2F&url=http%3A%2F%2Fwww.google.com
    googlechrome-x-callback://x-callback-url/open/?x-source=MyApp&x-success=com.myapp.callback%3A%2F%2F&url=http%3A%2F%2Fwww.google.com&create-new-tab

[Opening links in Chrome for iOS](https://developers.google.com/chrome/mobile/docs/ios-links)

## Bookmarklets

### Open in Chrome (by [Jon Abrams](http://blog.jonabrams.com/post/26099585134/open-in-chrome))

```javascript
javascript:location.href="googlechrome"+location.href.substring(4);
```

### Open in Chrome & Return to Dolphin

```javascript
javascript:if(location.href.substring(4,5)=='s'){var%20link=location.href.substring(5);}else{link=location.href.substring(4);}location.href='googlechrome-x-callback://x-callback-url/open/?url='+encodeURIComponent(location.href)+'&x-source=Dolphin&x-success=dolphin://';
```

### Open in Chrome & Return to Mercury

```javascript
javascript:location.href='googlechrome-x-callback://x-callback-url/open/?url='+encodeURIComponent(location.href)+'&x-source=Mercury&x-success=merc://'+encodeURIComponent(location.href)
```

Note: x-callback Bookmarklets are based on [Google Chrome URL Schemes documentation](https://developers.google.com/chrome/mobile/docs/ios-links), Federico Viticci´s [Chrome to Safari bookmarklet](http://www.macstories.net/tutorials/chrome-for-ios-send-a-webpage-back-to-safari-via-bookmarklet/) & the respective browser bookmarklets included in my other workflows.