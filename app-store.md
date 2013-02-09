# App Store

Default Apple App

## URL Scheme

### Function

    itms-apps://
        phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=
            itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=Twitter
    
    http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=

[handleOpenURL](http://handleopenurl.com/scheme/app-store)

### Help!

I'm still trying to figure out the best way to handle app store links and would appreciate suggestions.

Launch Center Pro's preset uses this URL:

    http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=

When you use it to search for an App it always opens the App Store.

However, giving Bang On or a bookmarklet the same URL will cause the iTunes store to launch with the specified search some (or all) of the time. Bang On's developer [suggested](https://twitter.com/kepner/status/297177480417140737) the itms-app:// protocol instead:

    itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=

This works fine for Bang On but it does have a disadvantage for bookmarklets because using the http:// URL in a bookmarklet on a Mac will launch iTunes with the search term but using itms-app:// instead won't. If you use the same bookmarks on both platforms either solution will (consistently) work on one platform or the other.

I plan on doing more research on a better solution but wouldn't mind a shortcut!

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

[Download Service](https://raw.github.com/christopherdwhite/iosWorkflows/master/mrreader-services/app-store.mrreaderbrowserconf)

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
javascript:location.href='itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(window.getSelection());
```

This bookmarklet doesn't play work on desktop browsers. You can use the following bookmarklet instead but it may open iTunes instead of the App Store on iOS devices, see the help note above for further information.

```javascript
javascript:location.href='http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(window.getSelection());
```

#### Search App Store for for...? Prompt

```javascript
javascript:var%20search=window.prompt('Search%20App%20Store%20for...');location.href='itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(search);
```

This bookmarklet doesn't play work on desktop browsers. You can use the following bookmarklet instead but it may open iTunes instead of the App Store on iOS devices, see the help note above for further information.

```javascript
javascript:var%20search=window.prompt('Search%20App%20Store%20for...');location.href='http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(search);
```