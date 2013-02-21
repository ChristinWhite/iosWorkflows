# Bookmarklets for App Interactions

## Safari (Generic)

#### Search App Store for Selection

```
javascript:if(navigator.userAgent.match(/(iPhone|iPod|iPad)/i)){location.href='itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(window.getSelection());}else{location.href='http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(window.getSelection());}
```

#### Search App Store for for...? Prompt

```
javascript:var%20search=window.prompt('Search%20App%20Store%20for...');if(navigator.userAgent.match(/(iPhone|iPod|iPad)/i)){location.href='itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(search);}else{location.href='http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(search);}
```

## Safari (iOS)

#### Open in Chrome & Return to Safari
  
```
javascript:window.location='googlechrome-x-callback://x-callback-url/open/?url='+encodeURIComponent(location.href)+'&x-source=Safari&x-success='+encodeURIComponent(location.href);
```

---

## Things (Generic)

#### Create Things Task with Timestamp ([semi-official](https://culturedcode.com/forums/read.php?8,48550,49622#msg-49622))

```
javascript:window.location='things:add?title='+escape(document.title)+'&notes=Visited%20on%20'+new%20Date().toDateString()+':%20'+escape(document.URL)
```

#### Create Things Task

```
javascript:if(window.getSelection()!=''){var%20selected=encodeURIComponent(window.getSelection());var%20selected='%250A%250A%253E%2520'+selected.replace(/%250A/g,'%250A%253E%2520');}else{var%20selected='';}location.href='things:add?title='+encodeURIComponent(document.title)+'&notes='+encodeURIComponent(location.href)+selected;
```

Expanded:

```
javascript:

if (window.getSelection() != '') {
    var selected = encodeURIComponent(window.getSelection());
    var selected = '%250A%250A%253E%2520' + selected.replace(/%250A/g,'%250A%253E%2520');
} else if {
    var selected='';
}
    
    location.href = 'things:add?title=' + encodeURIComponent(document.title) + '&notes=' + encodeURIComponent(location.href) + selected;
```


# Bookmarklets for Web Interactions

## Google Cache & Coral Cache

#### Lookup Website via Google Cache

```
javascript:location.href='http:/webcache.googleusercontent.com/search?q=cache:'+window.location.href
```

#### Avoid GEO-Restrictions via Coral Cache

```
javascript:void((function(){location.href=location.href.replace(/^http%5C:%5C/%5C/([^%5C/%5C@]+)%5C/(?:)/,'http://'+'$1'.replace('%5C:','.')+'.nyud.net/');})())
```

---

## Bit.ly

#### Shorten URL with Bit.ly

```
javascript:(function()%20%7B%20var%20s%20=%20document.createElement(%22script%22);%20s.setAttribute(%22id%22,%20%22bitmark_js%22);%20s.setAttribute(%22type%22,%20%22text/javascript%22);%20s.setAttribute(%22src%22,%20%22//bitly.com/a/bitmarklet.js%22);%20(top.document.body%20%7C%7C%20top.document.getElementsByTagName(%22head%22)[0]).appendChild(s);%20%7D)();
```

---

## Search Site

#### Add a Search Box to the current Website

```
javascript:(function(){void(q=prompt('What are you looking for?',''));if(q)location.href='http://www.google.com/search?q=site%3A'+document.domain.replace('www.','')+'%20'+escape(q)})()
```

---

## Send To & Social Sharing

#### Bookmark on Pinboard

```
javascript:q=location.href;if(document.getSelection)%7Bd=document.getSelection();%7Delse%7Bd='';%7D;p=document.title;void(open('https://pinboard.in/add?url='+encodeURIComponent(q)+'&description='+encodeURIComponent(d)+'&title='+encodeURIComponent(p),'Pinboard',%20'toolbar=no,width=700,height=350'));
```

#### Send to Pocket

```
javascript:(function(){ISRIL_H='97ca';PKT_D='getpocket.com';ISRIL_SCRIPT=document.createElement('SCRIPT');ISRIL_SCRIPT.type='text/javascript';ISRIL_SCRIPT.src='http://'+PKT_D+'/b/r.js';document.getElementsByTagName('head')[0].appendChild(ISRIL_SCRIPT)})();
```

#### Send to Kindle

```
javascript:(%28function%28%29%7Bwindow.baseUrl%3D%27http%3A//www.readability.com%27%3Bwindow.readabilityToken%3D%27%27%3Bvar%20s%3Ddocument.createElement%28%27script%27%29%3Bs.setAttribute%28%27type%27%2C%27text/javascript%27%29%3Bs.setAttribute%28%27charset%27%2C%27UTF-8%27%29%3Bs.setAttribute%28%27src%27%2CbaseUrl%2B%27/bookmarklet/send-to-kindle.js%27%29%3Bdocument.documentElement.appendChild%28s%29%3B%7D%29%28%29)
```

#### Share on Twitter

```
javascript:(function()%7Bwindow.twttr=window.twttr%7C%7C%7B%7D;var%20D=550,A=450,C=screen.height,B=screen.width,H=Math.round((B/2)-(D/2)),G=0,F=document,E;if(C%3EA)%7BG=Math.round((C/2)-(A/2))%7Dwindow.twttr.shareWin=window.open('http://twitter.com/share','','left='+H+',top='+G+',width='+D+',height='+A+',personalbar=0,toolbar=0,scrollbars=1,resizable=1');E=F.createElement('script');E.src='http://platform.twitter.com/bookmarklets/share.js?v=1';F.getElementsByTagName('head')%5B0%5D.appendChild(E)%7D());
```

#### Share on Pinterest

```
javascript:void((function()%7Bvar%20e=document.createElement('script');e.setAttribute('type','text/javascript');e.setAttribute('charset','UTF-8');e.setAttribute('src','http://assets.pinterest.com/js/pinmarklet.js?r='+Math.random()*99999999);document.body.appendChild(e)%7D)());
```

#### Share on Tumblr

```
javascript:var%20d=document,w=window,e=w.getSelection,k=d.getSelection,x=d.selection,s=(e?e():(k)?k():(x?x.createRange().text:0)),f='http://www.tumblr.com/share',l=d.location,e=encodeURIComponent,p='?v=3&u='+e(l.href)%20+'&t='+e(d.title)%20+'&s='+e(s),u=f+p;try%7Bif(!/%5E(.*%5C.)?tumblr%5B%5E.%5D*$/.test(l.host))throw(0);tstbklt();%7Dcatch(z)%7Ba%20=function()%7Bif(!w.open(u,'t','toolbar=0,resizable=0,status=1,width=450,height=430'))l.href=u;%7D;if(/Firefox/.test(navigator.userAgent))setTimeout(a,0);else%20a();%7Dvoid(0)
```

---

## Save as PDF

#### Save current Website as PDF

```
javascript:void(window.open('http://www.web2pdfconvert.com/convert.aspx?cURL='+escape(location.href)))
```

---

## Reading

#### Instapaper Text

```
javascript:function%20iptxt(){var%20d=document;try{if(!d.body)throw(0);window.location='http://www.instapaper.com/text?u='+encodeURIComponent(d.location.href);}catch(e){alert('Please%20wait%20until%20the%20page%20has%20loaded.');}}iptxt();void(0)
```

#### Lookup Word at term.ly

```
javascript:javascript:%20function%20getSelText()%20%7Bvar%20txt%20=%20%27%27;if%20(window.getSelection)%20%7Btxt%20=%20window.getSelection();%7D%20else%20if(document.getSelection)%20%7Btxt%20=%20document.getSelection();%7D%20else%20if(document.selection)%20%7Btxt%20=%20document.selection.createRange().text;%7D%20else%20return%20%27%27;return%20txt;%7D;var%20q%20=%20getSelText();if%20(q%20!=%20%27%27)%20%7Bvar%20load%20=%20window.open(%27http://term.ly/%27%20+%20escape(q));%7Delse%20%7Balert(%22No%20text%20selected.%22);%7D
```

---

## Web Developement

#### Firebug

```
javascript:(function(F,i,r,e,b,u,g,L,I,T,E)%7Bif(F.getElementById(b))return;E=F%5Bi+'NS'%5D&&F.documentElement.namespaceURI;E=E?F%5Bi+'NS'%5D(E,'script'):F%5Bi%5D('script');E%5Br%5D('id',b);E%5Br%5D('src',I+g+T);E%5Br%5D(b,u);(F%5Be%5D('head')%5B0%5D%7C%7CF%5Be%5D('body')%5B0%5D).appendChild(E);E=new%20Image;E%5Br%5D('src',I+L);%7D)(document,'createElement','setAttribute','getElementsByTagName','FirebugLite','4','firebug-lite.js','releases/lite/latest/skin/xp/sprite.png','https://getfirebug.com/','%23startOpened');
```

#### View Source Code

By [joaocolombo](https://gist.github.com/joaocolombo/2920678).

```
javascript:(function(document) { window.open('data:text/html;charset=utf-8,' + encodeURIComponent(' <!doctype html> <head> <meta name="viewport" content="width=device-width, initial-scale=1.0"> <link href="http://google-code-prettify.googlecode.com/svn/trunk/src/prettify.css" type="text/css" rel="stylesheet" /> <style> pre.prettyprint { padding: 0; border: none; } </style> <script src="http://google-code-prettify.googlecode.com/svn/trunk/src/prettify.js" type="text/javascript"></script> <script src="http://jsbeautifier.org/beautify-html.js"></script> <script> document.title = "Source Code of ' + window.location + '"; window.onload = function() { var source = document.getElementById("source"); source.innerText = style_html(source.innerText); prettyPrint(); } </script> </head> <body> <pre class="prettyprint"><code class="language-html" id="source">' + document.documentElement.innerHTML.replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;") + '</code></pre> </body> </html>')); }(document));
```

#### Lookup Font Usage

```
javascript:(function()%7Bdocument.body.appendChild(document.createElement('scr'+'ipt')).setAttribute('src',%20'http://chengyinliu.com/wf.js')%7D)();
```