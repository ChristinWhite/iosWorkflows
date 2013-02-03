# Pinbook

## URL Scheme

## Bookmarklets

### Open in Pinbook

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&description='+encodeURIComponent(window.getSelection());
```

### Open in Pinbook (Private)

The private tag doesn't seem to be working at the moment, I've contacted the developer and am awaiting a response. 

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&private=yes'+'&description='+encodeURIComponent(window.getSelection());
```

### Read Later in Pinbook

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&description='+encodeURIComponent(window.getSelection());
```

### Read Later in Pinbook (Private)



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


