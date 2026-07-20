- **Name:** Right in front of your eyes
- **Category:** Web

## Description

You just walked right past it without even realizing it existed... or maybe it never did.

## Walkthrough

The root path `/` returns a **302 redirect to `/(random character)`** — the redirect body itself contains the flag. Browsers automatically follow the redirect so the user never sees it. The flag is in the body of the 302 response.

### Steps

1. Visit the site in browser — you see the HTML page at `/(random character)`, no flag.
2. Use `curl -v http://site/` to see the raw 302 response.
3. The redirect body says:

```
Well done! You never expect this page to be here, right?
Here is the flag: LYKNCTF{d59407abc6a04f6083d38fa1cd64abfb}
```

### Flag

`LYKNCTF{d59407abc6a04f6083d38fa1cd64abfb}`
