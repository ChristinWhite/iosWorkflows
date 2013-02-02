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

## Bookmarklet: Open Page in 1Password

```javascript
javascript:location.href="ophttp"+location.href.substring(4);
```

Based on Jon Abrams' [Google Chrome Bookmarklet](http://blog.jonabrams.com/post/26099585134/open-in-chrome).

## Bookmarklet: Search 1Password for Site

## Bookmarklet: Search 1Password for Selection