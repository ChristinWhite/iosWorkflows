# App Store

*The* default Apple app.

## Table of Contents

1. [URL Scheme](#url-scheme)
1. [Launch Center Pro Actions](#launch-center-pro-actions)
    1. [Clipboard Actions](#clipboard-actions)
    1. [Prompt Actions](#prompt-actions)
1. [Bang On Custom Search URL](#bang-on-custom-search-url)
1. [Drafts Actions](#drafts-actions)
    1. [URL Actions](#url-actions)
1. [Mr. Reader Services](#mr-reader-services)
    1. [Other App Services](#other-app-services)
1. [Bookmarklets](#bookmarklets)
    1. [Generic](#generic)

---

## URL Scheme

### Search App Store

#### iOS App Store

    itms-apps://
        phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=
            
    Example:
        itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=Twitter
 
#### iTunes

    http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=

    Example
        http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=Twitter


Note: Using the *itms-apps://* protocol will launch your search in the iOS App Store while using *http://* may launch the search in iTunes. One possible downside to using *itms-apps://* is that it will not work on OS X or Windows so for potentially cross-platform tools like Bookmarklets you either need to make it platform specific or build it to use the correct URL depending on the platform like I do in the bookmarklet below. 

If there's a better way of handling this or if you can fill in any more information about the App Store URL schemes I'd really appreciate [the help](README.md#project-updates--contact-information)!

[handleOpenURL](http://handleopenurl.com/scheme/app-store)

[Table of Contents ↩](#table-of-contents)

---

## Launch Center Pro Actions

### Clipboard Actions

#### Search App Store for \[clipboard\]

    http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=[clipboard]

### Prompt Actions

#### Search App Store for \[prompt\]

    http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=[prompt]

[Table of Contents ↩](#table-of-contents)

---

## Bang On Custom Search URL

    itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=%@

[Table of Contents ↩](#table-of-contents)

---

## Drafts Actions

### URL Actions

#### Search App Store for Title

    Name: Search App Store for Title
    URL:

        itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term=[[title]]

Note: This action will search the App Store for whatever is on the first line of your draft.

~~[Install Action](drafts://x-callback-url/import_action?type=URL&name=Search%20App%20Store%20for%20Title&url=itms-apps%3A%2F%2Fphobos.apple.com%2FWebObjects%2FMZSearch.woa%2Fwa%2Fsearch%3Fmedia%3Dsoftware%26term%3D%5B%5Btitle%5D%5D) • [Help](guide.md#installing-drafts-actions)~~ • Copy & paste this URL into the location bar:

    drafts://x-callback-url/import_action?type=URL&name=Search%20App%20Store%20for%20Title&url=itms-apps%3A%2F%2Fphobos.apple.com%2FWebObjects%2FMZSearch.woa%2Fwa%2Fsearch%3Fmedia%3Dsoftware%26term%3D%5B%5Btitle%5D%5D

[Table of Contents ↩](#table-of-contents)

---

## Mr. Reader Services

### Other App Services

#### Search App Store for Selection

    App Name: Search App Store for Selection
    Protocol: itms-apps://
    URL Scheme Template:

        itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term={[TEXT-SELECTED]}
    
    Visibility:
        Standard Menu: Off
        Text Selection Menu: On
        Link Menu: Off

[Download Service](https://github.com/christopherdwhite/iosWorkflows/raw/master/mrreader-services/search-app-store-for-selection.mrreaderappconf) • [Help](guide.md#installing-mr-reader-browser-and-other-app-services)

[Table of Contents ↩](#table-of-contents)

---

## Bookmarklets

Important Note: Bookmarklets that take advantage of your text selection work differently or don't work at all in different browsers. Please see the guide for [further details and workarounds](guide.md#bookmarklet-limitations-for-selected-text-in-different-browsers).

### Generic

#### Search App Store for Selection

```javascript
javascript:if(navigator.userAgent.match(/(iPhone|iPod|iPad)/i)){location.href='itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(window.getSelection());}else{location.href='http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(window.getSelection());}
```

This bookmarklet also works correctly on OS X (& probably Windows, haven't tested it yet).

#### Search App Store for...? Prompt

```javascript
javascript:var%20search=window.prompt('Search%20App%20Store%20for...');if(navigator.userAgent.match(/(iPhone|iPod|iPad)/i)){location.href='itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(search);}else{location.href='http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(search);}
```

[Table of Contents ↩](#table-of-contents)