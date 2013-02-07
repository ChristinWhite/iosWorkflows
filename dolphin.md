# Dolphin

## URL Scheme

    dolphin://
    dolphin://dolphin-browser.com

Dolphin's URL Scheme is listed on [handleOpenURL](http://handleopenurl.com/scheme/dolphin-browser) but I believe the information is incorrect. Including the http:// in the URL scheme result in Dolphin trying to load http://http://dolphin-browser.com.

## Bookmarklet: Open in Dolphin

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

Caution: This will open an https:// link in Dolphin but it will strip away the 's.' Unlike Mercury or Chrome there isn't a way to pass along an https link intact.

When I asked @DolphinCares about it [this was their reply](http://twitter.com/DolphinCares/status/296874545028161536):

> @chriswhite Sorry, we don't support such URL right now.