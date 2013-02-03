# 1Password

## URL Scheme

### Search 1Password:

	onepassword://
	onepassword://search/
	onepassword://search/twitter

### Open in 1Password's browser:

	ophttp://
	ophttp://www.google.com
	ophttps://
	ophttps://www.google.com

Source: [Developers: Here’s how to add a little 1Password to your iOS apps](http://blog.agilebits.com/2013/01/24/developers-heres-how-to-add-a-little-1password-to-your-ios-apps/)

## Launch Center Pro

### Open HTTP URL (Official + Clipboard)

    ophttp://[clipboard]

### Open HTTPS URL (Official + Clipboard)

    ophttps://[clipboard]

### Search for Clipped (Official + Clipboard)

    onepassword://search/[clipboard]

### Search 1Password for ..? (Official + Prompt)

    onepassword://search/[prompt]

## Mr. Reader Browser Service: Open in 1Password

    App Name: 1Password
    Protocol: onepassword:
    HTTP URL Scheme:
        ophttp://[URL-WITHOUT-PROTOCOL]
    HTTPS URL Scheme:
        ophttps://[URL-WITHOUT-PROTOCOL]

## Drafts URL Action: Open Link (without protocol) in 1Password

This isn't ideal because you need to strip out the protocol manually since 1Password doesn't know what to do with this link:

*[ophttp://http://www.google.com](ophttp://http://www.google.com)*

    Name: Open Link (without protocol) in 1Password
    URL: ophttp://[[title]]

## Browser Bookmarklets 

### Open in 1Password

Based on Jon Abrams' [Google Chrome Bookmarklet](http://blog.jonabrams.com/post/26099585134/open-in-chrome) for the substring trick.

```javascript
javascript:location.href='ophttp'+location.href.substring(4);
```

### Search 1Password for Selection

```javascript
javascript:location.href='onepassword://search/'+encodeURIComponent(window.getSelection());
```

### Search 1Password for...? Prompt

```javascript
javascript:var%20search=window.prompt('Search%201Password%20for...');location.href='onepassword://search/'+encodeURIComponent(search);
```

### Search 1Password for Current Domain

This bookmarklet will work great if you always name your 1Password logins the domain name (*twitter.com*) which is the default item name if you use the 1Password browser extensions to create the login. However, since 1Password for iOS only searches the item names, not their URL's this may cause problems if you name your logins by site name since searching for *twitter.com* won't find an item named *Twitter* due the URL suffix. 

I almost always adjust the name when I'm using the extension or I catch it when I do a cleanup review later so for me this isn't a great option. If 1Password for iOS eventually adds the functionality to search URL and other information instead of just titles this will become infinitely more useful.

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

### Search 1Password for...? If Empty Search for Domain

This bookmarklet combines the prior two. I don't usually leave 1Password item names as just the domain names but it could be useful to have the domain feature built into a single bookmarklet.

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

## Todo

- Pythonista?
    - Protocol converter for apps like Drafts?

## AgileBits Requests

Being able to search more beyond item names to URLs and other item information would be a **huge** improvement to open up more possibilities for URL Scheme workflows.

It would also be fantastic if you switched over to or added x-callback-url functionality to your scheme. With an x-callback-url scheme it would be easy to open 1Password from Safari (or another alternative browser), do a search for the URL or title, then let the user select the item and copy your password. 1Password could then automatically send you back to your other browser where you could paste the password. It isn't quite like having a browser extension but it would be the most seamless 1Password workflow possible on iOS so far.

Finally, it would be nice to have [ophttp://http:www.google.com](ophttp://http:www.google.com), [ophttps://https://www.google.com](ophttps://https://www.google.com) or even [ophttp://https://www.google.com](ophttps://https://www.google.com) work so that 'Open URL in 1Password' actions could be added to apps like Drafts that don't offer JavaScript (like a browser) or more advanced URL configurability (like Mr. Reader) to automatically strip away the *http://* protocol and replace it with *ophttp://.* See [Mercury Browser](http://mercury-browser.com/) for precedent. 