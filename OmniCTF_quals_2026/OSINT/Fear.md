# Fear

## Challenge Info
- **Name:** Fear
- **Category:** OSINT


> **Note:** The original flag was compromised, so the correct flag format was changed. The Dread URL changes frequently — use the placeholder structure shown below.

## Description

New flag format: Find the URL of the posts-endpoint site forum where the hacker got banned (Format: `https://somethingdeep.com/posts`)

Hint: A user with the name `Maaasquerade` did unspeakable things in the darkest parts of the web. You will find him soon! He posted a message regarding the flag.

## Walkthrough

> **Note:** The hint was misleading — "darkest parts" pointed toward a darknet forum, and the most popular one is Dread which .

1. **Find the forum** — The "darkest parts of the web" refers to ``. The most prominent darknet forum is Dread, accessible via its onion address (e.g. `dreadurlhere` — URL changes frequently).
2. **Find the hacker** — Navigate to the user profile: `dreadurlhere/u/Maaasquerade`
3. **Find the posts** — Navigate to the posts section: `dreadurlhere/u/Maaasquerade/posts`
4. **Extract the flag** — The post endpoint URL is the flag.

*Note: The actual Dread URL is dynamic and changes frequently. In the real challenge, access the specific Dread forum URL directly to find Maaasquerade's posts.*

## Flag

`OmniCTF{https://dreadytofatroptsdj6io7l3xptbet6onoyno2yv7jicoxknyazubrad.onion/u/Maaasquerade/posts}`
