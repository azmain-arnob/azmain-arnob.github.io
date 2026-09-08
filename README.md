# Azmain Iqtidar Arnob — portfolio

Single-file portfolio site. No build step, no dependencies to install. `index.html`
carries the CSS, the JavaScript and both photos (embedded as base64), so the only
other file it looks for is `resume.pdf`.

## Publish it

1. Create a new public repository named exactly **`azmain-arnob.github.io`**.
2. Upload `index.html`, `resume.pdf` and this `README.md` to the root of the repo.
3. Go to **Settings → Pages**, set **Source** to `Deploy from a branch`, branch `main`, folder `/ (root)`, and save.
4. Wait a minute or two. The site is live at **https://azmain-arnob.github.io**.

If you'd rather keep the repo under another name, say `portfolio`, the same steps
work and the URL becomes `https://azmain-arnob.github.io/portfolio/`.

## Three things to change

All three live at the top of the `<script>` block near the end of `index.html`,
under the comment `things you may want to change`.

**1. The contact form.** Sign up at [formspree.io](https://formspree.io), create a
form, and paste the form ID into:

```js
var FORM_ENDPOINT = "https://formspree.io/f/YOUR_FORM_ID";
```

Until you do, the Send button falls back to opening the visitor's email app with
the message pre-filled, so nothing is broken in the meantime.

**2. Project links.** LabDesk, HAMS and VisionGuard currently link to your GitHub
profile because I couldn't find their repos. Search `View code` in `index.html`
and swap in the real URLs — Travelmate BD already points at its repo.

**3. The CV.** `resume.pdf` is the file the Download CV button serves. Replace it
whenever you update your CV, keeping the same filename.

## How it works

The portrait is a WebGL particle system: each of roughly 15,000 points takes its
colour from one pixel of your photo, with dark pixels pulled toward electric blue
so the hair and suit don't disappear against the navy background. A scan band
sweeps down the face every few seconds, matching the banner on the GitHub profile.

As you scroll, the same points morph between four shapes: your portrait, a
feed-forward neural network, an embedding space with four clusters, and a loss
surface. Each shape brightens when it is fully formed and dims while you read,
and the portrait returns on the contact section. Three.js r128 loads from cdnjs.

The GitHub numbers in the About section come from the public GitHub API on every
page load, so they stay current on their own. If the API rate-limits a visitor,
the numbers show a dash instead of breaking.

Everything degrades: no WebGL shows your photo instead of the particles, and
`prefers-reduced-motion` turns off the intro animation.
