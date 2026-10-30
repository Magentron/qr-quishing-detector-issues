# Manual-test QR images

Written by `make qr-images` from `test/fixtures/manual_test_cases.json` on every run; do not edit it. `docs/manual-test/README.md` says how to scan the images.

- Look-alike: the "Look-alike brand names (experimental)" setting to choose before scanning.
- Band: the expected risk band, `none` when the payload is not scored.
- Domain age: what the opt-in lookup does with the "Look up domain age" setting on; with it off nothing is looked up.
- Payload: every character other than printable ASCII, a space at either end, a backtick and `|` is written `<U+XXXX>`.

| No. | File | Payload | Look-alike | Band | Domain age |
|---|---|---|---|---|---|
| 1 | `01-clean-low-org.png` | `https://www.iana.org/` | off | low | looked up for `iana.org` |
| 2 | `02-clean-low-nl.png` | `https://www.sidn.nl/` | off | low | looked up for `sidn.nl` |
| 3 | `03-clean-low-uk.png` | `https://www.nominet.uk/` | off | low | looked up for `nominet.uk` |
| 4 | `04-clean-low-app.png` | `https://nic.app/` | off | low | looked up for `nic.app` |
| 5 | `05-at-trick-medium-com.png` | `https://www.paypal.com@www.verisign.com/` | off | medium | looked up for `verisign.com` |
| 6 | `06-ip-literal-medium-none.png` | `http://192.0.2.1/login/verify` | off | medium | skipped: ipLiteralHost |
| 7 | `07-ip-literal-v6-medium-none.png` | `http://[2001:db8::1]/` | off | medium | skipped: ipLiteralHost |
| 8 | `08-punycode-medium-test.png` | `https://xn--mnchen-3ya.test/` | off | medium | skipped: specialUseName |
| 9 | `09-url-shortener-low-ly.png` | `https://bit.ly/` | off | low | looked up for `bit.ly` |
| 10 | `10-suspicious-tld-low-top.png` | `https://nic.top/` | off | low | looked up for `nic.top` |
| 11 | `11-brand-impersonation-high-xyz.png` | `https://paypal.nic.xyz/` | off | high | looked up for `nic.xyz` |
| 12 | `12-excess-subdomains-low-dev.png` | `https://a.b.c.d.e.nic.dev/` | off | low | looked up for `nic.dev` |
| 13 | `13-excess-hyphens-low-info.png` | `https://secure-account-update-verify.nic.info/` | off | low | looked up for `nic.info` |
| 14 | `14-urgency-terms-low-fr.png` | `https://www.afnic.fr/urgent/verify-account` | off | low | looked up for `afnic.fr` |
| 15 | `15-combined-high-click.png` | `https://paypal-secure-login.nic.click/verify-now` | off | high | looked up for `nic.click` |
| 16 | `16-insecure-scheme-low-online.png` | `http://nic.online/` | off | low | looked up for `nic.online` |
| 17 | `17-embedded-credentials-medium-site.png` | `https://user:pass@nic.site/` | off | medium | looked up for `nic.site` |
| 18 | `18-obfuscated-ip-decimal-medium-none.png` | `http://3221225985/` | off | medium | skipped: ipLiteralHost |
| 19 | `19-obfuscated-ip-hex-medium-none.png` | `http://0xc0000201/` | off | medium | skipped: ipLiteralHost |
| 20 | `20-obfuscated-idn-medium-test.png` | `https://paypa%C4%BC.test/` | off | medium | skipped: notADnsName |
| 21 | `21-brand-lookalike-high-example.png` | `https://xn--pypal-4ve.example/` | on | high | skipped: hostNotValidated |
| 22 | `22-dangerous-javascript-high-none.png` | `javascript:void(0)` | off | high | not looked up |
| 23 | `23-dangerous-data-high-none.png` | `data:text/plain,manual-test` | off | high | not looked up |
| 24 | `24-dangerous-file-high-none.png` | `file:///etc/hosts` | off | high | not looked up |
| 25 | `25-dangerous-intent-high-none.png` | `intent://scan/#Intent;scheme=zxing;end` | off | high | not looked up |
| 26 | `26-dangerous-vbscript-high-none.png` | `vbscript:msgbox(1)` | off | high | not looked up |
| 27 | `27-dangerous-blob-high-none.png` | `blob:https://www.iana.org/00000000-0000-0000-0000-000000000000` | off | high | not looked up |
| 28 | `28-no-registry-es-low-es.png` | `https://www.dominios.es/` | off | low | skipped: noRegistryService |
| 29 | `29-no-registry-de-low-de.png` | `https://www.denic.de/` | off | low | skipped: noRegistryService |
| 30 | `30-no-registry-io-low-io.png` | `https://nic.io/` | off | low | skipped: noRegistryService |
| 31 | `31-special-use-test-low-test.png` | `https://bank.test/` | off | low | skipped: specialUseName |
| 32 | `32-special-use-local-low-local.png` | `http://printer.local/` | off | low | skipped: specialUseName |
| 33 | `33-special-use-internal-low-internal.png` | `https://intranet.internal/` | off | low | skipped: specialUseName |
| 34 | `34-single-label-low-none.png` | `http://intranet/` | off | low | skipped: singleLabelHost |
| 35 | `35-public-suffix-low-uk.png` | `https://co.uk/` | off | low | skipped: hostIsPublicSuffix |
| 36 | `36-wifi-none-none.png` | `WIFI:T:WPA;S:ManualTest;P:not-a-real-password;;` | off | none | not looked up |
| 37 | `37-plain-text-none-none.png` | `This is a manual test code with no address.` | off | none | not looked up |
| 38 | `38-mailto-none-none.png` | `mailto:nobody@example.org` | off | none | not looked up |
| 39 | `39-tel-none-none.png` | `tel:+441632960000` | off | none | not looked up |
| 40 | `40-vcard-none-none.png` | `BEGIN:VCARD<U+000D><U+000A>VERSION:3.0<U+000D><U+000A>N:Tester;Manual;;;<U+000D><U+000A>FN:Manual Tester<U+000D><U+000A>END:VCARD` | off | none | not looked up |
| 41 | `41-unsupported-scheme-none-none.png` | `ftp://ftp.iana.org/` | off | none | not looked up |
| 42 | `42-malformed-whitespace-none-none.png` | `https://www.iana .org/` | off | none | not looked up |
| 43 | `43-malformed-percent-none-none.png` | `https://www.iana.org/%zz` | off | none | not looked up |
| 44 | `44-malformed-port-none-none.png` | `https://www.iana.org:1234567/` | off | none | not looked up |
| 45 | `45-malformed-encoded-delimiter-none-none.png` | `https://www.iana.org%2Fnic.top/` | off | none | not looked up |
| 46 | `46-malformed-control-none-none.png` | `https://example.com/p<U+0000>ath` | off | none | not looked up |
| 47 | `47-registry-endpoint-low-com.png` | `https://rdap.verisign.com/v1/domain/x` | off | low | skipped: destinationIsScannedHost |
| 48 | `48-host-not-validated-medium-test.png` | `https://xn--3ba.test/` | off | medium | skipped: hostNotValidated |
| 49 | `49-schemeless-www-low-net.png` | `www.ripe.net/` | off | low | looked up for `ripe.net` |
| 50 | `50-schemeless-bare-low-org.png` | `icann.org/` | off | low | looked up for `icann.org` |
| 51 | `51-trailing-dot-low-net.png` | `https://www.apnic.net./` | off | low | looked up for `apnic.net` |
| 52 | `52-private-suffix-tenant-low-com.png` | `https://googleblog.blogspot.com/` | off | low | looked up for `blogspot.com` |
| 53 | `53-escaped-host-unreserved-high-top.png` | `https://p%61ypal.nic.top/` | off | high | skipped: notADnsName |
| 54 | `54-official-brand-domain-low-es.png` | `https://www.dgt.es/multas` | off | low | skipped: noRegistryService |
| 55 | `55-malformed-empty-host-none-none.png` | `http:///login` | off | none | not looked up |
| 56 | `56-malformed-parse-failure-none-none.png` | `https://a@b@example.com/` | off | none | not looked up |
| 57 | `57-malformed-bracket-none-none.png` | `http://[::1]xyz/` | off | none | not looked up |
| 58 | `58-mapped-delimiter-literal-none-none.png` | `https://neutral<U+FF0E>x.test/` | off | none | not looked up |
| 59 | `59-mapped-delimiter-encoded-none-none.png` | `https://neutral%EF%BC%8Ex.test/` | off | none | not looked up |
| 60 | `60-clean-low-cz.png` | `https://www.nic.cz/` | off | low | looked up for `nic.cz` |
| 61 | `61-clean-low-no.png` | `https://www.norid.no/` | off | low | looked up for `norid.no` |
| 62 | `62-clean-low-pl.png` | `https://www.dns.pl/` | off | low | looked up for `dns.pl` |
| 63 | `63-clean-low-ca.png` | `https://www.cira.ca/` | off | low | looked up for `cira.ca` |
| 64 | `64-clean-low-br.png` | `https://registro.br/` | off | low | looked up for `registro.br` |
| 65 | `65-clean-low-fi.png` | `https://www.traficom.fi/` | off | low | looked up for `traficom.fi` |
| 66 | `66-clean-low-is.png` | `https://www.isnic.is/` | off | low | looked up for `isnic.is` |
| 67 | `67-clean-low-sg.png` | `https://www.sgnic.sg/` | off | low | looked up for `sgnic.sg` |
| 68 | `68-clean-low-au.png` | `https://www.auda.org.au/` | off | low | looked up for `auda.org.au` |
| 69 | `69-brand-in-path-low-shop.png` | `https://nic.shop/paypal/` | off | low | looked up for `nic.shop` |
| 70 | `70-brand-in-query-low-store.png` | `https://nic.store/?from=correos` | off | low | looked up for `nic.store` |
| 71 | `71-urgency-in-query-low-tech.png` | `https://nic.tech/?step=confirm` | off | low | looked up for `nic.tech` |
| 72 | `72-urgency-dutch-low-live.png` | `https://www.nic.live/boete/achterstallig` | off | low | looked up for `nic.live` |
| 73 | `73-credentials-insecure-high-website.png` | `http://admin:1234@nic.website/` | off | high | looked up for `nic.website` |
| 74 | `74-insecure-subdomains-urgency-medium-space.png` | `http://pago.multa.aviso.cobro.nic.space/` | off | medium | looked up for `nic.space` |
| 75 | `75-suspicious-tld-link-low-link.png` | `https://nic.link/` | off | low | looked up for `nic.link` |
| 76 | `76-brand-hyphens-urgency-high-work.png` | `https://dhl-parcel-fee-payment.nic.work/` | off | high | looked up for `nic.work` |
| 77 | `77-insecure-urgency-path-medium-icu.png` | `http://nic.icu/aduana/tasa` | off | medium | looked up for `nic.icu` |
| 78 | `78-two-brands-high-cam.png` | `https://seur.dhl.nic.cam/` | off | high | looked up for `nic.cam` |
| 79 | `79-deep-subdomains-suspicious-tld-low-cyou.png` | `https://login.account.secure.update.nic.cyou/` | off | low | looked up for `nic.cyou` |
| 80 | `80-url-shortener-root-low-com.png` | `https://tinyurl.com/` | off | low | looked up for `tinyurl.com` |
| 81 | `81-at-trick-urgency-medium-help.png` | `https://login.paypal.com@nic.help/confirm` | off | medium | looked up for `nic.help` |
| 82 | `82-upper-case-low-cc.png` | `HTTPS://WWW.NIC.CC/` | off | low | looked up for `nic.cc` |
| 83 | `83-brand-subdomain-medium-pro.png` | `https://santander.nic.pro/` | off | medium | looked up for `nic.pro` |
| 84 | `84-escaped-ip-literal-medium-none.png` | `https://%3192.0.2.1/` | off | medium | skipped: notADnsName |
| 85 | `85-escaped-suspicious-tld-low-top.png` | `https://nic.t%6Fp/` | off | low | skipped: notADnsName |
| 86 | `86-escaped-url-shortener-low-ly.png` | `https://bit.l%79/` | off | low | skipped: notADnsName |
| 87 | `87-punycode-undecoded-medium-test.png` | `https://xn--.test/` | off | medium | skipped: notADnsName |
| 88 | `88-urgency-three-words-low-surf.png` | `https://nic.surf/pago/multa/urgente` | off | low | looked up for `nic.surf` |
| 89 | `89-brand-single-domain-high-loan.png` | `https://correos.nic.loan/` | off | high | looked up for `nic.loan` |
| 90 | `90-subdomains-threshold-low-biz.png` | `https://a.b.c.nic.biz/` | off | low | looked up for `nic.biz` |
| 91 | `91-clean-low-tw.png` | `https://www.twnic.tw/` | off | low | looked up for `twnic.tw` |
| 92 | `92-dangerous-obfuscated-high-none.png` | `java<U+0009>script:void(0)` | off | high | not looked up |
| 93 | `93-dangerous-padded-obfuscated-high-none.png` | `<U+0020> java<U+0009>script:void(0)` | off | high | not looked up |
| 94 | `94-plain-text-padded-none-none.png` | `<U+0020> This is a padded manual test code. <U+0020>` | off | none | not looked up |
| 95 | `95-plain-text-markers-none-none.png` | `Hidden characters A<U+202E>B<U+200B>C<U+E000>D <U+30C6><U+30B9><U+30C8><U+3002>` | off | none | not looked up |
| 96 | `96-url-padded-low-si.png` | `<U+0020>https://www.register.si/<U+0020>` | off | low | looked up for `register.si` |
| 97 | `97-url-long-low-ar.png` | `https://nic.ar/aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa` | off | low | looked up for `nic.ar` |
| 98 | `98-idn-literal-medium-fun.png` | `https://m<U+00FC>nchen.nic.fun/` | off | medium | looked up for `nic.fun` |
| 99 | `99-path-delimiter-mapped-low-club.png` | `https://nic.club/a<U+FF0E>b` | off | low | looked up for `nic.club` |

## Image cases

Each draws on the cases it names; open it with "Check a code from an image" rather than scanning it.

| No. | File | Cases | Expected |
|---|---|---|---|
| 100 | `100-multi-code.png` | 1, 11 | two codes of different bands in one picked image, handled as master §7.3.5 describes |
| 101 | `101-oversized.png` | 1 | a picked image larger than kEncodedByteCap, refused before decoding as master §7.3.4 describes |

## Long URLs

Extra cases from `test/fixtures/manual_long_urls.json`: one payload of an exact character length per row, built to land in the stated band.

- Look-alike: the "Look-alike brand names (experimental)" setting to choose before scanning.
- Domain age: not part of these cases' expectation, so "Look up domain age" may be left either on or off.

| No. | File | Length | Band | Look-alike | Payload |
|---|---|---|---|---|---|
| 200 | `200-long-128-low-nl.png` | 128 | low | off | `https://www.sidn.nl/?pad=0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000` |
| 201 | `201-long-256-low-nl.png` | 256 | low | off | `https://www.sidn.nl/?pad=000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000` |
| 202 | `202-long-512-low-nl.png` | 512 | low | off | `https://www.sidn.nl/?pad=0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000` |
| 203 | `203-long-1024-low-nl.png` | 1024 | low | off | `https://www.sidn.nl/?pad=000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000` |
| 204 | `204-long-2048-low-nl.png` | 2048 | low | off | `https://www.sidn.nl/?pad=0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000` |
| 205 | `205-long-128-medium-nl.png` | 128 | medium | off | `https://www.paypal.com@www.sidn.nl/?pad=0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000` |
| 206 | `206-long-256-medium-nl.png` | 256 | medium | off | `https://www.paypal.com@www.sidn.nl/?pad=000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000` |
| 207 | `207-long-512-medium-nl.png` | 512 | medium | off | `https://www.paypal.com@www.sidn.nl/?pad=0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000` |
| 208 | `208-long-1024-medium-nl.png` | 1024 | medium | off | `https://www.paypal.com@www.sidn.nl/?pad=000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000` |
| 209 | `209-long-2048-medium-nl.png` | 2048 | medium | off | `https://www.paypal.com@www.sidn.nl/?pad=0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000` |
| 210 | `210-long-128-high-xyz.png` | 128 | high | off | `https://paypal.nic.xyz/?pad=0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000` |
| 211 | `211-long-256-high-xyz.png` | 256 | high | off | `https://paypal.nic.xyz/?pad=000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000` |
| 212 | `212-long-512-high-xyz.png` | 512 | high | off | `https://paypal.nic.xyz/?pad=0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000` |
| 213 | `213-long-1024-high-xyz.png` | 1024 | high | off | `https://paypal.nic.xyz/?pad=000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000` |
| 214 | `214-long-2048-high-xyz.png` | 2048 | high | off | `https://paypal.nic.xyz/?pad=0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000` |

## Look-alike brand names

Extra cases from `test/fixtures/manual_lookalike_cases.json`: hosts that resemble a brand through a look-alike letter, a digit or a hyphen, and a few the look-alike check deliberately leaves alone. Scan each twice, once with the "Look-alike brand names (experimental)" setting on and once with it off: the two bands show what the setting changes.

- Resembles: the brands the look-alike check names with the setting on, `-` when it names none.
- Domain age: not part of these cases' expectation, so "Look up domain age" may be left either on or off; a reserved `.example` host is never looked up.
- Payload: escaped as in the first table, so a look-alike letter shows as `<U+XXXX>`.

| No. | File | Payload | Resembles | Band (look-alike on) | Band (look-alike off) |
|---|---|---|---|---|---|
| 400 | `400-lookalike-cyrillic-literal-high-example.png` | `https://p<U+0430>ypal.example/` | paypal | high | medium |
| 401 | `401-lookalike-cyrillic-a-label-high-example.png` | `https://xn--orreos-hrf.example/` | correos | high | medium |
| 402 | `402-lookalike-greek-high-example.png` | `https://bbv<U+03B1>.example/` | bbva | high | medium |
| 403 | `403-lookalike-upper-case-high-example.png` | `https://<U+0405>ANTANDER.example/` | santander | high | medium |
| 404 | `404-lookalike-cyrillic-dze-high-example.png` | `https://<U+0455>eur.example/` | seur | high | medium |
| 405 | `405-lookalike-digit-one-medium-example.png` | `https://paypa1.example/` | paypal | medium | low |
| 406 | `406-lookalike-digit-zero-medium-example.png` | `https://c0rreos.example/` | correos | medium | low |
| 407 | `407-lookalike-digit-five-medium-example.png` | `https://5eur.example/` | seur | medium | low |
| 408 | `408-lookalike-digit-three-medium-example.png` | `https://r3nfe.example/` | renfe | medium | low |
| 409 | `409-lookalike-hyphen-medium-example.png` | `https://d-g-t.example/` | dgt | medium | low |
| 410 | `410-lookalike-hyphen-split-medium-example.png` | `https://caixa-bank.example/` | caixabank | medium | low |
| 411 | `411-lookalike-two-brands-high-example.png` | `https://dh1-5eur.example/` | dhl, seur | high | low |
| 412 | `412-lookalike-urgency-insecure-high-example.png` | `http://paypa1.example/login/verify` | paypal | high | low |
| 413 | `413-lookalike-suspicious-tld-high-top.png` | `https://iberdro1a.nic.top/verify` | iberdrola | high | low |
| 414 | `414-lookalike-suppressed-high-example.png` | `https://dgt-multas-pago.example/` | - | high | high |
| 415 | `415-lookalike-official-domain-low-com.png` | `https://www.paypal.com/` | - | low | low |
| 416 | `416-lookalike-escaped-low-example.png` | `https://paypa%31.example/` | - | low | low |
| 417 | `417-lookalike-diacritic-medium-example.png` | `https://p<U+00E0>ypal.example/` | - | medium | medium |

## Young domains

Extra cases, not from a manifest: one `https://<host>/` per young host, found by `make young-domain-image` or given in `QR_YOUNG_HOSTS`, rewritten on every run and kept, through `young-domains.json`, until either names others or `make clean-qr-images` removes them. Each domain is a stranger's and newly registered domains are often abusive: scan it, never open its link.

- Look-alike: the "Look-alike brand names (experimental)" setting to choose before scanning.
- Registered: when the domain was registered, from its registry; "not looked up" for a host given by hand.
- Young until: with "Look up domain age" on, the badge calls the domain young until this day, 90 days after its registration, and gives its age without that word from then on.

| No. | File | Payload | Look-alike | Band | Registered | Young until |
|---|---|---|---|---|---|---|
| 500 | `500-young-domain.png` | `https://51theme.com/` | off | low | 2026-10-27 | 2027-01-25 |
