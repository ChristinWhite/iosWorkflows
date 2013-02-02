# Bang On

## URL Scheme

    bang-on://
    bang-on://?q=

## Bookmarklet: Launch (Official)

```javascript
javascript:location.href='bang-on://'+location.href
```

## Bookmarklet: Search for Selection

```javascript
javascript:location.href='bang-on://?q='+encodeURIComponent(window.getSelection())
```

## Reference

I was curious why the developer @kepner added the '+location.href' to his bookmarklet and I wanted to double check the URL scheme.

@chrisWhite:

> @kepner I’m digging through the Bang On URL scheme & bookmarklet, does the ‘+location.href’ part do anything? Seems like it’s not used.

> @kepner bang-on:// to launch, bang-on://?q= to search, am I missing anything? Thanks!

[Tweet 1](http://twitter.com/chrisWhite/status/296695444908695554) & [Tweet 2](http://twitter.com/chrisWhite/status/296695857393315841)

@kepner's [reply:](https://twitter.com/kepner/status/296825551887429632)

> @chrisWhite That´s it. The bookmark is designed to preserve your search query after launching Bang On, which is why it grabs location.href.