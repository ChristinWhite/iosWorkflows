# 1Password

## URL Scheme

Search 1Password:

	onepassword://
	onepassword://search/
	onepassword://search/twitter

Open in 1Password's browser:

	ophttp://
	ophttps://

[Developers: Here’s how to add a little 1Password to your iOS apps](http://blog.agilebits.com/2013/01/24/developers-heres-how-to-add-a-little-1password-to-your-ios-apps/)

## Bookmarklet: Open in 1Password

```javascript
javascript:location.href='ophttp'+location.href.substring(4);
```

Based on Jon Abrams' [Google Chrome Bookmarklet](http://blog.jonabrams.com/post/26099585134/open-in-chrome).

## Bookmarklet: Search 1Password for Selection

```javascript
javascript:location.href='onepassword://search/'+encodeURIComponent(window.getSelection());
```

## Bookmarklet: Search 1Password for...?

```javascript
javascript:var%20search=window.prompt('Search%201Password%20for...');location.href='onepassword://search/'+encodeURIComponent(search);
```

## Bookmarklet: Search 1Password for Domain

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

Note: This bookmarklet will work great if you always name your 1Password logins the domain name (*twitter.com*,*finerthings.in*,) which is the default convention if you use the 1Password browser extensions. However, since 1Password for iOS only searches the item names, not their URL's this may cause problems if you name your logins by site name since searching for *twitter.com* won't find an item named *Twitter* due the URL suffix.

## Bookmarklet: Search 1Password for...? If Empty Search 1Password for Domain

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

This bookmarklet combines the prior two. I don't usually leave 1Password item names as just the domain names but I figured having it doesn't hurt to have this as a backup option.