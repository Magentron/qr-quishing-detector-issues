# QR Quishing Detector: issue tracker

This repository is the public place to **report problems with QR Quishing
Detector and to follow what happens to them**. It holds no source code: the app
is proprietary, and this repository exists only for issues.

QR Quishing Detector reads QR codes and similar codes with the camera or from
an image on your device, shows plainly what a code contains, and, for a web
address it can check, gives an explained risk rating of LOW, MEDIUM or HIGH
from checks that run offline on your device. It never visits the address it
reads. It is built for Android and iOS, in English, Spanish and Dutch.

Website, where you can also find the privacy policy:
<https://magentron.codeberg.page/qr-quishing-detector/>

## What belongs here

Open an issue for any of these:

- **A bug**: the app crashes, freezes, shows something wrong, or a screen
  does not work as it should.
- **A wrong risk rating**: a web address rated too high (a false alarm) or too
  low (a missed warning). These reports are welcome, and they help.
- **A code the app does not read**: a QR code, Data Matrix, Aztec, PDF417 or
  barcode that the camera or a picked image does not read, or reads wrongly.
- **A translation problem**: wording that is wrong, unclear or missing in
  Spanish, Dutch or English.
- **A suggestion** for something the app could do.

Please search the open and closed issues first, and add to an existing one
instead of opening a second.

## What to include

The more of this you can give, the faster a problem can be reproduced:

1. **The app version.** Open the Options screen: the version is shown at the
   top, next to the word "Version".
2. **Your device and system**: for example "Pixel 8, Android 15" or
   "iPhone 14, iOS 18".
3. **The language** the app was set to.
4. **What you did**, step by step, **what you expected** and **what happened
   instead**. For a code that is not read, say whether you used the camera or
   picked an image, and in what light or from what source.
5. **A screenshot** if it helps. Check it first for anything private.

For a wrong risk rating, add the result screen and the web address if it is
safe to share. See "Keep private things out" below.

## Test codes

The [`manual-test/`](manual-test/README.md) directory holds QR codes and other
barcodes for checking the app by hand, with an `INDEX.md` for each set that
says what every image is expected to show. Its `README.md` says how to use
them. If the app shows something different, open an issue as described above,
naming the file and the settings you used.

## Keep private things out

**Everything in an issue is public**, and it stays public even if you edit or
delete it later.

- The app collects nothing, and its optional result history, when you turn
  it on, is stored on your device and is never sent to the developer, so the
  developer knows only what you write here. Do not paste an entry from it
  that holds something private, such as a Wi-Fi password.
- Do not post a code or a web address that carries a personal link, an
  account, a token, a password, a payment detail or a private document.
- If an address matters to the report but should not be clicked by a reader,
  write it defanged, for example `hxxps://example[.]com/path`. If only the
  domain matters, give just the domain.
- If you cannot share the real address, a similar example with the same shape
  (the same kind of domain, subdomains, path and characters) is usually enough.
- Crop or blur personal details in screenshots, including notification bars
  and other apps behind the app.

## Security problems

If you think you have found a **vulnerability**, a way to make the app unsafe,
or a way to hide a dangerous address from its checks, **do not open a public
issue**. Email <security@magentron.com> with the word "Security" in the subject and
describe what you found and how to reproduce it.

## What to expect

This is a one-person project. Every report is read, but this page makes no
promise about when a problem will be answered or fixed. The status of an issue
is shown by its open or closed state and its labels, and a closing comment says
what was decided.

A risk rating is a heuristic, structural check and an aid to your own
judgement. A low score does not mean a link is safe, and a high score is not
proof of phishing. When in doubt, do not open the link: go to the organisation's
official site or app yourself. Reports that a rating was wrong are used to
improve the checks, and an individual rating may not change as a result.

## Languages

Issues can be written in English, Spanish or Dutch.

## Licence and credits

The application is proprietary, all rights reserved. Copyright © 2026
Magentron a.k.a. Jeroen Derks. Nothing in this repository grants a licence to
the application or its source code.

Part of the heuristic logic of the app is based on the work of Nieves Casquero
(`qr_forense.py`, MIT licence):
[LinkedIn](https://www.linkedin.com/in/nievescasquero/) and the
[source project](https://github.com/AnkbNikas/quishing-detector).
The full notices are shown on the licence page inside the app.
