This **package is deprecated** because CSP support has been added to the **nette/http** package in [version 2.4.4](https://github.com/nette/http/releases/tag/v2.4.4)...

**Nette/http** package does have very similar syntax and additionally it support [nonces](https://www.websec.be/blog/cspstrictdynamic/#fixing-broken-whitelists). Here is the future syntax:

```yaml
http:
    csp:
        default-src: "'self' https://example.com"
        upgrade-insecure-requests:
        script-src: 'nonce'
        style-src:
            - self
            - https://example.com
```

Yeah that's right - you don't have to register special extension, because it's already in Nette Framework. Please read more about nonce support in [Nette Framework forum](https://forum.nette.org/en/27918-nette-framework-2-4-2017-01-19#p183884).
