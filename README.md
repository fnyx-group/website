# fnyx-group website

## What this is

This is the source of fnyx-group.org, the website of fnyx-group. fnyx-group is a French non-profit association that makes free and open source apps, flust and fnoise.

## Structure

The site is static HTML with one style.css. There is no build step and no JavaScript.

- French pages are at the root, for example /flust/ and /mentions-legales/.
- English pages are under /en/, for example /en/flust/ and /en/legal/.
- Old URLs such as /fr/, /fr/flust/, /fr/fnoise/, /legal/ and /privacy/ are small redirect pages that point to the current ones.
- Images and logos are in /assets/.

## Adding a page

Every new page goes through this checklist.

1. A title and a description, each under 160 characters.
2. A canonical link to the page itself.
3. hreflang links for fr, en and x-default. x-default points to the French page.
4. og and twitter tags, with the same title, description and image as the page.
5. The page in the header and footer nav, in both languages.
6. An entry in sitemap.xml.
7. A character scan, see Writing rules.

## Running locally

```
python3 -m http.server
```

Then open http://localhost:8000.

## Deployment

The site is served by GitHub Pages from the main branch. The custom domain is set in CNAME.

## Writing rules

- No colon or semicolon inside sentences. Split the sentence or use a comma instead.
- Straight apostrophes and quotes only.
- Titles use " | " as separator, for example "flust | fnyx-group".
- The following characters are forbidden, listed by code point.
  - U+2014 em dash and U+2013 en dash
  - U+00B7 middle dot and U+2022 bullet
  - U+2192 and U+2190 arrows
  - U+00AB and U+00BB angle quotes
  - U+201C, U+201D, U+2018 and U+2019 curly quotes
  - U+2026 ellipsis
  - U+2713 check mark, U+00D7 multiplication sign and U+2248 almost equal sign
  - Zero-width characters U+200B, U+200C, U+200D, U+2060 and U+FEFF

To scan the repository, run the command below. It prints nothing when the files are clean.

```
grep -rnP '[\x{2014}\x{2013}\x{00B7}\x{2022}\x{2192}\x{2190}\x{00AB}\x{00BB}\x{201C}\x{201D}\x{2018}\x{2019}\x{2026}\x{2713}\x{00D7}\x{2248}\x{200B}\x{200C}\x{200D}\x{2060}\x{FEFF}]' --exclude-dir=.git --exclude=LICENSE .
```

## License

The code is under MPL-2.0, see LICENSE. The names and logos are not covered, see TRADEMARKS.md.
