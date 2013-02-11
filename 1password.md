# 1Password

[Official Site](https://agilebits.com/onepassword/ios) • [iTunes Link](https://itunes.apple.com/us/app/1password/id568903335?mt=8)

Note: Some or all of these workflows may not work on previous versions of 1Password such as 1Password for iPhone, 1Password for iPad and 1Password Pro.

## URL Scheme

### Search 1Password

    onepassword://
        onepassword://search/
            onepassword://search/twitter

### Open in 1Password's browser

    ophttp://
        ophttp://www.google.com
    ophttps://
        ophttps://www.google.com

Documentation: [Official - Developers: Here’s how to add a little 1Password to your iOS apps](http://blog.agilebits.com/2013/01/24/developers-heres-how-to-add-a-little-1password-to-your-ios-apps/) • [handleOpenURL](http://handleopenurl.com/scheme/1password)

---

## Launch Center Pro Actions

### Open HTTP URL - \[clipboard\]

    ophttp://[clipboard]

### Open HTTPS URL - \[clipboard\]

    ophttps://[clipboard]

### Search for Clipped - \[clipboard\]

    onepassword://search/[clipboard]

### Search 1Password for ..? - \[prompt\]

    onepassword://search/[prompt]

---

## Bang On Custom URL Scheme

    onepassword://search/%@

---

## Mr. Reader Services

### Browser Service: Open in 1Password

    App Name: 1Password
    Protocol: onepassword:
    HTTP URL Scheme:
        ophttp://[URL-WITHOUT-PROTOCOL]
    HTTPS URL Scheme:
        ophttps://[URL-WITHOUT-PROTOCOL]

[Download Service](https://raw.github.com/christopherdwhite/iosWorkflows/master/mrreader-services/1password.mrreaderbrowserconf)
                   
---

## Drafts Actions

### URL Action: Open Link (without protocol) in 1Password

    Name: Open Link (without protocol) in 1Password
    URL:
        ophttp://[[title]]

*Note: This action will send 1Password whatever is on the first line of your draft.*

This bookmarklet isn't ideal because you need to strip out the protocol manually since 1Password doesn't know what to do with a URL that still has the *http://* protocol included like this:

*[ophttp://http://www.google.com](ophttp://http://www.google.com)*

[Install Action](drafts://x-callback-url/import_action?type=URL&name=Open%20Link%20%28without%20protocol%29%20in%201Password&url=ophttp%3A%2F%2F%5B%5Btitle%5D%5D)

---

## Bookmarklets

### Generic (Safari)

#### Open in 1Password

```javascript
javascript:location.href='ophttp'+location.href.substring(4);
```

This bookmarklet is based on Jon Abrams' [Google Chrome Bookmarklet](http://blog.jonabrams.com/post/26099585134/open-in-chrome) for the substring trick.

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

This bookmarklet will work great if you always name your 1Password logins by the domain name (*twitter.com*), the default naming convention if you save logins via the desktop browser extensions. 

However, if you name all of your logins by the site name (*Twitter*) this won't work very well because 1Password for iOS currently only searches the login titles, *not* the URLs or other information. This means that searching for *twitter.com* won't find an item with the title *Twitter* due the URL suffix.

I personally prefer naming everything by the site name because it seems cleaner and it's easier to find items at glance. Because of the search limitation this bookmarklet isn't a great solution for me for the time being. I hope that AgileBits will improve the search functionality to include URLs, if they do this bookmarklet will become infinitely more useful.

Alternatively, if you don't already use the domain in the title you could always change your naming convention. Being a bit OCD and having over 1000 logins in 1Password I think I'll wait for now and use the following bookmarklet instead.

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

This bookmarklet combines the prior two, I thought it could be useful to have the domain feature built into a single bookmarklet for anyone that uses the domain naming convention.

---

## Suggested improvements for AgileBits

Being able to search beyond item names to URLs and other item information would be a **huge** improvement to open up more URL Scheme workflow possibilities.

It would also be fantastic if they switched over to (or added added support for) [x-callback-url](http://x-callback-url.com/) functionality. One way I think they could use this is to designate coping a password to the clipboard as x-success.

If they were to do this you could setup a bookmarklet to open 1Password and search for the site (hopefully by URL), 1Password could automatically select the login if there's only one result or let you choose. You could then copy the password and 1Password would send you back to your chosen browser with the password ready for you to paste. It isn't quite like having a browser extension but it could be the most seamless 1Password workflow possible on iOS.

Finally, it would be nice to have [ophttp://http:www.google.com](ophttp://http:www.google.com), [ophttps://https://www.google.com](ophttps://https://www.google.com) or even [ophttp://https://www.google.com](ophttps://https://www.google.com) work so that 'Open URL in 1Password' actions could be added to apps like Drafts that don't offer JavaScript (like a browser) or more advanced URL configurability (like Mr. Reader) to automatically strip away the *http://* protocol and replace it with *ophttp://.* [Mercury Browser](http://mercury-browser.com/) is a good example of this working.

For a security centric application this would also help ensure that an users who may currently need to strip out the protocol wouldn't accidentally open an *https://* link as *http://*.
