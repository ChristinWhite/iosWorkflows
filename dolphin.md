# Dolphin

## URL Scheme

    dolphin://
    dolphin://dolphin-browser.com

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

Note: This will open an https: link in Dolphin but it will strip away the 's.' Unlike Mercury and Chrome there isn't a way to pass along an https link intact.

[@DolphinCares](http://twitter.com/DolphinCares/status/296874545028161536)
> @chriswhite Sorry, we don't support such URL right now.

http://twitter.com/DolphinCares/status/296874545028161536