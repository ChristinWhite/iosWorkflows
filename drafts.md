# Drafts

## URL Scheme

[Drafts for Developers](http://agiletortoise.com/drafts-developers)

## Bookmarklets

### Send to Drafts

```javascript
javascript:if(window.getSelection()!=''){var%20selected=encodeURIComponent(window.getSelection());var%20selected='%250A%250A%253E%2520'+selected.replace(/%250A/g,'%250A%253E%2520');}else{var%20selected='';}location.href='drafts://x-callback-url/create?text=['+encodeURIComponent(document.title)+']('+encodeURIComponent(location.href)+')'+selected;
```

Expanded:

```javascript
javascript:

if (window.getSelection() != '') {
    var selected = encodeURIComponent(window.getSelection());
    var selected = '%250A%250A%253E%2520' + selected.replace(/%250A/g,'%250A%253E%2520');
} else {
    var selected='';
}
    
location.href = 'drafts://x-callback-url/create?text=[' + encodeURIComponent(document.title) + '](' + encodeURIComponent(location.href) + ')' + selected;
```

### Append to Scratch via Drafts



## Dolphin Bookmarklets

### Append to Scratch via Drafts & Return to Dolphin

```javascript
javascript:if(window.getSelection()!=''){var%20selected=encodeURIComponent(window.getSelection());var%20selected='%250A%250A%253E%2520'+selected.replace(/%250A/g,'%250A%253E%2520');}else{var%20selected='';}location.href='drafts://x-callback-url/create?'+'text='+'['+encodeURIComponent(document.title)+']('+encodeURIComponent(location.href)+')'+selected+'&action='+'Append%20to%20Scratch&nbsp;'+'&x-success='+'dolphin://';
```

Expanded:

```javascript
javascript:

if (window.getSelection() != '') {
    var selected = encodeURIComponent(window.getSelection());
    var selected = '%250A%250A%253E%2520' + selected.replace(/%250A/g,'%250A%253E%2520');
} else {
    var selected='';
}
    
location.href = 'drafts://x-callback-url/create?'
    + 'text=' + '[' + encodeURIComponent(document.title) + '](' + encodeURIComponent(location.href) + ')' + selected
    + '&action=' + 'Append%20to%20Scratch&nbsp;'
    + '&x-success=' + 'dolphin://';
```