# Pinbook

[Official Site](http://albinadevelopment.com/pinbook/index.html) • [iTunes Link](https://itunes.apple.com/us/app/pinbook-for-pinboard/id564452716?mt=8)

## Table of Contents

1. [URL Scheme](#url-scheme)
1. [Launch Center Pro Actions](#launch-center-pro-actions)
    1. [Clipboard Actions](#clipboard-actions)
    1. [Prompt Actions](#prompt-actions)
1. [Drafts Actions](#drafts-actions)
    1. [URL Actions](#url-actions)
1. [Mr. Reader Services](#mr-reader-services)
    1. [Other App Services](#other-app-services)
1. [Bookmarklets](#bookmarklets)
    1. [Generic](#generic)
    1. [Google Chrome](#google-chrome)
    1. [Dolphin](#dolphin)
    1. [iCab Mobile](#icab-mobile)
    1. [Mercury](#mercury)
1. [Additional Ideas](#additional-ideas)
1. [Suggested Improvements for Developer](#suggested-improvements-for-developer)

---

## URL Scheme

### Add

    pinbook://
        x-callback-url/
            add?
                url
                title
                tags (separated by spaces)
                description
                private (yes/no, default: no)
                readlater (yes/no, default: no)
            x-success=
            x-cancel=
    
    Example: 
        pinbook:///x-callback-url/add?url=http://apple.com&title=Apple&tags=tag1%20tag2%20tag3&description=Here%20are%20some%20notes&private=yes&readlater=no&x-success=googlechrome://&x-cancel=googlechrome://

Documentation: [Official](http://help.albinadevelopment.com/kb/pinbook/adding-bookmarks-using-pinbooks-url-scheme) - Note: The documentation has not yet been updated to reflect [x-callback-url](http://x-callback-url.com/) support. I've corrected this in the URL scheme information above.

## Private Flag is Currently Broken

The private flag in Pinbook's URL scheme is currently broken and will not automatically mark links as private. I've spoken to the developer and he [confirmed](http://twitter.com/pinbookapp/status/301560094355759104) that this will be fixed in the next update. You can go ahead and start using the *private* workflows, they will still work, just make sure you remember to mark them as private manually until the bug is fixed.

[Table of Contents ↩](#table-of-contents)

---

## Launch Center Pro Actions

There are four variations to each of these actions:

1. Normal
2. Private
3. Read Later
4. Private & Read Later

To save space and increase legibility I'm only including *Normal* variation of the actions below, if you'd prefer to use one of the variations just add the following respective suffixes to the URL:

    &private=yes
    &readlater=yes
    &private=yes&readlater=yes

### Clipboard Actions

#### Add \[clipboard\] URL to Pinbook

    pinbook://x-callback-url/add?url=[clipboard]

#### Add \[clipboard\] URL to Pinbook with Tags \[Prompt\]

    pinbook://x-callback-url/add?url=[clipboard]&tags=[prompt]

#### Add \[clipboard\] URL to Pinbook with Description \[Prompt\]

    pinbook://x-callback-url/add?url=[clipboard]&description=[prompt]

### Prompt Actions

#### Add \[prompt\] URL to Pinbook

    pinbook://x-callback-url/add?url=[prompt]

#### Add \[prompt\] URL to Pinbook with Tags \[Prompt\]

    pinbook://x-callback-url/add?url=[prompt]&tags=[prompt]

#### Add \[prompt\] URL to Pinbook with Description \[clipboard\]

    pinbook://x-callback-url/add?url=[prompt]&description=[clipboard]

#### Add \[prompt\] URL to Pinbook with Description \[Prompt\]

    pinbook://x-callback-url/add?url=[prompt]&description=[prompt]

#### Add \[prompt\] URL to Pinbook with Tags \[Prompt\] & Description \[clipboard\]

    pinbook://x-callback-url/add?url=[prompt]&tags=[prompt]&description=[clipboard]

#### Add \[prompt\] URL to Pinbook with Tags \[Prompt\] & Description \[prompt\]

    pinbook://x-callback-url/add?url=[prompt]&tags=[prompt]&description=[prompt]

[Table of Contents ↩](#table-of-contents)

---

## Drafts Actions

### URL Actions

Note: For all of these actions the URL must be on the first line in Drafts. All following lines will be added as the description.

#### Add Link to Pinbook

    Name: Add Link to Pinbook
    URL:
        pinbook://x-callback-url/add?url=[[title]]&description=[[body]]&x-success=drafts://&x-cancel=drafts://

[Install Action](drafts://x-callback-url/import_action?type=URL&name=Add%20Link%20to%20Pinbook&url=pinbook%3A%2F%2Fx-callback-url%2Fadd%3Furl%3D%5B%5Btitle%5D%5D%26description%3D%5B%5Bbody%5D%5D%26x-success%3Ddrafts%3A%2F%2F%26x-cancel%3Ddrafts%3A%2F%2F) • [Help](guide.md#installing-drafts-actions)

#### Add Link to Pinbook (Private)

    Name: Add Link to Pinbook (Private)
    URL:
        pinbook://x-callback-url/add?url=[[title]]&description=[[body]]&x-success=drafts://&x-cancel=drafts://

[Install Action](drafts://x-callback-url/import_action?type=URL&name=Add%20Link%20to%20Pinbook%20%28Private%29&url=pinbook%3A%2F%2Fx-callback-url%2Fadd%3Furl%3D%5B%5Btitle%5D%5D%26private%3Dyes%26description%3D%5B%5Bbody%5D%5D%26x-success%3Ddrafts%3A%2F%2F%26x-cancel%3Ddrafts%3A%2F%2F) • [Help](guide.md#installing-drafts-actions)

#### Read Link Later in Pinbook

    Name: Read Link Later in Pinbook
    URL:
        pinbook://x-callback-url/add?url=[[title]]&readlater=yes&description=[[body]]&x-success=drafts://&x-cancel=drafts://

[Install Action](drafts://x-callback-url/import_action?type=URL&name=Read%20Link%20Later%20in%20Pinbook&url=pinbook%3A%2F%2Fx-callback-url%2Fadd%3Furl%3D%5B%5Btitle%5D%5D%26readlater%3Dyes%26description%3D%5B%5Bbody%5D%5D%26x-success%3Ddrafts%3A%2F%2F%26x-cancel%3Ddrafts%3A%2F%2F) • [Help](guide.md#installing-drafts-actions)

#### Read Link Later in Pinbook (Private)

    Name: Read Link Later in Pinbook (Private)
    URL:
        pinbook://x-callback-url/add?url=[[title]]&private=yes&readlater=yes&description=[[body]]&x-success=drafts://&x-cancel=drafts://

[Install Action](drafts://x-callback-url/import_action?type=URL&name=Read%20Link%20Later%20in%20Pinbook%20%28Private%29&url=pinbook%3A%2F%2Fx-callback-url%2Fadd%3Furl%3D%5B%5Btitle%5D%5D%26private%3Dyes%26readlater%3Dyes%26description%3D%5B%5Bbody%5D%5D%26x-success%3Ddrafts%3A%2F%2F%26x-cancel%3Ddrafts%3A%2F%2F) • [Help](guide.md#installing-drafts-actions)

[Table of Contents ↩](#table-of-contents)

---

## Mr. Reader Services

### Other App Services

#### Add to Pinbook

    App Name: Add to Pinbook
    Protocol: pinbook:
    URL Scheme Template:
        pinbook://x-callback-url/add?url=[URL]&title={[TITLE]}&description={[TEXT-SELECTED]}&x-success=mrreader://&x-cancel=mrreader://
    
    Visibility:
        Standard Menu: On
        Text Selection Menu: On
        Link Menu: On

[Download Service](https://github.com/christopherdwhite/iosWorkflows/raw/master/mrreader-services/add-to-pinbook.mrreaderappconf) • [Help](guide.md#installing-mr-reader-browser-and-other-app-services)

#### Add to Pinbook (Private)

    App Name: Add to Pinbook (Private)
    Protocol: pinbook:
    URL Scheme Template:
        pinbook://x-callback-url/add?url=[URL]&title={[TITLE]}&private=yes&description={[TEXT-SELECTED]}&x-success=mrreader://&x-cancel=mrreader://
    
    Visibility:
        Standard Menu: On
        Text Selection Menu: On
        Link Menu: On

[Download Service](https://github.com/christopherdwhite/iosWorkflows/raw/master/mrreader-services/add-to-pinbook-private.mrreaderappconf) • [Help](guide.md#installing-mr-reader-browser-and-other-app-services)

#### Read Later in Pinbook

    App Name: Read Later in Pinbook
    Protocol: pinbook:
    URL Scheme Template:
        pinbook://x-callback-url/add?url=[URL]&title={[TITLE]}&readlater=yes&description={[TEXT-SELECTED]}&x-success=mrreader://&x-cancel=mrreader://
    
    Visibility:
        Standard Menu: On
        Text Selection Menu: On
        Link Menu: On

[Download Service](https://github.com/christopherdwhite/iosWorkflows/raw/master/mrreader-services/read-later-in-pinbook.mrreaderappconf) • [Help](guide.md#installing-mr-reader-browser-and-other-app-services)

#### Read Later in Pinbook (Private)

    App Name: Read Later in Pinbook (Private)
    Protocol: pinbook:
    URL Scheme Template:
        pinbook://x-callback-url/add?url=[URL]&title={[TITLE]}&private=yes&readlater=yes&description={[TEXT-SELECTED]}&x-success=mrreader://&x-cancel=mrreader://
    
    Visibility:
        Standard Menu: On
        Text Selection Menu: On
        Link Menu: On

[Download Service](https://github.com/christopherdwhite/iosWorkflows/raw/master/mrreader-services/read-later-in-pinbook-private.mrreaderappconf) • [Help](guide.md#installing-mr-reader-browser-and-other-app-services)

[Table of Contents ↩](#table-of-contents)

---

## Bookmarklets

Important Note: Bookmarklets that take advantage of your text selection work differently or don't work at all in different browsers. Please see the guide for [further details and workarounds](guide.md#bookmarklet-limitations-for-selected-text-in-different-browsers).

### Generic

#### Open in Pinbook

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&description='+encodeURIComponent(window.getSelection());
```

#### Open in Pinbook (Private)

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&private=yes'+'&description='+encodeURIComponent(window.getSelection());
```

#### Read Later in Pinbook

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&description='+encodeURIComponent(window.getSelection());
```

#### Read Later in Pinbook (Private)

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&private=yes'+'&description='+encodeURIComponent(window.getSelection());
```

### Google Chrome

#### Open in Pinbook & Return to Chrome

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&description='+encodeURIComponent(window.getSelection())+'&x-success=googlechrome://'+'&x-cancel=googlechrome://';
```

#### Open in Pinbook (Private) & Return to Chrome

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&private=yes'+'&description='+encodeURIComponent(window.getSelection())+'&x-success=googlechrome://'+'&x-cancel=googlechrome://';
```

#### Read Later in Pinbook & Return to Chrome

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&description='+encodeURIComponent(window.getSelection())+'&x-success=googlechrome://'+'&x-cancel=googlechrome://';
```

#### Read Later in Pinbook (Private) & Return to Chrome

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&private=yes'+'&description='+encodeURIComponent(window.getSelection())+'&x-success=googlechrome://'+'&x-cancel=googlechrome://';
```

### Dolphin

#### Open in Pinbook & Return to Dolphin

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&description='+encodeURIComponent(window.getSelection())+'&x-success=dolphin://'+'&x-cancel=dolphin://';
```

#### Open in Pinbook (Private) & Return to Dolphin

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&private=yes'+'&description='+encodeURIComponent(window.getSelection())+'&x-success=dolphin://'+'&x-cancel=dolphin://';
```

#### Read Later in Pinbook & Return to Dolphin

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&description='+encodeURIComponent(window.getSelection())+'&x-success=dolphin://'+'&x-cancel=dolphin://';
```

#### Read Later in Pinbook (Private) & Return to Dolphin

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&private=yes'+'&description='+encodeURIComponent(window.getSelection())+'&x-success=dolphin://'+'&x-cancel=dolphin://';
```

### iCab Mobile

#### Open in Pinbook & Return to iCab Mobile

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&description='+encodeURIComponent(window.getSelection())+'&x-success=x-icabmobile://'+'&x-cancel=x-icabmobile://';
```

#### Open in Pinbook (Private) & Return to iCab Mobile

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&private=yes'+'&description='+encodeURIComponent(window.getSelection())+'&x-success=x-icabmobile://'+'&x-cancel=x-icabmobile://';
```

#### Read Later in Pinbook & Return to iCab Mobile

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&description='+encodeURIComponent(window.getSelection())+'&x-success=x-icabmobile://'+'&x-cancel=x-icabmobile://';
```

#### Read Later in Pinbook (Private) & Return to iCab Mobile

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&private=yes'+'&description='+encodeURIComponent(window.getSelection())+'&x-success=x-icabmobile://'+'&x-cancel=x-icabmobile://';
```

### Mercury

#### Open in Pinbook & Return to Mercury

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&description='+encodeURIComponent(window.getSelection())+'&x-success=merc://'+escape(window.location)+'&x-cancel=merc://'+escape(window.location);
```

#### Open in Pinbook (Private) & Return to Mercury

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&private=yes'+'&description='+encodeURIComponent(window.getSelection())+'&x-success=merc://'+escape(window.location)+'&x-cancel=merc://'+escape(window.location);
```

#### Read Later in Pinbook & Return to Mercury

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&description='+encodeURIComponent(window.getSelection())+'&x-success=merc://'+escape(window.location)+'&x-cancel=merc://'+escape(window.location);
```

#### Read Later in Pinbook (Private) & Return to Mercury

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&private=yes'+'&description='+encodeURIComponent(window.getSelection())+'&x-success=merc://'+escape(window.location)+'&x-cancel=merc://'+escape(window.location);
```

[Table of Contents ↩](#table-of-contents)

---

## Additional Ideas

If Albina Development were to add search actions to their URL Scheme I would love to be able to fire off a Pinbook search from Bang-On, Launch Center Pro, etc.

[Table of Contents ↩](#table-of-contents)

---

## Suggested Improvements for Developer

I love Pinbook's fantastic URL scheme, especially x-callback-url functionality but I think the URL scheme could be expanded to other functions rather than just adding new bookmarks. The most obvious functionality would be to connect Pinbook's search to the URL scheme so that you could define a Pinbook search (as noted above).

Here are a couple of examples of how search could be used:

1. I do a ton of searching in Bang On, it's my one stop search app,. I'd love to be able to type in my search in Bang On with a !pinbook bang to launch Pinbook with that search term. For other people they might us Launch Center Pro, the same functionality would apply.
1. I could be browsing the web and find an article about [LESS](http://lesscss.org/) for CSS, I know I've bookmarked LESS related things before so I select *LESS* in the article and use a bookmarklet to launch Pinbook with LESS as the search term.
1. While working on a new blog post I might need to look up some research that I have bookmarked in Pinboard. By combining search with the x-callback-url I could send the relevant search query from a writing app like [Drafts](http://agiletortoise.com/drafts) to Pinbook, find the information I need and then use a Chrome-like UI button to send me right back to Drafts. No home button, no multitasking bar, no gestures needed.

[Table of Contents ↩](#table-of-contents)