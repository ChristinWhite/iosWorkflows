# Drafts

[Official Site](http://agiletortoise.com/drafts/) • iTunes Link: [iPad](https://itunes.apple.com/us/app/drafts-for-ipad/id542797283?mt=8) & [iPhone](
https://itunes.apple.com/us/app/drafts/id502385074?mt=8)

Drafts URL scheme support is **Amazing** and is a fantastic benchmark to compare other apps' to. Not that this should be a surprise given that Greg Pierce of Agile Tortoise [wrote the spec](http://x-callback-url.com/about/) for [x-callback-url](http://x-callback-url.com/).

For more ideas and workflows for use with Drafts check out Federico Viticci's MacStories article [iOS Automation and Workflows with Drafts](http://www.macstories.net/reviews/ios-automation-and-workflows-with-drafts/). Agile Tortoise also maintains their own [Drafts Actions Directory](http://actions.getdrafts.com/)

## Table of Contents

1. [URL Scheme](#url-scheme)
1. [Launch Center Pro Actions](#launch-center-pro-actions)
    1. [Clipboard Actions](#clipboard-actions)
    1. [Prompt Actions](#prompt-actions)
1. [Drafts Actions](#drafts-actions)
    1. [Dropbox Actions](#dropbox-actions)
1. [Mr. Reader Services](#mr-reader-services)
    1. [Other App Services](#other-app-services)
1. [Bookmarklets](#bookmarklets)
    1. [Generic](#generic)
    1. [Google Chrome](#google-chrome)
    1. [Dolphin](#dolphin)
    1. [iCab Mobile](#icab-mobile)
    1. [Mercury](#mercury)
1. [Additional Ideas](#additional-ideas)

---

## URL Scheme

### Drafts for iPad

    drafts://
    x-drafts-for-ipad://

### Drafts for iPhone

    drafts://
    x-drafts://

### Create

    drafts://
        x-callback-url/
            create?
                text
                &action
                &x-success
                &x-error
        
    Example:
    	drafts://x-callback-url/create?text=Drafts%20rocks&action=Append%20to%20Scratch

Documentation: [Official: Drafts for Developers](http://agiletortoise.com/drafts-developers/) • [handleOpenURL](http://handleopenurl.com/scheme/drafts) • [App Lookup](http://applookup.com/App/502385074)

[Table of Contents ↩](#table-of-contents)

---

## Launch Center Pro Actions

### Clipboard Actions

#### Create a new Draft with \[clipboard\]

    drafts://x-callback-url/create?text=[clipboard]

#### Append \[clipboard\] to Scratch via Drafts

    drafts://x-callback-url/create?text=[clipboard]&action=Append%20to%20Scratch

*See the [Append to Scratch](#append-to-scratch) Dropbox Action below.*

### Prompt Actions

#### Create a new Draft with \[Prompt\]

    drafts://x-callback-url/create?text=[prompt]

#### Append \[Prompt\] to Scratch via Drafts

    drafts://x-callback-url/create?text=[prompt]&action=Append%20to%20Scratch

[Table of Contents ↩](#table-of-contents)

---

## Drafts Actions

### Dropbox Actions

#### Append to Scratch

I keep a [Folding Text](http://www.foldingtext.com/) file named Scratch.ft open on my Mac at all times for quickly copy and pasting text, running timers, creating lists or working with whatever other temporary text is needed at the moment. A lot of people use a workflow like this but may use other filenames and formats and I encourage you to use it as a starting point and to customize it to fit the way you work. 

In this case you can change the *Predefined* *File* name and extension (*Ext*) to match your preferred plaintext file such as temp.md, inbox.txt or todo.taskpaper. Customize the location by changing the *Path*.

    Name: Append to Scratch
    Path:/Drafts/
    File: Predefined:
        Scratch
    Ext: ft
    Write: Append
    Template:
        
        
        ---
        
        [[draft]]
        
        [[time_log]]

I like having two line breaks before the horizontal rule before the appended text so appending multiple drafts shows up like this:

> Whatever's already in the file. For instance, I leave an Append heading at the end of the file so I can quickly *fold* everything I've added to the file from Drafts.
>
> \# Append
> 
> 
> ---
> 
> My first draft
> 
> February 11, 2013, 10:33:59 AM MST
> 
> 
> ---
> 
> My second draft
> 
> February 12, 2013, 11:45:32 AM MST

This is also easy to change, especially since Drafts will take care of the URL encoding for you.

~~[Install Action](drafts://x-callback-url/import_action?type=dropbox&name=Append%20to%20Scratch&path=%2FDrafts%2F&filenametype=2&filename=Scratch&ext=ft&writetype=2&template=%0A%0A---%0A%0A%5B%5Bdraft%5D%5D%0A%0A%5B%5Btime_long%5D%5D) • [Help](guide.md#installing-drafts-actions)~~ • Copy & paste this URL into the location bar:

    drafts://x-callback-url/import_action?type=dropbox&name=Append%20to%20Scratch&path=%2FDrafts%2F&filenametype=2&filename=Scratch&ext=ft&writetype=2&template=%0A%0A---%0A%0A%5B%5Bdraft%5D%5D%0A%0A%5B%5Btime_long%5D%5D

[Table of Contents ↩](#table-of-contents)

---

## Mr. Reader Services

### Other App Services

#### Send to Drafts (Official)

    App Name: Drafts
    Protocol: drafts:
    URL Scheme Template:

        drafts://x-calback-url/create?text={[TITLE]
        
        [URL]
        
        [TEXT-SELECTED]}
    
    Visibility:
        Standard Menu: On
        Text Selection Menu: On
        Link Menu: On

Note: This service is built into Mr. Reader. I've included it here for completeness and as an example.

[Download Service](https://github.com/christopherdwhite/iosWorkflows/raw/master/mrreader-services/drafts.mrreaderappconf) • [Help](guide.md#installing-mr-reader-browser-and-other-app-services)

#### Append to Scratch via Drafts

    App Name: Drafts
    Protocol: drafts:
    URL Scheme Template:

        drafts://x-calback-url/create?text={[TITLE]
        
        [URL]
        
        [TEXT-SELECTED]}&action=Append%20to%20Scratch&x-success=mrreader://
    
    Visibility:
        Standard Menu: On
        Text Selection Menu: On
        Link Menu: On

Note: This service is built into Mr. Reader. I've included it here for completeness and as an example.

[Download Service](https://github.com/christopherdwhite/iosWorkflows/raw/master/mrreader-services/append-to-scratch-via-drafts.mrreaderappconf) • [Help](guide.md#installing-mr-reader-browser-and-other-app-services)

[Table of Contents ↩](#table-of-contents)

---

## Bookmarklets

Important Note: Bookmarklets that take advantage of your text selection work differently or don't work at all in different browsers. Please see the guide for [further details and workarounds](guide.md#bookmarklet-limitations-for-selected-text-in-different-browsers).

### Generic

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

#### Append to Scratch via Drafts

```javascript
javascript:if(window.getSelection()!=''){var%20selected=encodeURIComponent(window.getSelection());var%20selected='%250A%250A%253E%2520'+selected.replace(/%250A/g,'%250A%253E%2520');}else{var%20selected='';}location.href='drafts://x-callback-url/create?'+'text='+'['+encodeURIComponent(document.title)+']('+encodeURIComponent(location.href)+')'+selected+'&action='+'Append%20to%20Scratch'+'&x-success='+encodeURIComponent(location.href);
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
    + '&action=' + 'Append%20to%20Scratch'
    + '&x-success=' + encodeURIComponent(location.href);
```

### Safari

#### Append to Scratch via Drafts & Return to Safari

```javascript
javascript:if(window.getSelection()!=''){var%20selected=encodeURIComponent(window.getSelection());var%20selected='%250A%250A%253E%2520'+selected.replace(/%250A/g,'%250A%253E%2520');}else{var%20selected='';}location.href='drafts://x-callback-url/create?'+'text='+'['+encodeURIComponent(document.title)+']('+encodeURIComponent(location.href)+')'+selected+'&action='+'Append%20to%20Scratch';
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
    + '&action=' + 'Append%20to%20Scratch';
```

### Google Chrome

#### Append to Scratch via Drafts & Return to Chrome

```javascript
javascript:if(window.getSelection()!=''){var%20selected=encodeURIComponent(window.getSelection());var%20selected='%250A%250A%253E%2520'+selected.replace(/%250A/g,'%250A%253E%2520');}else{var%20selected='';}location.href='drafts://x-callback-url/create?'+'text='+'['+encodeURIComponent(document.title)+']('+encodeURIComponent(location.href)+')'+selected+'&action='+'Append%20to%20Scratch'+'&x-success='+'googlechrome://';
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
    + '&action=' + 'Append%20to%20Scratch'
    + '&x-success=' + 'googlechrome://';
```

### Dolphin

#### Append to Scratch via Drafts & Return to Dolphin

```javascript
javascript:if(window.getSelection()!=''){var%20selected=encodeURIComponent(window.getSelection());var%20selected='%250A%250A%253E%2520'+selected.replace(/%250A/g,'%250A%253E%2520');}else{var%20selected='';}location.href='drafts://x-callback-url/create?'+'text='+'['+encodeURIComponent(document.title)+']('+encodeURIComponent(location.href)+')'+selected+'&action='+'Append%20to%20Scratch'+'&x-success='+'dolphin://';
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
    + '&action=' + 'Append%20to%20Scratch'
    + '&x-success=' + 'dolphin://';
```

### iCab Mobile

#### Append to Scratch via Drafts & Return to iCab Mobile

```javascript
javascript:if(window.getSelection()!=''){var%20selected=encodeURIComponent(window.getSelection());var%20selected='%250A%250A%253E%2520'+selected.replace(/%250A/g,'%250A%253E%2520');}else{var%20selected='';}location.href='drafts://x-callback-url/create?'+'text='+'['+encodeURIComponent(document.title)+']('+encodeURIComponent(location.href)+')'+selected+'&action='+'Append%20to%20Scratch'+'&x-success='+'x-icabmobile://';
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
    + '&action=' + 'Append%20to%20Scratch'
    + '&x-success=' + 'x-icabmobile://';
```

### Mercury

#### Append to Scratch via Drafts & Return to Mercury

```javascript
javascript:if(window.getSelection()!=''){var%20selected=encodeURIComponent(window.getSelection());var%20selected='%250A%250A%253E%2520'+selected.replace(/%250A/g,'%250A%253E%2520');}else{var%20selected='';}location.href='drafts://x-callback-url/create?'+'text='+'['+encodeURIComponent(document.title)+']('+encodeURIComponent(location.href)+')'+selected+'&action='+'Append%20to%20Scratch'+'&x-success='+'merc://'+encodeURIComponent(location.href);
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
    + '&action=' + 'Append%20to%20Scratch'
    + '&x-success=' + 'merc://' + encodeURIComponent(location.href);
```

[Table of Contents ↩](#table-of-contents)

---

## Additional Ideas

I'm brimming with Drafts ideas, between Drafts flexibility with URL and Dropbox actions and its fantastic x-callback-url implementation the possibilities are endless. This will definitely be one of the most updated app workflows page, stay tuned!

[Table of Contents ↩](#table-of-contents)
