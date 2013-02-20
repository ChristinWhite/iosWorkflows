# Bookmarklets

## Safari (Generic)

#### Search App Store for Selection

```
javascript:if(navigator.userAgent.match(/(iPhone|iPod|iPad)/i)){location.href='itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(window.getSelection());}else{location.href='http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(window.getSelection());}
```

This bookmarklet also works on OS X (& probably Windows, haven't tested it yet).

#### Search App Store for for...? Prompt

```
javascript:var%20search=window.prompt('Search%20App%20Store%20for...');if(navigator.userAgent.match(/(iPhone|iPod|iPad)/i)){location.href='itms-apps://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(search);}else{location.href='http://phobos.apple.com/WebObjects/MZSearch.woa/wa/search?media=software&term='+encodeURIComponent(search);}
```

## Safari (iOS)

#### Open in Chrome & Return to Safari
  
```
javascript:window.location='googlechrome-x-callback://x-callback-url/open/?url='+encodeURIComponent(location.href)+'&x-source=Safari&x-success='+encodeURIComponent(location.href);
```


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


## Google Cache

#### Lookup Website via Google Cache

```
javascript:location.href='http:/webcache.googleusercontent.com/search?q=cache:'+window.location.href
```


## Coral Cache

#### Avoid GEO-Restrictions via Coral Cache

```
javascript:void((function(){location.href=location.href.replace(/^http%5C:%5C/%5C/([^%5C/%5C@]+)%5C/(?:)/,'http://'+'$1'.replace('%5C:','.')+'.nyud.net/');})())
```


## Bit.ly

#### Shorten URL with Bit.ly

```
javascript:(function()%20%7B%20var%20s%20=%20document.createElement(%22script%22);%20s.setAttribute(%22id%22,%20%22bitmark_js%22);%20s.setAttribute(%22type%22,%20%22text/javascript%22);%20s.setAttribute(%22src%22,%20%22//bitly.com/a/bitmarklet.js%22);%20(top.document.body%20%7C%7C%20top.document.getElementsByTagName(%22head%22)[0]).appendChild(s);%20%7D)();
```


## Search Site

#### Add a Search Box to the current Website

```
javascript:(function(){void(q=prompt('What are you looking for?',''));if(q)location.href='http://www.google.com/search?q=site%3A'+document.domain.replace('www.','')+'%20'+escape(q)})()
```


## Kindle

#### Send to Kindle

```
javascript:(%28function%28%29%7Bwindow.baseUrl%3D%27http%3A//www.readability.com%27%3Bwindow.readabilityToken%3D%27%27%3Bvar%20s%3Ddocument.createElement%28%27script%27%29%3Bs.setAttribute%28%27type%27%2C%27text/javascript%27%29%3Bs.setAttribute%28%27charset%27%2C%27UTF-8%27%29%3Bs.setAttribute%28%27src%27%2CbaseUrl%2B%27/bookmarklet/send-to-kindle.js%27%29%3Bdocument.documentElement.appendChild%28s%29%3B%7D%29%28%29)
```


## Save as PDF

#### Save current Website as PDF

```
javascript:void(window.open('http://www.web2pdfconvert.com/convert.aspx?cURL='+escape(location.href)))
```