# ocr-tools v1.6 (1997-11-14)

Source code of the tools from the book *Tools for Publishing Source Code via OCR*
by Colin Plumb, Mark H. Weaver and Philip R. Zimmermann
(© 1997 Pretty Good Privacy, Inc.).

## What this is

In 1997 the US Export Administration Regulations (EAR) restricted exporting encryption software, but exempted printed books (EAR §734.3(b)(2)).
To get around this, PGP Inc. published the source code of PGP as printed books.
Outside the US, volunteers (the PGPi project) scanned the pages and turned them back into compilable source code.
This book prints the toolchain built to make that round trip reliable:

- `munge`: turns source files into printable pages. Every line carries a CRC, and each page has a
  header and a CRC-32. Tabs, form feeds and trailing whitespace are made visible.
- `repair`: corrects OCR output interactively. It uses the per-line CRCs and a learned table of
  likely OCR substitutions (for example `l`/`1` and `O`/`0`).
- `unmunge`: checks the repaired pages and turns them back into the original file tree.
- `bootstrap`, `bootstrap2`: small Perl scripts, short enough to type in by hand, that recover
  the rest of the tools from the printed pages.
- `sortpages`, `makemanifest`, `psgen`, `yapp`: helpers for ordering pages, writing the
  manifest and producing PostScript.

## Where this copy comes from

These files were recovered from the PDF text layer of a scan of the printed book. The recovery used the book's own checks: every line matched its printed CRC, and
the book's own `repair` made 0 substitutions across the 99 munged pages. The CVS `$Id` keywords
date the snapshot to 1997-11-14 or earlier (the newest is `repair.c,v 1.37 1997/11/14`).

## Historical uniqueness

As of 2026-11-11, five of these files, exactly as printed in the book, are not found online:
`sortpages` (v1.6), `repair.c`, `util.c`, `unmunge.c` and `Makefile`.

- Software Heritage, <https://archive.softwareheritage.org/> only knows 14 source files:
  `bootstrap`, `bootstrap2`, `heap.c`, `heap.h`, `makemanifest`, `mempool.c`, `mempool.h`,
  `munge.c`, `psgen`, `subst.c`, `subst.h`, `util.h`, `yapp` and `yapp.doc`.
- GitHub code search, <https://github.com/search?type=code>: no match for the CVS `$Id` strings of `sortpages` v1.6 and `repair.c` v1.37.

Unless one of these searches missed a copy, this repository is the only public digital copy of
the tools exactly as printed in the book.

## Building

```sh
make            # builds munge, unmunge and repair
make clean
```

This was written for 1997 compilers. It still builds with GCC 15, with warnings.
