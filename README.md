# Gerasimos Balatsoukas — Engineering Portfolio (website)

A single-page static website. No build tools, no frameworks. Open `index.html`
in a browser to preview locally, or follow the steps below to put it online.

```
portfolio-site/
├── index.html                     ← the whole page (text, layout, styling)
├── images/                        ← figures, headshot, and video posters
├── media/                         ← animations (mp4)
├── Gerasimos_Balatsoukas_CV.pdf   ← your CV (the CV buttons link to this)
└── README.md                      ← this file
```

## How the page works
- The **top buttons** switch between the landing page and each project. Only one
  shows at a time. If JavaScript is ever off, all sections simply show in a long
  scroll, so the page is never blank.
- Each figure is a **thumbnail**. Click it to open a large version with a caption
  beneath, like a figure in a paper. **Animations are thumbnails too** — clicking
  one plays it, looping and muted.

## Editing (no coding needed)
- **Colours / fonts:** edit the `:root { }` block near the top of `index.html`.
- **Text:** find the project (banners like `PROJECT 4 — GENERATOR`) and type over it.
- **A figure caption:** change the `data-cap="Figure X. ..."` on that figure.
- **Add an image figure:** drop the file in `images/`, then copy a `<figure>` block:
  ```html
  <figure class="fig" data-type="image" data-src="images/my-pic.png"
          data-cap="Figure X. My caption.">
    <img src="images/my-pic.png" alt="short description">
  </figure>
  ```
- **Add an animation (mp4 or gif):** drop the clip in `media/`, add a still frame
  (poster) in `images/`, then:
  ```html
  <figure class="fig fig-video" data-type="video" data-src="media/my-clip.mp4"
          data-cap="Figure X. My caption.">
    <img src="images/my-clip-poster.png" alt="short description">
    <span class="play">&#9658;</span>
  </figure>
  ```
  For a `.gif`, set `data-type="gif"` and point `data-src` at the `.gif`.
  (Tip: mp4 is far smaller than gif. The animations here were converted from your
  gifs/clips with ffmpeg, audio stripped, set to loop on click.)
- **Add a whole project:** copy a `<section class="view"> ... </section>` block,
  give it a new `id`, and add a matching menu button with the same `data-view`.

## Save-as-PDF button
The **Save PDF** button opens the browser print dialog — choose *Save as PDF*. The
print layout shows **all projects** (not just the open one), keeps every figure, and
hides the menu and buttons. Animations can't print, so their poster frame prints
instead, which is why each animation keeps a still poster.

## Replace your CV
The CV buttons open `Gerasimos_Balatsoukas_CV.pdf` in this folder. Replace that file
(keep the name) to update it.

## Publish / update with GitHub Pages (~3 minutes)
1. In your repository, make sure `index.html`, `images/`, `media/` and the CV sit at
   the **top level** (the repo root), **not** inside an extra folder. This is the most
   common reason a deploy shows nothing.
2. **Settings → Pages → Build and deployment.** Using the Actions workflow you set up,
   set **Source: GitHub Actions**. (Or use **Deploy from a branch → main → /(root)**.)
3. Commit. Check the **Actions** tab for a green tick, then open the URL shown in
   Settings → Pages. Updating later is just uploading the changed files again.
