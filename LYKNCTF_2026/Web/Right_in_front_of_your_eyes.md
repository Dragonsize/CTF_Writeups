# Right in front of your eyes

## Challenge Info
- **Name:** Right in front of your eyes
- **Category:** Web
- **CTF:** LYKNCTF 2026

## Description
An HTTP protocol trick. The root URL returns a 302 with the flag in the response body; browsers follow the redirect and drop the body without rendering it.

## Walkthrough

### Step 1 — Browser rendering hides the flag
Opening the URL in a browser shows a plain page:

```
It in front of your eyes But you can't see it
```

The address bar reads `/`. Devtools shows the request path as `/`, and the returned document includes:

```html
<script>
  // You find 1 more clue hmmm.
  history.replaceState(null, "", "/");
  document.currentScript.remove();
</script>
```

Someone deliberately rewrote the URL bar back to `/` and deleted the script afterwards. The real path the browser landed on was hidden from view.

### Step 2 — Raw HTTP without follow-redirects
```
$ curl -s -i "http://<host>/"
HTTP/1.1 302 Found
Content-Length: 116
Content-Type: text/plain; charset=utf-8
Location: /A
Server: Python/3.12 aiohttp/3.14.1

Well done! You never expect this page to be here, right?
Here is the flag: LYKNCTF{ff32f12568be4a43a62abdbb80d85b2a}
```




## Flag
`LYKNCTF{ff32f12568be4a43a62abdbb80d85b2a}`
