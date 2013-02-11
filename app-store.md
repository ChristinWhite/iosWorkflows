# App Store

Default Apple App

## URL Scheme

### Search App Store

    itms-apps://
        phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=
            itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=Twitter
    
    http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=

Note: Using the *itms-apps://* protocol will launch your search in the iOS App Store while using *http://* may launch the search in iTunes. One possible downside to using *itms-apps://* is that it will not work on OS X or Windows so for potentially cross-platform tools like Bookmarklets you either need to make it platform specific or build it to use the correct URL depending on the platform like I do in the bookmarklet below. If there's a better way of handling this I'd love to hear it!

[handleOpenURL](http://handleopenurl.com/scheme/app-store)

---

## Launch Center Pro Actions

### Search App Store for \[clipboard\]

    http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=[clipboard]

### Search App Store for \[prompt\]

    http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=[prompt]

---

## Bang On Custom URL Scheme

    itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=%@

---

## Mr. Reader Services

### Other App Service: Search App Store for Selection

    App Name: App Store
    Protocol: itms-apps://
    URL Scheme Template:
        itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=
    
    Visibility:
        Standard Menu: Off
        Text Selection Menu: On
        Link Menu: Off

[Download Service](https://raw.github.com/christopherdwhite/iosWorkflows/master/mrreader-services/app-store.mrreaderappconf)

---

## Drafts Actions

### URL Action: Search App Store for Title

    Name: Search App Store for Title
    URL:
        itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=[[title]]

Note: This action will search the App Store for whatever is on the first line of your draft.

[Install Action](drafts://x-callback-url/import_action?type=URL&name=Search%20App%20Store%20for%20Title&url=itms-apps%3A%2F%2Fphobos.apple.com%2FWebObjects%2FMZSearch.woa%2Fwa%2Fsearch%3Fmedia%3Dsoftware%26term%3D%5B%5Btitle%5D%5D)

---

## Bookmarklets

### Generic (Safari)

#### Search App Store for Selection

```javascript
javascript:if(navigator.userAgent.match(/(iPhone|iPod|iPad)/i)){location.href='itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(window.getSelection());}else{location.href='http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(window.getSelection());}
```

This bookmarklet also works on OS X (& probably Windows, haven't tested it yet).

#### Search App Store for for...? Prompt

```javascript
javascript:var%20search=window.prompt('Search%20App%20Store%20for...');if(navigator.userAgent.match(/(iPhone|iPod|iPad)/i)){location.href='itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(search);}else{location.href='http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(search);}
```