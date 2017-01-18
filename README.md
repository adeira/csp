This **package is deprecated** because CSP support has been added to the **nette/http** package in [this pull request](https://github.com/nette/http/pull/115). This package will be hardly deprecated after new version of package **nette/http** will be released.

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

Yeah that's right - you don't have to register special extension, because it's already in Nette  Framework. But for now (if you don't have this new version yet) you can use this package as sort of polyfill:

# Content Security Policy for Nette Framework

[![Build Status](https://travis-ci.org/adeira/csp.svg?branch=master)](https://travis-ci.org/adeira/csp)

Please read this:
- https://www.w3.org/TR/CSP/
- http://content-security-policy.com/
- https://developer.mozilla.org/en-US/docs/Web/Security/CSP/CSP_policy_directives

This library introduces simple CSP extension for DIC which help you to secure your application:

```
extensions:
  csp: Adeira\ContentSecurityPolicyExtension
```

There are a lot of configuration options. These are the default ones:

```
csp:
  enabled: yes
  report-only: no
  default-src: self
  script-src: * unsafe-inline unsafe-eval
  style-src: * unsafe-inline
  img-src: self data:
  connect-src: self
  font-src: *
  object-src: *
  media-src: *
  report-uri: NULL
  child-src: *
  form-action: self
  frame-ancestors: self
```

You can also use arrays in configuration:

```
csp:
  default-src: self
  script-src:
    - *
    - unsafe-inline
    - unsafe-eval
```

If enabled, it will send `Content-Security-Policy` or `Content-Security-Policy-Report-Only` header in `report-only` mode. You can setup whatever values you want in config. `report-uri` should be relative URL:

```
csp:
	report-uri: api/v1/csp_report
```

And remember, you can use `report-only` mode only if there is `report-uri` specified.
