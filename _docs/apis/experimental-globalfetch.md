---
title: globalFetch API
section: webAPIs
sectionUrl: /docs/apis
sectionTitle: Web APIs
sectionSubtitle: Explore Beaker's Web APIs for reading and writing the peer-to-peer filesystem
experimental: true
---

`experimental.globalFetch` is an experimental API for making Ajax calls across origins.

This API is functionally identical to [fetch()](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) with the following caveats:

 - Contrary to  [SOP](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy), [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) is applied, so the site can send a request to any service 
 - A permission prompt is raised for each request to a new origin
 - Only HEAD and GET are supported
 - Cookies/credentials are never sent

For each new origin that the site contacts, a permission prompt will be presented to the user. This makes it possible for `dat://` websites to make cross-origin requests, while the user still has an opportunity to block the requests.

To use this API, include the following in your <a href="/docs/apis/manifest"><code>dat.json</code> manifest file</a>:

```json
{
  "experimental": {
    "apis": ["globalFetch"]
  }
}
```

{% include experimental-api-notice.html %}

## Methods

{% include api-reference.html items=site.data.apis.experimental-globalfetch.methods %}
