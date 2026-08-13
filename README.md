# ProxyPilot

A native Win32 **intercepting HTTP proxy** for debugging traffic. One
executable, no installer, no runtime, and it never asks for elevation.

**[Download and full feature list &rarr; moreiraio.github.io/ProxyPilot](https://moreiraio.github.io/ProxyPilot/)**

---

## What it is

Point a client at `127.0.0.1:8888` and every HTTP transaction becomes a row:
method, host, URL, status, body sizes and timings, with the request and
response bytes retained for inspection.

```
curl -x 127.0.0.1:8888 https://example.com
```

- **HTTPS on your terms.** `CONNECT` is relayed blind by default. Turn
  decryption on and it is intercepted instead, a certificate minted per host,
  and the requests inside listed individually. Decryption and trusting the root
  are two separate decisions, and the status bar says so when they disagree.
- **HTTP/2, WebSocket, SSE and gRPC, decoded.** Full h2 framing and HPACK
  inside decrypted tunnels, every WebSocket frame listed, `text/event-stream`
  events published while the stream is still open, and gRPC split into messages
  and judged by `grpc-status` in its trailers rather than by a 200.
- **Bodies made readable without touching the wire.** gzip, Brotli and
  Zstandard decoded in-house, stacked encodings unwound in order, JSON and XML
  pretty-printed, protobuf read with no schema, images previewed, form bodies
  split into fields — all at display time. The stored bytes stay exactly what
  arrived.
- **Break, rewrite and answer traffic.** Breakpoints before the request and
  after the response, AutoResponder rules, and a composer that replays by
  dialling the proxy's own listener so replays are captured like anything else.
- **Scripting with FiddlerScript's reach.** A QuickJS host with `onRequest` and
  `onResponse`. Off by default, and loud on the status bar while on.
- **Nothing leaves the machine.** No account, no telemetry, no update check, no
  network calls of its own. It works with no network connection at all.

## Requirements

| | |
|---|---|
| Operating system | Windows 10 or later, x64 |
| Runtime | None — no .NET, no Electron, no DLLs |
| Elevation | Never asked for |
| Install | None. `config.json` lands beside the executable |
| Cost | Free, and no account |

## The root certificate

There is nothing to download. The program mints its own root the first time you
turn decryption on and writes it beside `config.json` as `ProxyPilotRoot.cer`
and `ProxyPilotRoot.pem`. Installing it into the Windows trust store is always
a separate, explicit act, and ProxyPilot never does it without being asked.

## Reporting a problem

[Open an issue](https://github.com/moreiraio/ProxyPilot/issues). Please include:

- the version, from the title bar or *Settings &rsaquo; About*
- what the client was (curl, a browser, an app)
- whether **Decrypt HTTPS** was on

A crash also leaves a log file beside `config.json` — it records addresses and
module offsets only, never a memory dump.

## Repository layout

This repository is the public home of ProxyPilot: **releases, the issue
tracker, and the download page** served at
[moreiraio.github.io/ProxyPilot](https://moreiraio.github.io/ProxyPilot/).

The source is not public.

| Path | What |
|---|---|
| `index.html` | The download page, served by GitHub Pages |
| `img/` | Screenshots of the program, captured from real traffic |

## Support the work

<https://www.paypal.me/vrmoreira>

It buys nothing — every feature is in the build. A donation pays for the time,
it does not unlock anything.

## Contact

<vitor.moreira@gmail.com>
