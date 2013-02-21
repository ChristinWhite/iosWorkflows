# Google Chrome

[Official Site](http://www.google.com/intl/en/chrome/browser/mobile/ios.html) • [iTunes Link](http://itunes.apple.com/us/app/chrome/id535886823?ls=1&mt=8)

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
    1. [Dolphin](#dolphin)
    1. [iCab Mobile](#icab-mobile)
    1. [Mercury](#mercury)
1. [Suggested Improvements for Developer](#suggested-improvements-for-developer)

---

## URL Scheme

### HTTP

    googlechrome://
        URL Without Protocol
        
    Example:
    	googlechrome://www.google.com

### HTTPS

    googlechromes://
        URL Without Protocol
        
    Example:
    	googlechromes://www.google.com



## x-callback-url:
  
    googlechrome-x-callback://
        x-callback-url/
            open/?
                url=
                &x-source=
                &x-success=
                &create-new-tab
    
    Example:
        googlechrome-x-callback://x-callback-url/open/?x-source=Dolphin&x-success=dolphin://&url=http://www.google.com&create-new-tab

Documentation: [Official: Opening links in Chrome for iOS](https://developers.google.com/chrome/mobile/docs/ios-links) • [handleOpenURL](http://handleopenurl.com/scheme/google-chrome) • [akosma wiki](http://wiki.akosma.com/IPhone_URL_Schemes#Google_Chrome)

[Table of Contents ↩](#table-of-contents)

---

## Launch Center Pro Actions

### Clipboard Actions

#### Open \[clipboard\] in Chrome

    googlechrome-x-callback://x-callback-url/open/?url=[clipboard]

You must have a valid URL in the clipboard.

### Prompt Actions

#### Open \[prompt\] in Chrome (with protocol)

    googlechrome-x-callback://x-callback-url/open/?url=[prompt]

You must include *http://* or *https://* in the URL. *http://www.google.com*

#### Open \[prompt\] in Chrome (without protocol)

    googlechrome://[prompt]

You must not include *http://* or *https://* in the URL. *www.google.com*

[Table of Contents ↩](#table-of-contents)

---

## Drafts Actions

### URL Actions

#### Open Link (with protocol) in Chrome

    Name: Open Link in Chrome
    URL:
        googlechrome-x-callback://x-callback-url/open/?url=[[title]]

This action will send Drafts whatever is on the first line of your draft.

You must include *http://* or *https://* in the URL. *http://www.google.com*

[Install Action](drafts://x-callback-url/import_action?type=URL&name=Open%20Link%20in%20Chrome&url=googlechrome-x-callback%3A%2F%2Fx-callback-url%2Fopen%2F%3Furl%3D%5B%5Btitle%5D%5D) • [Help](guide.md#installing-draft-actions)

#### Open Link (without protocol) in Chrome

    Name: Open Link (without protocol) in Chrome
    URL:
        googlechrome://[[title]]

This action will send Drafts whatever is on the first line of your draft.

You must not include *http://* or *https://* in the URL. *www.google.com*

[Install Action](drafts://x-callback-url/import_action?type=URL&name=Open%20Link%20%28without%20protocol%29%20in%20Chrome&url=googlechrome%3A%2F%2F%5B%5Btitle%5D%5D) • [Help](guide.md#installing-draft-actions)

#### Open Link (with protocol) in Chrome & Return to Drafts

    Name: Open Link in Chrome & Return to Drafts
    URL:
        googlechrome-x-callback://x-callback-url/open/?url=[[title]]&x-source=Drafts&x-success=drafts://

This action will send Chrome whatever is on the first line of your draft. When you're finished in Chrome you can use the Drafts button to return to Drafts.

You must include *http://* or *https://* in the URL. *http://www.google.com*

[Install Action](drafts://x-callback-url/import_action?type=URL&name=Open%20Link%20in%20Chrome%20%26%20Return%20to%20Drafts&url=googlechrome-x-callback%3A%2F%2Fx-callback-url%2Fopen%2F%3Furl%3D%5B%5Btitle%5D%5D%26x-source%3DDrafts%26x-success%3Ddrafts%3A%2F%2F) • [Help](guide.md#installing-draft-actions)

[Table of Contents ↩](#table-of-contents)

---

## Mr. Reader Services

### Browser Services

#### Google Chrome (Official)

    App Name: Google Chrome
    Protocol: googlechrome:
    HTTP URL Scheme:
        googlechrome://[URL-WITHOUT-PROTOCOL]
    HTTPS URL Scheme:
        googlechromes://[URL-WITHOUT-PROTOCOL]

Note: This service is built into Mr. Reader. I've included it here for completeness and as an example.

[Download Service](https://github.com/christopherdwhite/iosWorkflows/raw/master/mrreader-services/google-chrome.mrreaderbrowserconf) • [Help](guide.md#installing-mr-reader-browser-and-other-app-services)

#### Open in Google Chrome & Return to Mr. Reader

    App Name: Open in Google Chrome & Return to Mr. Reader
    Protocol: googlechrome:
    HTTP URL Scheme:
        googlechrome-x-callback://x-callback-url/open/?url=[URL]&x-source=Mr.%20Reader&x-success=mrreader://
    HTTPS URL Scheme:
        googlechrome-x-callback://x-callback-url/open/?url=[URL]&x-source=Mr.%20Reader&x-success=mrreader://

[Download Service](https://github.com/christopherdwhite/iosWorkflows/raw/master/mrreader-services/open-in-google-chrome-and-return-to-mr-reader.mrreaderbrowserconf) • [Help](guide.md#installing-mr-reader-browser-and-other-app-services)

[Table of Contents ↩](#table-of-contents)

---

## Bookmarklets

Important Note: Bookmarklets that take advantage of your text selection work differently or don't work at all in different browsers. Please see the guide for [further details and workarounds](guide.md#bookmarklet-limitations-for-selected-text-in-different-browsers).

It's also worth noting that the x-callback-url Bookmarklets are based on [Google Chrome URL Schemes documentation](https://developers.google.com/chrome/mobile/docs/ios-links), Federico Viticci´s [Chrome to Safari bookmarklet](http://www.macstories.net/tutorials/chrome-for-ios-send-a-webpage-back-to-safari-via-bookmarklet/) & the respective browser bookmarklets included in my other workflows.

### Generic

#### Open in Google Chrome (by [Jon Abrams](http://blog.jonabrams.com/post/26099585134/open-in-chrome))

```javascript
javascript:location.href="googlechrome"+location.href.substring(4);
```

### Dolphin

#### Open in Google Chrome & Return to Dolphin

```javascript
javascript:if(location.href.substring(4,5)=='s'){var%20link=location.href.substring(5);}else{link=location.href.substring(4);}location.href='googlechrome-x-callback://x-callback-url/open/?url='+encodeURIComponent(location.href)+'&x-source=Dolphin&x-success=dolphin://';
```

### iCab Mobile

#### Open in Google Chrome & Return to iCab

```javascript
javascript:location.href='googlechrome-x-callback://x-callback-url/open/?url='+encodeURIComponent(location.href)+'&x-source=iCab%20Mobile&x-success=x-icabmobile://';
```

### Mercury

#### Open in Google Chrome & Return to Mercury

```javascript
javascript:location.href='googlechrome-x-callback://x-callback-url/open/?url='+encodeURIComponent(location.href)+'&x-source=Mercury&x-success=merc://'+encodeURIComponent(location.href)
```

[Table of Contents ↩](#table-of-contents)

---

## Suggested Improvements for Google

1. Adding a search option to the URL scheme would be quite handy. Being able to easily enter a search term in Launch Center Pro and having Google Chrome open with that search would be awesome. Bonus points for letting the scheme specify which search engine.

[Table of Contents ↩](#table-of-contents)