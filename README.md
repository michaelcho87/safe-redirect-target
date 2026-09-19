# safe-redirect-target

Is this `?next=` value safe to redirect to? Returns the path if it is a plain same-origin path, the fallback otherwise.

Catches the spellings that actually get exploited: protocol-relative `//evil.com`, the backslash form `/\evil.com` (Chrome and Safari treat it as `//`), percent-encoded slashes, control characters, absolute URLs and `javascript:`.

```js
import { safeRedirectTarget } from "safe-redirect-target";
safeRedirectTarget("/library");        // "/library"
safeRedirectTarget("//evil.com");      // "/"
safeRedirectTarget("/\\evil.com");     // "/"
safeRedirectTarget("/x", { allowPrefixes: ["/products"] }); // "/"
```

Zero dependencies. Node 18+. `npm test` runs node:test. MIT.
