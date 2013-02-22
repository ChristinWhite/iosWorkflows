# Bookmarklets

A summary and collection of iosWorkflows bookmarklets and web bookmarklets to increase your productivity.

**Important Note:** Bookmarklets that take advantage of your text selection work differently or don't work at all in different browsers. Please see the guide for [further details and workarounds](guide.md#bookmarklet-limitations-for-selected-text-in-different-browsers).


## Table of Contents

1. [App Interactions](#app-interactions)
    1. [1Password](#1password)
    1. [Bang On](#bang-on)
    1. [Drafts](#drafts)
    1. [Google Chrome](#google-chrome)
    1. [Pinbook](#pinbook)
    1. [Safari](#safari)
    1. [Things](#things)
1. [Web Interactions](#web-interactions)
    1. [Bit.ly](#bitly)
    1. [Google Cache & Coral Cache](#google-cache--coral-cache)
    1. [Reading](#reading)
    1. [Save as PDF](#save-as-pdf)
    1. [Search Site](#search-site)
    1. [Send To & Social Sharing](#send-to-social-sharing)
    1. [Web Development](#web-development)
    
---

# App Interactions

## 1Password

### Open in 1Password

```javascript
javascript:window.location='op'+(window.location.href);
```

From the MacStories [post about 1Password 4.1](http://www.macstories.net/links/1password-4-1/).

### Search 1Password for Selection

```javascript
javascript:location.href='onepassword://search/'+encodeURIComponent(window.getSelection());
```

### Search 1Password for...? Prompt

```javascript
javascript:var%20search=window.prompt('Search%201Password%20for...');location.href='onepassword://search/'+encodeURIComponent(search);
```

### Search 1Password for...? If Empty Search for Domain

```javascript
javascript:var%20search=window.prompt('Search%201Password%20for...');if(search==''){var%20search=document.domain;if(search.substring(0,4)=='www.'){search=search.substring(4);}}location.href='onepassword://search/'+encodeURIComponent(search);
```

Expanded:

```javascript
var search = window.prompt('Search%201Password%20for...');

if (search == '') {

    var search = document.domain;

    if (search.substring(0,4) == 'www.') {
        search = search.substring(4);
    }
} 

location.href = 'onepassword://search/' + encodeURIComponent(search);
```

[Table of Contents ↩](#table-of-contents)

---

## Bang On

### Launch Bang On (Official)

```javascript
javascript:location.href='bang-on://'+location.href
```

### Search Bang On for Selection

```javascript
javascript:location.href='bang-on://?q='+encodeURIComponent(window.getSelection())
```

### Search Bang On for Selection with a specific !bang

```javascript
javascript:location.href='bang-on://?q='+encodeURIComponent(window.getSelection())+'%20'+'!bang'
```

Just replace *!bang* with the !bang you'd like to hard code into the bookmarklet.

[Table of Contents ↩](#table-of-contents)

---

## Drafts

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

### Safari: Append to Scratch via Drafts & Return to Safari

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

### Chrome: Append to Scratch via Drafts & Return to Chrome

```javascript
javascript:if(window.getSelection()!=''){var%20selected=encodeURIComponent(window.getSelection());var%20selected='%250A%250A%253E%2520'+selected.replace(/%250A/g,'%250A%253E%2520');}else{var%20selected='';}location.href='drafts://x-callback-url/create?'+'text='+'['+encodeURIComponent(document.title)+']('+encodeURIComponent(location.href)+')'+selected+'&action='+'Append%20to%20Scratch'+'&x-success='+'googlechrome://://';
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
    + '&x-success=' + 'googlechrome://://';
```

[Table of Contents ↩](#table-of-contents)

---

## Google Chrome

### Open in Google Chrome (by [Jon Abrams](http://blog.jonabrams.com/post/26099585134/open-in-chrome))

```javascript
javascript:location.href="googlechrome"+location.href.substring(4);
```

[Table of Contents ↩](#table-of-contents)

---

## Pinbook

### Open in Pinbook

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&description='+encodeURIComponent(window.getSelection());
```

### Open in Pinbook (Private)

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&private=yes'+'&description='+encodeURIComponent(window.getSelection());
```

### Read Later in Pinbook

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&description='+encodeURIComponent(window.getSelection());
```

### Read Later in Pinbook (Private)

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&private=yes'+'&description='+encodeURIComponent(window.getSelection());
```

### Chrome: Open in Pinbook & Return to Chrome

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&description='+encodeURIComponent(window.getSelection())+'&x-success=googlechrome://'+'&x-cancel=googlechrome://';
```

### Chrome: Open in Pinbook (Private) & Return to Chrome

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&private=yes'+'&description='+encodeURIComponent(window.getSelection())+'&x-success=googlechrome://'+'&x-cancel=googlechrome://';
```

### Chrome: Read Later in Pinbook & Return to Chrome

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&description='+encodeURIComponent(window.getSelection())+'&x-success=googlechrome://'+'&x-cancel=googlechrome://';
```

### Chrome: Read Later in Pinbook (Private) & Return to Chrome

```javascript
javascript:location.href='pinbook://x-callback-url/add?'+'url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)+'&readlater=yes'+'&private=yes'+'&description='+encodeURIComponent(window.getSelection())+'&x-success=googlechrome://'+'&x-cancel=googlechrome://';
```

[Table of Contents ↩](#table-of-contents)

---

## Safari

### Search App Store for Selection

```javascript
javascript:if(navigator.userAgent.match(/(iPhone|iPod|iPad)/i)){location.href='itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(window.getSelection());}else{location.href='http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(window.getSelection());}
```

### Search App Store for for...? Prompt

```javascript
javascript:var%20search=window.prompt('Search%20App%20Store%20for...');if(navigator.userAgent.match(/(iPhone|iPod|iPad)/i)){location.href='itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(search);}else{location.href='http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(search);}
```

### Open in Chrome & Return to Safari
  
```javascript
javascript:window.location='googlechrome-x-callback://x-callback-url/open/?url='+encodeURIComponent(location.href)+'&x-source=Safari&x-success='+encodeURIComponent(location.href);
```

[Table of Contents ↩](#table-of-contents)

---

## Things

### Create Things Task with Timestamp ([semi-official](https://culturedcode.com/forums/read.php?8,48550,49622#msg-49622))

```javascript
javascript:window.location='things:add?title='+escape(document.title)+'&notes=Visited%20on%20'+new%20Date().toDateString()+':%20'+escape(document.URL)
```

### Create Things Task

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

[Table of Contents ↩](#table-of-contents)

---

# Web Interactions

## Bit.ly

### Shorten URL with Bit.ly

```javascript
javascript:(function()%20%7B%20var%20s%20=%20document.createElement(%22script%22);%20s.setAttribute(%22id%22,%20%22bitmark_js%22);%20s.setAttribute(%22type%22,%20%22text/javascript%22);%20s.setAttribute(%22src%22,%20%22//bitly.com/a/bitmarklet.js%22);%20(top.document.body%20%7C%7C%20top.document.getElementsByTagName(%22head%22)[0]).appendChild(s);%20%7D)();
```

[Table of Contents ↩](#table-of-contents)

---

## Google Cache & Coral Cache

### Lookup Website via Google Cache

```javascript
javascript:location.href='http:/webcache.googleusercontent.com/search?q=cache:'+window.location.href
```

### Avoid GEO-Restrictions via Coral Cache

```javascript
javascript:void((function(){location.href=location.href.replace(/^http%5C:%5C/%5C/([^%5C/%5C@]+)%5C/(?:)/,'http://'+'$1'.replace('%5C:','.')+'.nyud.net/');})())
```

[Table of Contents ↩](#table-of-contents)

---

## Reading

### Increase Readability via Instapaper

```javascript
javascript:function%20iptxt(){var%20d=document;try{if(!d.body)throw(0);window.location='http://www.instapaper.com/text?u='+encodeURIComponent(d.location.href);}catch(e){alert('Please%20wait%20until%20the%20page%20has%20loaded.');}}iptxt();void(0)
```

### Lookup Word Definition at term.ly

```javascript
javascript:javascript:%20function%20getSelText()%20%7Bvar%20txt%20=%20%27%27;if%20(window.getSelection)%20%7Btxt%20=%20window.getSelection();%7D%20else%20if(document.getSelection)%20%7Btxt%20=%20document.getSelection();%7D%20else%20if(document.selection)%20%7Btxt%20=%20document.selection.createRange().text;%7D%20else%20return%20%27%27;return%20txt;%7D;var%20q%20=%20getSelText();if%20(q%20!=%20%27%27)%20%7Bvar%20load%20=%20window.open(%27http://term.ly/%27%20+%20escape(q));%7Delse%20%7Balert(%22No%20text%20selected.%22);%7D
```

[Table of Contents ↩](#table-of-contents)

---

## Save as PDF

### Save current Website as PDF

```javascript
javascript:void(window.open('http://www.web2pdfconvert.com/convert.aspx?cURL='+escape(location.href)))
```

[Table of Contents ↩](#table-of-contents)

---

## Search Site

### Add a Search Box to the current Website

```javascript
javascript:(function(){void(q=prompt('What are you looking for?',''));if(q)location.href='http://www.google.com/search?q=site%3A'+document.domain.replace('www.','')+'%20'+escape(q)})()
```

[Table of Contents ↩](#table-of-contents)

---

## Send To & Social Sharing

### Bookmark on Pinboard

```javascript
javascript:q=location.href;if(document.getSelection)%7Bd=document.getSelection();%7Delse%7Bd='';%7D;p=document.title;void(open('https://pinboard.in/add?url='+encodeURIComponent(q)+'&description='+encodeURIComponent(d)+'&title='+encodeURIComponent(p),'Pinboard',%20'toolbar=no,width=700,height=350'));
```

### Bookmark on Delicious

```javascript
javascript:(function(e,t){var%20n=e.document;setTimeout(function(){function%20a(e){if(e.data==="destroy_bookmarklet"){var%20r=n.getElementById(t);if(r){n.body.removeChild(r);r=null}}}var%20t="DELI_bookmarklet_iframe",r=n.getElementById(t);if(r){return}var%20i="https://delicious.com/save?%22,s=n.createElement(%22iframe%22);s.id=t;s.src=i+%22url=%22+encodeURIComponent(e.location.href)+%22&title=%22+encodeURIComponent(n.title)+%22&note=%22+encodeURIComponent(%22%22+(e.getSelection?e.getSelection():n.getSelection?n.getSelection():n.selection.createRange().text))+%22&v=1.1%22;s.style.position=%22fixed%22;s.style.top=%220%22;s.style.left=%220%22;s.style.height=%22100%25%22;s.style.width=%22100%25%22;s.style.zIndex=%2216777270%22;s.style.border=%22none%22;s.style.visibility=%22hidden%22;s.onload=function(){this.style.visibility=%22visible%22};n.body.appendChild(s);var%20o=e.addEventListener?%22addEventListener%22:%22attachEvent%22;var%20u=o==%22attachEvent%22?%22onmessage%22:%22message%22;e[o](u,a,false)},1)})(window)
```

### Bookmark on Kippt

```javascript
javascript:(function(){var%20w=window.open('https://kippt.com/extensions/new/?url='+encodeURIComponent(document.location.href)+'&title='+encodeURIComponent(document.title)+'&source=bp1&notes='+encodeURIComponent(''+(window.getSelection?window.getSelection():document.getSelection?document.getSelection():document.selection.createRange().text)),'kippt','width=420,height=240,location=0,links=0,scrollbars=0,toolbar=0');%20if(w)setTimeout(function(){w.focus()},100);else{alert('It%20seems%20that%20you%20have%20a%20popup%20blocker.%20Please,%20hold%20the%20CTRL-key%20and%20try%20again.')}})();
```

### Send to Pocket

```javascript
javascript:(function(){ISRIL_H='97ca';PKT_D='getpocket.com';ISRIL_SCRIPT=document.createElement('SCRIPT');ISRIL_SCRIPT.type='text/javascript';ISRIL_SCRIPT.src='http://'+PKT_D+'/b/r.js';document.getElementsByTagName('head')[0].appendChild(ISRIL_SCRIPT)})();
```

### Send to Instapaper

```javascript
javascript:function%20iprl5(){var%20d=document,z=d.createElement('scr'+'ipt'),b=d.body,l=d.location;try{if(!b)throw(0);d.title='(Saving...)%20'+d.title;z.setAttribute('src',l.protocol+'//www.instapaper.com/j/?u='+encodeURIComponent(l.href)+'&t='+(new%20Date().getTime()));b.appendChild(z);}catch(e){alert('Please%20wait%20until%20the%20page%20has%20loaded.');}}iprl5();void(0)
```

### Send to Kindle

```javascript
javascript:(%28function%28%29%7Bwindow.baseUrl%3D%27http%3A//www.readability.com%27%3Bwindow.readabilityToken%3D%27%27%3Bvar%20s%3Ddocument.createElement%28%27script%27%29%3Bs.setAttribute%28%27type%27%2C%27text/javascript%27%29%3Bs.setAttribute%28%27charset%27%2C%27UTF-8%27%29%3Bs.setAttribute%28%27src%27%2CbaseUrl%2B%27/bookmarklet/send-to-kindle.js%27%29%3Bdocument.documentElement.appendChild%28s%29%3B%7D%29%28%29)
```

### Share on Facebook

```javascript
javascript:var%20d=document,f='https://www.facebook.com/share',l=d.location,e=encodeURIComponent,p='.php?src=bm&v=4&i=1361527801&u='+e(l.href)+'&t='+e(d.title);1;try{if%20(!/^(.*\.)?facebook\.[^.]*$/.test(l.host))throw(0);share_internal_bookmarklet(p)}catch(z)%20{a=function()%20{if%20(!window.open(f+'r'+p,'sharer','toolbar=0,status=0,resizable=1,width=626,height=436'))l.href=f+p};if%20(/Firefox/.test(navigator.userAgent))setTimeout(a,0);else{a()}}void(0)
```

### Share on Twitter

```javascript
javascript:(function()%7Bwindow.twttr=window.twttr%7C%7C%7B%7D;var%20D=550,A=450,C=screen.height,B=screen.width,H=Math.round((B/2)-(D/2)),G=0,F=document,E;if(C%3EA)%7BG=Math.round((C/2)-(A/2))%7Dwindow.twttr.shareWin=window.open('http://twitter.com/share','','left='+H+',top='+G+',width='+D+',height='+A+',personalbar=0,toolbar=0,scrollbars=1,resizable=1');E=F.createElement('script');E.src='http://platform.twitter.com/bookmarklets/share.js?v=1';F.getElementsByTagName('head')%5B0%5D.appendChild(E)%7D());
```

### Share on Google+

```javascript
javascript:void(window.open('https://plus.google.com/share?ur\l='+encodeURIComponent(location),%20'Share%20to%20Google+','width=600,height=460,menubar=no,location=no,status=no'));
```

### Share on Pinterest

```javascript
javascript:void((function()%7Bvar%20e=document.createElement('script');e.setAttribute('type','text/javascript');e.setAttribute('charset','UTF-8');e.setAttribute('src','http://assets.pinterest.com/js/pinmarklet.js?r='+Math.random()*99999999);document.body.appendChild(e)%7D)());
```

### Share on Tumblr

```javascript
javascript:var%20d=document,w=window,e=w.getSelection,k=d.getSelection,x=d.selection,s=(e?e():(k)?k():(x?x.createRange().text:0)),f='http://www.tumblr.com/share',l=d.location,e=encodeURIComponent,p='?v=3&u='+e(l.href)%20+'&t='+e(d.title)%20+'&s='+e(s),u=f+p;try%7Bif(!/%5E(.*%5C.)?tumblr%5B%5E.%5D*$/.test(l.host))throw(0);tstbklt();%7Dcatch(z)%7Ba%20=function()%7Bif(!w.open(u,'t','toolbar=0,resizable=0,status=1,width=450,height=430'))l.href=u;%7D;if(/Firefox/.test(navigator.userAgent))setTimeout(a,0);else%20a();%7Dvoid(0)
```

[Table of Contents ↩](#table-of-contents)

---

## Web Developement

### Firebug

```javascript
javascript:(function(F,i,r,e,b,u,g,L,I,T,E)%7Bif(F.getElementById(b))return;E=F%5Bi+'NS'%5D&&F.documentElement.namespaceURI;E=E?F%5Bi+'NS'%5D(E,'script'):F%5Bi%5D('script');E%5Br%5D('id',b);E%5Br%5D('src',I+g+T);E%5Br%5D(b,u);(F%5Be%5D('head')%5B0%5D%7C%7CF%5Be%5D('body')%5B0%5D).appendChild(E);E=new%20Image;E%5Br%5D('src',I+L);%7D)(document,'createElement','setAttribute','getElementsByTagName','FirebugLite','4','firebug-lite.js','releases/lite/latest/skin/xp/sprite.png','https://getfirebug.com/','%23startOpened');
```

### View Source Code

By [joaocolombo](https://gist.github.com/joaocolombo/2920678).

```javascript
javascript:(function(document) { window.open('data:text/html;charset=utf-8,' + encodeURIComponent(' <!doctype html> <head> <meta name="viewport" content="width=device-width, initial-scale=1.0"> <link href="http://google-code-prettify.googlecode.com/svn/trunk/src/prettify.css" type="text/css" rel="stylesheet" /> <style> pre.prettyprint { padding: 0; border: none; } </style> <script src="http://google-code-prettify.googlecode.com/svn/trunk/src/prettify.js" type="text/javascript"></script> <script src="http://jsbeautifier.org/beautify-html.js"></script> <script> document.title = "Source Code of ' + window.location + '"; window.onload = function() { var source = document.getElementById("source"); source.innerText = style_html(source.innerText); prettyPrint(); } </script> </head> <body> <pre class="prettyprint"><code class="language-html" id="source">' + document.documentElement.innerHTML.replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;") + '</code></pre> </body> </html>')); }(document));
```

### Lookup Font Usage

```javascript
javascript:(function()%7Bdocument.body.appendChild(document.createElement('scr'+'ipt')).setAttribute('src',%20'http://chengyinliu.com/wf.js')%7D)();
```

[Table of Contents ↩](#table-of-contents)