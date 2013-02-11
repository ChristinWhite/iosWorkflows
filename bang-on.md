# Bang On

[Official Site](http://kepner.me/apps/) • [iTunes Link](https://itunes.apple.com/us/app/bang-on-a-nice-search-app/id521507324?mt=8)

## URL Scheme

### Function

    bang-on://
        bang-on://?q=
            bang-on://?q=Twitter

[App Lookup](http://applookup.com/App/521507324)

---

## Bookmarklets

### Generic (Safari)

#### Launch Bang On (Official)

```javascript
javascript:location.href='bang-on://'+location.href
```

#### Search Bang On for Selection

```javascript
javascript:location.href='bang-on://?q='+encodeURIComponent(window.getSelection())
```

#### Search Bang On for Selection with specific !bang

```javascript
javascript:location.href='bang-on://?q='+encodeURIComponent(window.getSelection())+'%20'+'!bang'
```

Just replace *!bang* with the !bang you'd like to hard code into the bookmarklet.

