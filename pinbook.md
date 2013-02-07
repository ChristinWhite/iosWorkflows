# Pinbook

## URL Scheme

    pinbook://
    pinbook://add?
        url
        title
        tags (separated by spaces)
        description
        private (yes/no, default: no)
        readlater (yes/no, default: no)

Source: [Adding Bookmarks Using Pinbook's URL Scheme](http://help.albinadevelopment.com/kb/pinbook/adding-bookmarks-using-pinbooks-url-scheme)

Note that this hasn't yet been updated to reflect Pinbook's x-callback-url changes. 

## Private Flag

The private flag doesn't seem to be working at the moment, I've contacted the developer and am awaiting a response. 

## Launch Center Pro

### Bookmark Clipboard in Pinboard



### Bookmark Clipboard in Pinbook with Tags Prompt



### Bookmark Clipboard in Pinbook with Description Prompt



### Bookmark Clipboard in Pinbook with Tags & Description Prompts



---

## Mr. Reader Pinbook Services

### Add to Pinbook

    App Name: Pinbook
    Protocol: pinbook:
    URL Scheme Template
        pinbook://x-callback-url/add?url=[URL]&title={[TITLE]}&description={[TEXT-SELECTED]}

### Add to Pinbook (Private)



### Read Later in Pinbook

    App Name: Read Later in Pinbook
    Protocol: pinbook:
    URL Scheme Template
      pinbook://x-callback-url/add?url=[URL]&title={[TITLE]}&readlater=yes&description={[TEXT-SELECTED]}

### Read Later in Pinbook (Private)



---

## Drafts URL Actions

Note: For all of these actions the URL must be on the first line in Drafts. Any additional lines will be added as the description.

### Add Link to Pinbook

    Name: Add Link to Pinbook
    URL: pinbook://x-callback-url/add?url=[[title]]&description=[[body]]

### Add Link to Pinbook (Private)



### Read Later in Pinbook

    Name: Add Link to Pinbook
    URL: pinbook://x-callback-url/add?url=[[title]]&readlater=yes&description=[[body]]

### Read Later in Pinbook (Private)

---

## Bookmarklets

### Open in Pinbook

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&description='+encodeURIComponent(window.getSelection());
```

### Open in Pinbook (Private)

(This doesn't work yet)

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&private=yes'+'&description='+encodeURIComponent(window.getSelection());
```

### Read Later in Pinbook

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&description='+encodeURIComponent(window.getSelection());
```

### Read Later in Pinbook (Private)



---

## Dolphin Bookmarklets

### Open in Pinbook & Return to Dolphin

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&description='+encodeURIComponent(window.getSelection())+'&x-success=dolphin://';
```

### Open in Pinbook (Private) & Return to Dolphin



### Read Later in Pinbook & Return to Dolphin

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&description='+encodeURIComponent(window.getSelection())+'&x-success=dolphin://';
```

### Read Later in Pinbook (Private) & Return to Dolphin

---

## Google Chrome Bookmarklets

---

## Mercury Bookmarklets

---

## Further Ideas

It would be great to setup Bang On & Launch Center Pro search actions if search was added to the URL Scheme.