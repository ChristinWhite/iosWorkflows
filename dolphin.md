# Dolphin

[Official Site](http://dolphin-browser.com/) • [iTunes Link](
https://itunes.apple.com/us/app/dolphin-browser-for-ipad/id460812023?mt=8)

## Table of Contents

1. [URL Scheme](#url-scheme)
1. [Launch Center Pro Actions](#launch-center-pro-actions)
    1. [Clipboard Actions](#clipboard-actions)
    1. [Prompt Actions](#prompt-actions)
1. [Drafts Actions](#drafts-actions)
    1. [URL Actions](#url-actions)
1. [Mr. Reader Services](#mr-reader-services)
    1. [Browser Services](#browser-services)
1. [Bookmarklets](#bookmarklets)
    1. [Generic](#generic)
1. [Suggested Improvements for MoboTap](#suggested-improvements-for-mobotap)

## URL Scheme

### Launch & Open URL

    dolphin://
        
    Example:
    	dolphin://dolphin-browser.com

Documentation: [handleOpenURL](http://handleopenurl.com/scheme/dolphin-browser)

Note: I believe the information on the handleOpenURL link is incorrect. Including the *http://* in the URL scheme result in Dolphin trying to load *[http://http://dolphin-browser.com](http://http://dolphin-browser.com)* and Dolphin doesn't seem to like the double protocol. I've pinged the developer to double check it.

[Table of Contents ↩](#table-of-contents)

---

## Launch Center Pro Actions

### Clipboard Actions

#### Open \[clipboard\] URL in Dolphin

    dolphin://[clipboard]

This isn't a great option since you need to make sure the URL in your clipboard doesn't have *http://* or *https://* attached. I'd recommend using the prompt action instead since you can paste into the prompt and then adjust the URL as needed.

### Prompt Actions

#### Open \[prompt\] URL in Dolphin

    dolphin://[prompt]

Don't forget to remove the protocol.

[Table of Contents ↩](#table-of-contents)

---

## Drafts Actions

### URL Actions

#### Open Link (without protocol) in Dolphin

    Name: Open Link (without protocol) in Dolphin
    URL:
        dolphin://[[title]]

*Note: This action will send Dolphin whatever is on the first line of your draft.*

This URL action isn't ideal because you need to strip out the protocol manually since Dolphin doesn't know what to do with a URL that still has the *http://* or https:// protocols included. It gets confused by this kind of URL:

*[dolphin://http://www.google.com](dolphin://http://www.google.com)*

~~[Install Action](drafts://x-callback-url/import_action?type=URL&name=Open%20Link%20%28without%20protocol%29%20in%20Dolphin&url=dolphin%3A%2F%2F%5B%5Btitle%5D%5D) • [Help](guide.md#installing-draft-actions)~~ • Copy & paste this URL into the location bar:

    drafts://x-callback-url/import_action?type=URL&name=Open%20Link%20%28without%20protocol%29%20in%20Dolphin&url=dolphin%3A%2F%2F%5B%5Btitle%5D%5D

[Table of Contents ↩](#table-of-contents)

---

## Mr. Reader Services

### Browser Services

#### Dolphin Browser (Official)

    App Name: Dolphin Browser
    Protocol: dolphin:
    HTTP URL Scheme:

        dolphin://[URL-WITHOUT-PROTOCOL]

    HTTPS URL Scheme:

        dolphin://[URL-WITHOUT-PROTOCOL]

Note: This service is built into Mr. Reader. I've included it here for completeness and as an example.

[Download Service](https://github.com/christopherdwhite/iosWorkflows/raw/master/mrreader-services/dolphin-browser.mrreaderbrowserconf) • [Help](guide.md#installing-mr-reader-browser-and-other-app-services)

[Table of Contents ↩](#table-of-contents)

---

## Bookmarklets

Important Note: Bookmarklets that take advantage of your text selection work differently or don't work at all in different browsers. Please see the guide for [further details and workarounds](guide.md#bookmarklet-limitations-for-selected-text-in-different-browsers).

### Generic

#### Open in Dolphin

```javascript
javascript:if(location.href.substring(4,5)=='s'){location.href='dolphin://'+location.href.substring(5);}else{location.href='dolphin://'+location.href.substring(4);}
```

Expanded:

```javascript
javascript:

if (location.href.substring(4,5) == 's') {
    location.href='dolphin://' + location.href.substring(5);
} else {
    location.href = 'dolphin://' + location.href.substring(4);
}
```

*Caution*: This will open an https:// link in Dolphin but it will strip away the 's.' Unlike Mercury or Chrome [there isn't a way](http://twitter.com/DolphinCares/status/296874545028161536) to pass along an https link intact.

[Table of Contents ↩](#table-of-contents)

---

## Suggested Improvements for MoboTap

1. It would be great to have the URL scheme properly documented somewhere. If it is and I couldn't find it please let me know.
1. Adding a search option to the URL scheme would be quite handy. Being able to easily enter a search term in Launch Center Pro and having Dolphin open with that search would be awesome. Bonus points for letting the scheme specify which search engine.
1. Adding support for [x-callback-url](http://x-callback-url.com/) functionality would be great. [Chrome's implementation]((https://developers.google.com/chrome/mobile/docs/ios-links) of this is awesome.
1. Dolphin really should be able to receive https:// links through the URL scheme, it isn't critical at most times but it's an easy thing that keeps everyone safer. 
    
    It would also be nice to have [dolphin://http:www.google.com](dolphin://http:www.google.com), [dolphin://https://www.google.com](dolphin://https://www.google.com) or even [dolphin://https://www.google.com](dolphin://https://www.google.com) work so that 'Open URL in Dolphin' actions could be added to apps like Launch Center Pro and Drafts that don't offer JavaScript (like a browser) or more advanced URL configurability (like Mr. Reader) to automatically strip away the *http://* protocol and replace it with *dolphin://.* [Mercury Browser](http://mercury-browser.com/) is a good example of this working.

[Table of Contents ↩](#table-of-contents)