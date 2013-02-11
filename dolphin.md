# Dolphin

[Official Site](http://dolphin-browser.com/) • [iTunes Link](http://itunes.apple.com/us/artist/mobotap-inc./id433626481)

## URL Scheme

### Function

    dolphin://
        dolphin://dolphin-browser.com

[handleOpenURL](http://handleopenurl.com/scheme/dolphin-browser)

Note: I believe the information on the handleOpenURL link is incorrect. Including the *http://* in the URL scheme result in Dolphin trying to load *http://http://dolphin-browser.com* and Dolphin doesn't seem to like the double protocol. I've pinged the developer to double check it.

For now, I've included the usage based on my personal testing above.

---

## Bookmarklets

### Generic (Safari)

#### Open in Dolphin

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

*Caution*: This will open an https:// link in Dolphin but it will strip away the 's.' Unlike Mercury or Chrome [there isn't a way](http://twitter.com/DolphinCares/status/296874545028161536) to pass along an https link intact.