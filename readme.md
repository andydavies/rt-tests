# Some Resource Timing Test Cases

Created to explore what Resource Timing information browsers provide in error cases. 

Each case attempts to load a resource, then when onload fires it checks the PerfromanceEntries for that resource.

| dns-failure.html | References an image from a domain that doesn't resolve |
| tcp-connection-failure.html | References an image from an IP that can't be connected to |
| http-404-failure.html | Referemces an image that doesn't exist |
| chrome-resource-timing-error.html | **Redundant** was created to reproduce an error in Chrome but other failures will produce it too |

## TODO

More test cases are needed for example:

- Original cases with cross-domain that has TAO header
- Mixed content
- CSP
- TLS negotiation failure

## Bugs Raised

**Chrome**

| Resource Timing - Missing PerformanceResourceTiming entries for Requests that don't receive a Response | https://code.google.com/p/chromium/issues/detail?id=460879 |
| Resource Timing - Malformed HTML causes incorrect PerformanceEntry | https://code.google.com/p/chromium/issues/detail?id=464058 |

**Firefox**

| Resource Timing API - responseEnd is before requestStart and responseStart for HTTP 404 | https://bugzilla.mozilla.org/show_bug.cgi?id=1139831 |

## Testing in WPT

If you want to check any of the cases in WPT set a custom metric so you can copy the values, or extract them via the API

For example:

```
[RT]
var url = document.getElementById("test-img");	
resourceEntries = window.performance.getEntriesByName(url.src);

return JSON.stringify(resourceEntries, null, 2);
```
