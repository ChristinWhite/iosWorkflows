# 1Password

[Official Site](https://agilebits.com/onepassword/ios) • [iTunes Link](https://itunes.apple.com/us/app/1password/id568903335?mt=8)

Note: Some or all of these workflows may not work on previous versions of 1Password including 1Password for iPhone, 1Password for iPad and 1Password Pro.

## Table of Contents

1. [URL Scheme](#url-scheme)
1. [Launch Center Pro Actions](#launch-center-pro-actions)
    1. [Clipboard Actions](#clipboard-actions)
    1. [Prompt Actions](#prompt-actions)
1. [Bang On Custom Search URL](#bang-on-custom-search-url)
1. [Drafts Actions](#drafts-actions)
    1. [URL Actions](#url-actions)
1. [Mr. Reader Services](#mr-reader-services)
    1. [Browser Services](#browser-services)
    1. [Other App Services](#other-app-services)
1. [Bookmarklets](#bookmarklets)
    1. [Generic](#generic)
1. [Additional Ideas](#additional-ideas)
1. [Suggested Improvements for AgileBits](#suggested-improvements-for-agilebits)

---

## URL Scheme

### Search 1Password

    onepassword://
        search/
    
    Example:
        onepassword://search/twitter

### Open in 1Password's browser

    ophttp://
    
    Example:
        ophttp://www.google.com
    
    ophttps://
    
    Example:        
        ophttps://www.google.com

Documentation: [Official - Developers: Here’s how to add a little 1Password to your iOS apps](http://blog.agilebits.com/2013/01/24/developers-heres-how-to-add-a-little-1password-to-your-ios-apps/) • [handleOpenURL](http://handleopenurl.com/scheme/1password)

---

## Launch Center Pro Actions

### Clipboard Actions

#### Open HTTP \[clipboard\] URL

    ophttp://[[clipboard]]

This clipboard action isn't ideal because you need to make sure that you copied the link without the protocol *http://* since 1Password doesn't know what to do with a URL that still has the protocol included. It gets confused by this kind of URL:

*[ophttp://http://www.google.com](ophttp://http://www.google.com)*

#### Open HTTPS \[clipboard\] URL

    ophttps://[[clipboard]]

The same is true for the *https://* protocol, you can't include it.

#### Search for \[clipboard\]

    onepassword://search/[clipboard]

### Prompt Actions

#### Open HTTP \[prompt\] URL

    ophttp://[prompt-URL]

Not being able to include the protocol actually works in our favor for the prompt actions, that's seven or eight fewer characters you have to type.

#### Open HTTPS \[prompt\] URL

    ophttps://[prompt-URL]

#### Search 1Password for \[prompt\]

    onepassword://search/[prompt]

[Table of Contents ↩](#table-of-contents)

---

## Bang On Custom Search URL

    onepassword://search/%@

[Table of Contents ↩](#table-of-contents)

---

## Drafts Actions

### URL Actions

#### Open Link (without protocol) in 1Password

    Name: Open Link (without protocol) in 1Password
    URL:
 
        ophttp://[[title]]

*Note: This action will send 1Password whatever is on the first line of your draft.*

This URL action isn't ideal because you need to strip out the protocol manually since 1Password doesn't know what to do with a URL that still has the *http://* protocol included. It gets confused by this kind of URL:

*[ophttp://http://www.google.com](ophttp://http://www.google.com)*

To install the action copy and paste the following URL into your iOS browser's location bar and hit enter • [Help](guide.md#installing-drafts-actions)

    drafts://x-callback-url/import_action?type=URL&name=Open%20Link%20%28without%20protocol%29%20in%201Password&url=ophttp%3A%2F%2F%5B%5Btitle%5D%5D

[Table of Contents ↩](#table-of-contents)

---

## Mr. Reader Services

### Browser Services

#### Open in 1Password

    App Name: 1Password
    Protocol: onepassword:
    HTTP URL Scheme:

        ophttp://[URL-WITHOUT-PROTOCOL]

    HTTPS URL Scheme:

        ophttps://[URL-WITHOUT-PROTOCOL]

[Download Service](/mrreader-services/1password.mrreaderbrowserconf) • [Help](guide.md#installing-mr-reader-browser-and-other-app-services)

### Other App Services

#### Search 1Password for Selection

    App Name: Search 1Password for Selection
    Protocol: onepassword:
    URL Scheme Template:

        onepassword://search/{[TEXT-SELECTED]}
    
    Visibility:
        Standard Menu: Off
        Text Selection Menu: On
        Link Menu: Off

[Download Service](mrreader-services/search-1password-for-selection.mrreaderappconf) • [Help](guide.md#installing-mr-reader-browser-and-other-app-services)

[Table of Contents ↩](#table-of-contents)
                   
---

## Bookmarklets

Important Note: Bookmarklets that take advantage of your text selection work differently or don't work at all in different browsers. Please see the guide for [further details and workarounds](guide.md#bookmarklet-limitations-for-selected-text-in-different-browsers).

### Generic

#### Open in 1Password

```javascript
javascript:window.location='op'+(window.location.href);
```

From the MacStories [post about 1Password 4.1](http://www.macstories.net/links/1password-4-1/).

#### Search 1Password for Selection

```javascript
javascript:location.href='onepassword://search/'+encodeURIComponent(window.getSelection());
```

#### Search 1Password for...? Prompt

```javascript
javascript:var%20search=window.prompt('Search%201Password%20for...');location.href='onepassword://search/'+encodeURIComponent(search);
```

#### Search 1Password for Current Domain

```javascript
javascript:var%20domainString=document.domain;if(domainString.substring(0,4)=='www.'){domainString=domainString.substring(4)}location.href='onepassword://search/'+domainString;
```

Expanded:

```javascript
javascript:

var domainString = document.domain;

if (domainString.substring(0,4) == 'www.') {
    domainString = domainString.substring(4)
}

location.href = 'onepassword://search/' + domainString;
```

This bookmarklet will work great if you always name your 1Password logins by the domain name *(twitter.com)*, the default naming convention if you save logins via the desktop browser extensions. 

However, if you name all of your logins by the site name *(Twitter)* this won't work very well because 1Password for iOS currently ~~only searches the login titles, *not* the URLs or other information. This means that searching for *twitter.com* won't find an item with the title *Twitter* due the URL suffix.~~ See *Update* below.

I personally prefer naming everything by the site name because it seems cleaner and it's easier to find items at glance. Because of the search limitation this bookmarklet isn't a great solution for me for the time being. I hope that AgileBits will improve the search functionality to include URLs, if they do this bookmarklet will become infinitely more useful.

Alternatively, if you don't already use the domain in the title you could always change your naming convention. Being a bit OCD and having over 1000 logins in 1Password I think I'll wait for now and use the following bookmarklet instead.

**Update:** There does seem to be some discrepancy with this, for instance, searching for twitter.com will bring up two of my five Twitter logins. Looking at the information stored in the logins I'm not sure what makes the difference, each of them are set to: http://twitter.com/

I will check with AgileBit's support to see if they know what's going on.

#### Search 1Password for...? If Empty Search for Domain

```javascript
javascript:var%20search=window.prompt('Search%201Password%20for...');if(search==''){var%20search=document.domain;if(search.substring(0,4)=='www.'){search=search.substring(4);}}location.href='onepassword://search/'+encodeURIComponent(search);
```

Expanded

```javascript
var search = window.prompt('Search%201Password%20for...');

if (search == '') {

    var search = document.domain;

    if (search.substring(0,4) == 'www.') {
        search = search.substring(4);
    }
} 

location.href = 'onepassword://search/' + encodeURIComponent(search);
```

This bookmarklet combines the prior two, I thought it could be useful to have the domain feature built into a single bookmarklet for anyone that sometimes uses the domain naming convention.

#### Search 1Password for Selection > Prompt > Domain, or open url in the 1Password browser

```javascript
javascript:(function(){var%20selection=window.getSelection()+%22%22,domain=document.domain.replace(/^ww.*%3F\./gi,%22%22),search=selection||window.prompt(%22Search%201Password%20for...%20\n\nEmpty:%20%22+domain+%22\n%22+'%22O%22:%20O̲pen%20url%20in%201P%20browser');null!==search%26%26(window.location=%22o%22===search.toLowerCase()%3F%22op%22+window.location.href:%22onepassword://search/%22+encodeURIComponent(search||domain))})();
```

Expanded

```javascript
(function(){

    var selection = window.getSelection() + "",
        domain    = document.domain.replace(/^ww.*?\./gi, ""),
        search    = ( selection || window.prompt(
            'Search 1Password for... \n\n' +
            'Empty: ' + domain + '\n' +
            '"O": O\u0332pen url in 1P browser'
        ));

    if (search !== null) { // stop if the user clicked cancel
        window.location = (search.toLowerCase() === 'o') ?
            'op' + (window.location.href) :
            'onepassword://search/' + encodeURIComponent(search || domain);
    }

}());
```

A bookmarklet that combines the [Search 1Password for Selection](#search-1password-for-selection-1) bookmarklet with [Search 1Password for...? If Empty Search for Domain.](search-1password-for-if-empty-search-for-domain). 

**Bonus:** Enter `O` (for "Open") as your search query to open the current URL in the 1Password Browser.


[Table of Contents ↩](#table-of-contents)

---

## Additional Ideas

- A expanded bookmarklet that combines the [Search 1Password for Selection](#search-1password-for-selection-1) bookmarklet with [Search 1Password for...? If Empty Search for Domain.](search-1password-for-if-empty-search-for-domain). Selection > Prompt > Domain.

[Table of Contents ↩](#table-of-contents)

---

## Suggested improvements for AgileBits

1. Being able to search beyond item names to URLs and other item information would be a **huge** improvement to open up more URL Scheme workflow possibilities.
1. It would be fantastic if they switched over to (or added support for) [x-callback-url](http://x-callback-url.com/) functionality. One way I think they could use this is to designate coping a password to the clipboard as x-success.
    
    If they were to do this you could setup a bookmarklet to open 1Password and search for the site (hopefully by URL), 1Password could automatically select the login if there's only one result or let you choose. You could then copy the password and 1Password would send you back to your chosen browser with the password ready for you to paste. It isn't quite like having a browser extension but it could be the most seamless 1Password workflow possible on iOS.
1. It would be nice to have [ophttp://http:www.google.com](ophttp://http:www.google.com), [ophttps://https://www.google.com](ophttps://https://www.google.com) or even [ophttp://https://www.google.com](ophttps://https://www.google.com) work so that 'Open URL in 1Password' actions could be added to apps like Drafts that don't offer JavaScript (like a browser) or more advanced URL configurability (like Mr. Reader) to automatically strip away the *http://* protocol and replace it with *ophttp://.* [Mercury Browser](http://mercury-browser.com/) is a good example of this working.
    
    For a security centric application I think this is important because it would also help ensure that an users who may currently need to strip out the protocol wouldn't accidentally open an *https://* link as *http://*.

[Table of Contents ↩](#table-of-contents)
