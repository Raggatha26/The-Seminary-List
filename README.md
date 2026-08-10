# The Seminary List

A shoppable packing list for girls going to seminary. 68 items across 9 categories,
each linking to Amazon, with a checklist that remembers what you have already packed.

**Live site:** _(paste your Vercel address here once deployed)_

---

## How it works

The whole site is one file: `index.html`. There is no build step, no framework,
and no dependencies. Every product card is real HTML written into the file, so the
page renders fully even if JavaScript never runs.

JavaScript only adds the extras:

- checkbox ticking and the progress meter
- search
- collapsing sections
- swapping icons for photos

Checked items are saved in the browser's `localStorage` under the key
`seminary-list-v2`, so the list keeps its place between visits. It is per-browser,
not per-account, so checking items on a phone will not show up on a laptop.

## Why 68 items but 93 links

Some products have two or three options (three egg crate toppers, three portable
chargers, and so on). Those share a single checkbox, because they are one thing to
buy. Ticking any one option checks all of them together.

That is what `data-group` on each card does. The hero progress squares and the
per-section counters count groups, not cards, so the numbers reflect things left
to pack rather than tiles on screen.

## Adding photos

Near the top of the `<script>` tag there is a block that looks like this:

```js
var IMAGES = {
  "shabbat-lamp": "",
  "linen-set-option-a": "",
  ...
};
```

Put a path or URL between the quotes and that card shows a photo instead of its
icon. Leave it blank and the icon stays. A broken link falls back to the icon
automatically.

For self-hosted photos, make an `img/` folder next to `index.html`, drop the file
in, and write `"shabbat-lamp": "img/shabbat-lamp.jpg",`. Resize to roughly 800px
wide first so the page stays fast.

Note: Amazon retired SiteStripe image links in December 2023, and their current
Creators API requires around 10 qualifying sales in the trailing 30 days. Their
terms do not permit self-hosting Amazon's product photos, so use your own.

## Editing

Small changes (fixing a name, swapping a link, adding a photo path) can be made
directly in `index.html` from GitHub's web editor, which works fine on an iPad.
Commit the change and Vercel republishes within about a minute.

Adding a whole new product by hand is fiddlier: a card needs a matching progress
square, an image-map entry, and updated counts in several places.

## Deploying

Connected to Vercel. Pushing to `main` redeploys automatically. No build settings
are needed since it is plain HTML.

## Affiliate disclosure

Participates in the Amazon Services LLC Associates Program. Product links are
affiliate links.
