# Drafts

[Official Site](http://agiletortoise.com/drafts/) • Drafts for iPad [iTunes Link](https://itunes.apple.com/us/app/drafts-for-ipad/id542797283?mt=8) • Drafts for iPhone [iTunes Link](https://itunes.apple.com/us/app/drafts-for-ipad/id542797283?mt=8)

Drafts URL scheme support is **Amazing** and is a fantastic benchmark to compare other apps' schemes to. Not that this should be a surprise given that Greg Pierce of Agile Tortoise [wrote the spec](http://x-callback-url.com/about/) for [x-callback-url](http://x-callback-url.com/).

For more ideas and workflows for use with Drafts check out Federico Viticci's MacStories article [iOS Automation and Workflows with Drafts](http://www.macstories.net/reviews/ios-automation-and-workflows-with-drafts/). Agile Tortoise also maintains their own [Drafts Actions Directory](http://actions.getdrafts.com/)

## URL Scheme

### Function

Drafts for iPad:

    drafts://
    x-drafts://

Drafts for iPhone:

    drafts://
    x-drafts-for-ipad://

/Create

    drafts://
        x-callback-url/
            create?
                text
                action
                x-success
                x-error
                    drafts://x-callback-url/create?text=Drafts%20rocks&action=Append%20to%20Scratch

Documentation: [Official: Drafts for Developers](http://agiletortoise.com/drafts-developers/) • [handleOpenURL](http://handleopenurl.com/scheme/drafts) • [App Lookup](http://applookup.com/App/502385074)

Note: There's also an undocumented scheme for importing Drafts actions, you can generate these urls by choosing *Share Action* from Draft's custom action settings.

---

## Bookmarklets

### Generic (Safari)

#### Send to Drafts

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

### Dolphin

#### Append to Scratch via Drafts & Return to Dolphin

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
