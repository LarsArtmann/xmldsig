# Fork of invopop/xmldsig — v0.14.0 + /ksef package backport

Private LarsArtmann fork. Upstream tag: `v0.14.0` (commit f7e688cb).

## Why

Upstream removed the root-level `ksef` package in v0.14.0 (it survives as
`profiles/ksef`), but `github.com/invopop/gobl.pl.ksef` v0.46.0 (the Polish
KSeF FA_VAT module, released the same day as gobl v0.507.0) still imports
`github.com/invopop/xmldsig/ksef` in its `api` package. Meanwhile every
`gobl.ubl` release built for gobl v0.507.0 (v0.77.0+) requires xmldsig
v0.14.0. The two cannot be satisfied simultaneously against upstream
modules alone.

## Delta vs upstream v0.14.0

- `ksef/ksef.go` + `ksef/ksef_test.go`: copied verbatim from upstream
  v0.13.0. Compiles and tests green against the v0.14.0 root package
  unchanged (the package only constructs `XMLDSigConfig`/`XAdESConfig`
  values and cert-subject helpers).

## When to drop this fork

When gobl.pl.ksef releases a version that no longer imports
`github.com/invopop/xmldsig/ksef` (or upstream restores the package).
Then: remove the `replace` directive in consumers and delete this repo.

## Tagging

`v0.14.0-lars1` = upstream v0.14.0 + the ksef package backport.
