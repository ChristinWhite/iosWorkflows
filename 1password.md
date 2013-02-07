# 1Password

[iTunes Link](https://itunes.apple.com/us/app/1password/id568903335?mt=8) • [Official Site](https://agilebits.com/onepassword)

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

Documentation: [Developers: Here’s how to add a little 1Password to your iOS apps](http://blog.agilebits.com/2013/01/24/developers-heres-how-to-add-a-little-1password-to-your-ios-apps/) • [handleOpenURL](http://handleopenurl.com/scheme/1password)

---

## Launch Center Pro Actions

### Open HTTP URL (Official) - Clipboard

    ophttp://[clipboard]

### Open HTTPS URL (Official) - Clipboard

    ophttps://[clipboard]

### Search for Clipped (Official) - Clipboard

    onepassword://search/[clipboard]

### Search 1Password for ..? (Official) - Prompt

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

This isn't ideal because you need to strip out the protocol manually since 1Password doesn't know what to do with a URL that has the *http://* protocol included like this:

*[ophttp://http://www.google.com](ophttp://http://www.google.com)*

Note: The URL must be on the first line in Drafts.

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

This bookmarklet will work great if you always name your 1Password logins the domain name (*twitter.com*) which is the default item name if you use the 1Password browser extensions to create the login. However, since 1Password for iOS only searches the item names, not their URL's this may cause problems if you name your logins by site name since searching for *twitter.com* won't find an item named *Twitter* due the URL suffix. 

I almost always adjust the name when I'm using the extension or I catch it when I do a cleanup review later so for me this isn't a great option. If 1Password for iOS eventually adds the functionality to search URL and other information instead of just titles this will become infinitely more useful.

#### Search 1Password for...? If Empty Search for Domain

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

Expanded

```javascript
javascript:var%20search=window.prompt('Search%201Password%20for...');if(search==''){var%20search=document.domain;if(search.substring(0,4)=='www.'){search=search.substring(4);}}location.href='onepassword://search/'+encodeURIComponent(search);
```

This bookmarklet combines the prior two, I thought it it could be useful to have the domain feature built into a single bookmarklet for anyone that uses the domain naming convention.

---

## Requested Improvements for AgileBits

Being able to search beyond item names to URLs and other item information would be a **huge** improvement to open up more URL Scheme workflow possibilities.

It would also be fantastic if you switched over to (or added added support for) [x-callback-url](http://x-callback-url.com/) functionality. With an x-callback-url scheme it would be easy to open 1Password from Safari (or another alternative browser), do a search for the URL or title, then let the user select the item and copy your password. Once the password is coppied 1Password could then automatically send you back to your other browser where you could paste in the password. It isn't quite like having a browser extension but it could be the most seamless 1Password workflow possible on iOS.

Finally, it would be nice to have [ophttp://http:www.google.com](ophttp://http:www.google.com), [ophttps://https://www.google.com](ophttps://https://www.google.com) or even [ophttp://https://www.google.com](ophttps://https://www.google.com) work so that 'Open URL in 1Password' actions could be added to apps like Drafts that don't offer JavaScript (like a browser) or more advanced URL configurability (like Mr. Reader) to automatically strip away the *http://* protocol and replace it with *ophttp://.* [Mercury Browser](http://mercury-browser.com/) a good example of this working. This would also simplify some of the bookmarklets included here.