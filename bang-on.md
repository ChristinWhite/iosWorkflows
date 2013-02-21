# Bang On

[Official Site](http://kepner.me/apps/) • [iTunes Link](https://itunes.apple.com/us/app/bang-on-a-nice-search-app/id521507324?mt=8)

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

---

## URL Scheme

### Search

	bang-on://
		bang-on://?q=

	Example:
		bang-on://?q=Twitter

Documentation: [App Lookup](http://applookup.com/App/521507324)

[Table of Contents ↩](#table-of-contents)

---

## Launch Center Pro Actions

### Clipboard Actions

#### Search Bang On for \[clipboard\]

    bang-on://?q=[clipboard]

#### Search Bang On for \[clipboard\] with a specific !bang

    bang-on://?q=[clipboard]%20!bang

Just replace *!bang* with the !bang you'd like to hard code into the Action.

### Prompt Actions

#### Search Bang On for \[prompt\]

    bang-on://?q=[prompt]

#### Search Bang On for \[prompt\] with a specific !bang

    bang-on://?q=[prompt]%20!bang

Just replace *!bang* with the !bang you'd like to hard code into the Action.

[Table of Contents ↩](#table-of-contents)

---

## Drafts Actions

### URL Actions

#### Search Bang On for Title

    Name: Search Bang On for Title
    URL:

        bang-on://?q=[[title]]

*Note: This action will send Bang On whatever is on the first line of your draft.*

~~[Install Action](drafts://x-callback-url/import_action?type=URL&name=Search%20Bang%20On%20for%20Title&url=bang-on%3A%2F%2F%3Fq%3D%5B%5Btitle%5D%5D) • [Help](guide.md#installing-draft-actions)~~ • Copy & paste this URL into the location bar:

    drafts://x-callback-url/import_action?type=URL&name=Search%20Bang%20On%20for%20Title&url=bang-on%3A%2F%2F%3Fq%3D%5B%5Btitle%5D%5D
zzz
[Table of Contents ↩](#table-of-contents)

---

## Mr. Reader Services

### Other App Services

#### Search Bang On for Selection

    App Name: Search Bang On for Selection
    Protocol: bang-on:
    URL Scheme Template:

        bang-on://?q={[TEXT-SELECTED]}
    
    Visibility:
        Standard Menu: On/Off
        Text Selection Menu: On/Off
        Link Menu: On/Off

[Download Service](https://github.com/christopherdwhite/iosWorkflows/raw/master/mrreader-services/search-bang-on-for-selection.mrreaderappconf) • [Help](guide.md#installing-mr-reader-browser-and-other-app-services)

[Table of Contents ↩](#table-of-contents)

---

## Bookmarklets

Important Note: Bookmarklets that take advantage of your text selection work differently or don't work at all in different browsers. Please see the guide for [further details and workarounds](guide.md#bookmarklet-limitations-for-selected-text-in-different-browsers).

### Generic

#### Launch Bang On (Official)

```javascript
javascript:location.href='bang-on://'+location.href
```

#### Search Bang On for Selection

```javascript
javascript:location.href='bang-on://?q='+encodeURIComponent(window.getSelection())
```

#### Search Bang On for Selection with a specific !bang

```javascript
javascript:location.href='bang-on://?q='+encodeURIComponent(window.getSelection())+'%20'+'!bang'
```

Just replace *!bang* with the !bang you'd like to hard code into the bookmarklet.

[Table of Contents ↩](#table-of-contents)