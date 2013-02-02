# Bang On

## URL Scheme

    bang-on://
    bang-on://?q=

## Bookmarklet: Launch (Official)

```javascript
javascript:location.href='bang-on://'+location.href
```

Note: I tweeted the developer @kepner about what the +location.href does, here's [his reply](https://twitter.com/kepner/status/296825551887429632)

> @chrisWhite That´s it. The bookmark is designed to preserve your search query after launching Bang On, which is why it grabs location.href.

## Bookmarklet: Search for Selection

```javascript
    javascript:location.href='bang-on://?q='+encodeURIComponent(window.getSelection())
```