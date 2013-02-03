# Things

## URL Scheme

    things:
    things:add?title=Buy%20milk&notes=Low%20fat&dueDate=2010-12-24

Things doesn't like to be launched, it expects you to define a new task and when one isn´t found you get an error alert. Support for URL schemes with Things is limited, as is documentation. There doesn't seem to be a way to include tags or anything else beyond Name, Notes & dueDate. Also note that Things tasks must have a name so make sure you include it all of your workflow.

Strangely, Things also doesn't use the typical AppName:// syntax, including the '//' doesn't work. I'm guessing this might be a leftover from the Mac app's URL scheme but it's just a guess.

As far as documentation goes there is a [forum post](https://culturedcode.com/forums/read.php?8,48550,49212#msg-49212) that gives the above example but that´s pretty much it. An official developer page may or may not be coming <strike>soon</strike> ever.

## Bookmarklet: Create Things Task with Timestamp ([semi-official](https://culturedcode.com/forums/read.php?8,48550,49622#msg-49622))

```javascript
Javascript:window.location='things:add?title='+escape(document.title)+'&notes=Visited%20on%20'+new%20Date().toDateString()+':%20'+escape(document.URL)
```

## Bookmarklet: Create Things Task

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