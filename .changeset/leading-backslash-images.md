---
"vinext": patch
---

Reject leading-backslash image URLs in `/_next/image` parsing to close a WHATWG URL parser differential: `\evil.example\img.png` is treated by browsers as the protocol-relative URL `//evil.example/img.png`, but was previously normalized into the local-looking path `/evil.example/img.png` and accepted. The optimizer only serves local sources, but the accepted value could be reinterpreted as an off-site origin by downstream URL consumers (see cloudflare/vinext#3767).
