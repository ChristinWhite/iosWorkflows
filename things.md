# Things

Official Site: [iPad](http://culturedcode.com/things/ipad/) & [iPhone](http://culturedcode.com/things/iphone/) • iTunes Link: [iPad](http://culturedcode.com/things/ipad/appstore/) & [iPhone](http://culturedcode.com/things/iphone/appstore/)

## Table of Contents

1. [URL Scheme](#url-scheme)
1. [Launch Center Pro Actions](#launch-center-pro-actions)
    1. [Clipboard Actions](#clipboard-actions)
    1. [Prompt Actions](#prompt-actions)
1. [Drafts Actions](#drafts-actions)
    1. [URL Actions](#url-actions)
1. [Mr. Reader Services](#mr-reader-services)
    1. [Other App Services](#other-app-services)
1. [Bookmarklets](#bookmarklets)
    1. [Generic](#generic)
1. [Suggested Improvements for Developer](#suggested-improvements-for-developer)

---

## URL Scheme

### Function

    things:
        add?
            title=
            &notes=
            &dueDate=YYYY-MM-DD
        
    Example:
    	things:add?title=Buy%20milk&notes=Low%20fat&dueDate=2010-12-24

Things doesn't like to be launched, it expects you to define a new task and when one isn´t found you get an error alert. Support for URL schemes with Things is limited, as is documentation. There doesn't seem to be a way to include tags or anything else beyond Name, Notes & dueDate. Also note that Things tasks must have a name so make sure you include it all of your workflow.

Strangely, Things also doesn't use the typical AppName:// syntax, including the '//' doesn't work. I'm guessing this might be a leftover from the Mac app's URL scheme but it's just a guess.

As far as documentation goes there is a [forum post](https://culturedcode.com/forums/read.php?8,48550,49212#msg-49212) that gives the above example but that´s pretty much it. An official developer page may or may not be coming ~~soon~~ ever. The information on [App Lookup](http://applookup.com/App/284971781) also seems to be wrong.

Documentation: [Forum Post](https://culturedcode.com/forums/read.php?8,48550,49212#msg-49212) • [App Lookup](http://applookup.com/App/284971781)

[Table of Contents ↩](#table-of-contents)

---

## Launch Center Pro Actions

### Clipboard Actions

#### Create Task from \[clipboard\]

    things:add?title=[clipboard]

#### Create Task from \[clipboard\] & Note \[prompt\]

    things:add?title=[clipboard]&notes=[prompt]

#### Create Task from \[clipboard\] & Due Date \[prompt\]

    things:add?title=[clipboard]&dueDate=[prompt]

#### Create Task from \[clipboard\], Note \[prompt\] & Due Date \[prompt\]

    things:add?title=[clipboard]&notes=[prompt]&dueDate=[prompt]

### Prompt Actions

#### Create Task from \[prompt\]

    things:add?title=[prompt]

#### Create Task from \[prompt\] & Note \[clipboard\]

    things:add?title=[prompt]&notes=[clipboard]

#### Create Task from \[prompt\] & Note \[clipboard\] & Due Date \[prompt\]

    things:add?title=[prompt]&notes=[clipboard]&dueDate=[prompt]

#### Create Task from \[prompt\] & Note \[prompt\]

    things:add?title=[prompt]&notes=[prompt]

#### Create Task from \[prompt\] & Note \[prompt\] & Due Date \[prompt\]

    things:add?title=[prompt]&notes=[prompt]&dueDate=[prompt]

[Table of Contents ↩](#table-of-contents)

---

## Drafts Actions

### URL Actions

Note: Drafts has a *Send to Things* action built in that takes whatever is in your draft and sends it as the task name.

#### Send to Things with Notes

    Name: Send to Things with Notes
    URL:
        things:add?title=[[title]]&notes=[[body]]

This action will send the first line of your draft to Things as the task title and will send any following lines as the task notes.

[Install Action](drafts://x-callback-url/import_action?type=URL&name=Send%20to%20Things%20with%20Notes&url=things%3Aadd%3Ftitle%3D%5B%5Btitle%5D%5D%26notes%3D%5B%5Bbody%5D%5D) • [Help](guide.md#installing-drafts-actions)

#### Send to Things with Due Date

    Name: Send to Things with Notes
    URL:
        things:add?title=[[title]]&dueDate=[[body]]

This action will send the first line of your draft to Things as the task title and will send any following lines as the task dueDate. 

Important! To use this action your due date must be on the second line of your draft in the YYYY-MM-DD format and there must be no additional spaces, text or line breaks after following it.

This is valid:

> Write a blog post
> 2013-02-17

Each of these are invalid and Things will give you an error:

> Write a blog post
> 2013/02/17

> Write a blog post
> 2013-02-17 by 6:00PM

> Write a blog post
> 2013-02-17
> Maybe plug the iosWorkflows project

[Install Action](drafts://x-callback-url/import_action?type=URL&name=Send%20to%20Things%20with%20Due%20Date&url=things%3Aadd%3Ftitle%3D%5B%5Btitle%5D%5D%26dueDate%3D%5B%5Bbody%5D%5D) • [Help](guide.md#installing-drafts-actions)

[Table of Contents ↩](#table-of-contents)

---

## Mr. Reader Services

### Other App Services

#### Send to Things (Official)

    App Name: Things
    Protocol: things:
    URL Scheme Template:
        things:add?title={[TITLE])&notes={[URL]}
    
    Visibility:
        Standard Menu: On
        Text Selection Menu: On
        Link Menu: On

Note: This service is built into Mr. Reader. I've included it here for completeness and as an example.

[Download Service](https://github.com/christopherdwhite/iosWorkflows/raw/master/mrreader-services/things.mrreaderappconf) • [Help](guide.md#installing-mr-reader-browser-and-other-app-services)

#### Send to Things with Selection

    App Name: Things (with selection)
    Protocol: things:
    URL Scheme Template:
        things:add?title={[TITLE])&notes={[URL]}%0A%0A%3E%20{[TEXT-SELECTED]}
    
    Visibility:
        Standard Menu: Off
        Text Selection Menu: On
        Link Menu: Off

This will add the selected text in this format:

> URL
>
> \> Text Selected

[Download Service](https://github.com/christopherdwhite/iosWorkflows/raw/master/mrreader-services/things-with-selection.mrreaderappconf) • [Help](guide.md#installing-mr-reader-browser-and-other-app-services)

Since I don't want an additional two line breaks & a '\>' symbol in a task's notes when I don't have anything selected I use a combination of both of these services. To make experience a little more seamless I turn *off* the *Text Selection Menu* visibility on official service. That way I always have only the correct service show up depending on the context.

[Table of Contents ↩](#table-of-contents)

---

## Bookmarklets

Important Note: Bookmarklets that take advantage of your text selection work differently or don't work at all in different browsers. Please see the guide for [further details and workarounds](guide.md#bookmarklet-limitations-for-selected-text-in-different-browsers).

### Generic

#### Create Things Task

```javascript
javascript:if(window.getSelection()!=''){var%20selected=encodeURIComponent(window.getSelection());var%20selected='%250A%250A%253E%2520'+selected.replace(/%250A/g,'%250A%253E%2520');}else{var%20selected='';}location.href='things:add?title='+encodeURIComponent(document.title)+'&notes='+encodeURIComponent(location.href)+selected;
```

Expanded:

```javascript
javascript:

if (window.getSelection() != '') {
    var selected = encodeURIComponent(window.getSelection());
    var selected = '%250A%250A%253E%2520' + selected.replace(/%250A/g,'%250A%253E%2520');
} else if {
    var selected='';
}
    
    location.href = 'things:add?title=' + encodeURIComponent(document.title) + '&notes=' + encodeURIComponent(location.href) + selected;
```

Note: This bookmarklet also works great with Things on OS X!

#### Bookmarklet: Create Things Task with Timestamp ([semi-official](https://culturedcode.com/forums/read.php?8,48550,49622#msg-49622))

```javascript
Javascript:window.location='things:add?title='+escape(document.title)+'&notes=Visited%20on%20'+new%20Date().toDateString()+':%20'+escape(document.URL)
```

[Table of Contents ↩](#table-of-contents)

---

## Suggested Improvements for Cultured Code

1. Document the URL scheme properly.
1. Let the app be just launched (without creating a new task) for launching utilities like Launch Center Pro.
1. Standardize. things://, not things:
1. Add parameter for tags, marking something as today and filing into projects or areas.
1. Add support for dueDates in the YYYY.MM.DD format as well as the current YYYY-MM-DD so that Launch Center Pro users can use a keypad prompt instead of needing the full keyboard. YYYY/MM/DD would make sense too.
1. Add [x-callback-url](http://x-callback-url.com/) support so that a user could create a task from another app and then be returned to that app upon task completion.


[Table of Contents ↩](#table-of-contents)