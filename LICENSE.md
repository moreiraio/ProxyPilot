# ProxyPilot licence

Copyright (c) 2026 Vitor Moreira. All rights reserved.

ProxyPilot is **free software to use** and **not open source**. The executable
is published here; the source is not. This file says what you may do with the
build you downloaded.

## You may

- **Use it for anything**, including at work and on commercial projects, on as
  many machines as you like, for as long as you like. There is no licence key,
  no seat count, no registration and no expiry.
- **Copy it and pass it on unchanged**, including on internal file shares and
  removable media, as long as it stays the unmodified executable published here
  and you do not charge for it.
- **Link to it.** The download page is
  <https://moreiraio.github.io/ProxyPilot/>; linking there rather than
  rehosting the file means the people you send get the current build and can
  check its published hash.

## You may not

- **Sell it**, or bundle it into something sold, without written permission.
- **Modify, patch, repackage or rebrand the executable**, or distribute a build
  that has been changed in any way. A modified binary carrying this name is
  indistinguishable from this one to the person running it, and the whole point
  of publishing a hash is that this cannot happen quietly.
- **Reverse engineer, decompile or disassemble it**, except where that right
  cannot be waived under the law that applies to you.

## No warranty

ProxyPilot is provided **"as is", without warranty of any kind**, express or
implied, including but not limited to the warranties of merchantability,
fitness for a particular purpose and non-infringement. In no event shall the
author be liable for any claim, damages or other liability, whether in an
action of contract, tort or otherwise, arising from, out of or in connection
with the software or its use.

## Use it lawfully

ProxyPilot is a debugging tool. It decrypts HTTPS only for traffic you point at
it, only after you turn decryption on, and only once you have installed its
root certificate yourself. Intercepting traffic on machines or networks you are
not authorised to inspect is your responsibility and, in most places, illegal.
The tool assumes you are debugging your own systems.

## Third-party components

The executable includes:

- **QuickJS-ng v0.16.1** — the scripting engine. MIT licence, Copyright (c)
  2017-2026 Fabrice Bellard, Copyright (c) 2017-2024 Charlie Gordon,
  Copyright (c) 2023-2026 Ben Noordhuis, Copyright (c) 2023-2026 Saúl Ibarra
  Corretgé. Full licence text: [`third-party/quickjs-ng.LICENSE`](third-party/quickjs-ng.LICENSE).
  The core engine only — `quickjs-libc` is deliberately not included, so a
  script reaches nothing beyond the API ProxyPilot binds itself.
- **stb_sprintf.h** — public domain / MIT, by Sean Barrett and contributors.

Everything else is the author's own work built on Windows system libraries. No
third-party cryptography is present: TLS and X.509 come from Schannel and
CryptoAPI, which are part of Windows.

## Questions

Anything this file does not answer, including permission to redistribute
commercially: <vitor.moreira@gmail.com>
