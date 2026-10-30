# Test codes for QR Quishing Detector

These codes are for checking the app by hand on a real device. Each directory
has an `INDEX.md` that lists every image and says what the app is expected to
show for it:

- [`qr/`](qr/INDEX.md): one QR code per test case. `INDEX.md` gives each
  file's content, how to set "Look-alike brand names (experimental)" in
  Options before scanning, and the risk rating and domain-age result the app
  should give. The domain-age result assumes "Look up domain age" is on.
- [`symbologies/`](symbologies/INDEX.md): other kinds of barcode, and codes
  saved in other image formats.

## How to use them

Show an image full size on a second screen, or print it, and scan it with the
app. A dense code, such as one of the long web addresses, needs a full-size
image held steady under even light; a thumbnail will not read.

An image that `INDEX.md` says is opened rather than scanned, such as
`qr/100-multi-code.png` and `qr/101-oversized.png`, is copied to the device and
opened with "Check a code from an image" on the scanner screen.

**Scan the look-alike cases, numbered from 400, twice**: once with
"Look-alike brand names (experimental)" on and once with it off. The two risk
ratings in `INDEX.md` show what the setting changes.

**The young-domain code**, numbered from 500 and listed under "Young domains"
in `INDEX.md`, holds the address of a real domain registered a few days before
the image was made. With "Look up domain age" on in Options, the app should say
the domain was registered only recently. That holds for 90 days from the
domain's registration only, so an older image shows the domain's age without
calling it young; if it does, say so in an issue and a fresh one will be made.
The domain belongs to a stranger, and newly registered domains are often used
for scams: scan it, but never open its link.

**Some codes are built to look like phishing on purpose, so do not open their
links.** Where `INDEX.md` mentions `make` or a path under `docs/`, it refers to
the app's own source, which is not public.

## Reporting a difference

If the app shows something other than what `INDEX.md` expects, open an issue
naming the file, the app version, your device, the settings you used and what
you saw, with a screenshot if you can.

These images are generated from the app's test cases and replaced as a whole
when those change, so please do not edit them here.
