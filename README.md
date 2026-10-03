# louisjoyntdefouw.com

A static site (no build step, no dependencies) for Louis Joynt de Fouw, videographer.

## Before you publish

**Contact form.** The Contact button opens a short form, but since this is a
static site with no server, there's no way to submit it silently in the
background. On submit, it opens the visitor's email app with a message
pre-filled to `louis@louisjoyntdefouw.com`, using the mailto: link standard.
That's the honest no-backend version. If you'd rather have a true in-page
submission (no email app popping open), a service like Formspree
(formspree.io) has a free tier that works with a static site like this one,
just swap the form's submit handler for a fetch() call to their endpoint.

## Deploy with GitHub Pages (free, no subscription)

1. Create a new GitHub repository (e.g. `louisjoyntdefouw-site`). Public repos
   get free Pages hosting; private repos need a paid GitHub plan for Pages.
2. Upload every file in this folder to the repo, keeping the `projects/` and
   `assets/` folder structure intact.
3. In the repo, go to **Settings, Pages**.
4. Under **Build and deployment, Source**, choose **Deploy from a branch**,
   then pick the `main` branch and `/ (root)` folder. Save.
5. GitHub will give you a URL like `https://yourusername.github.io/repo-name/`.
   Confirm the site loads there first.
6. Still on the **Pages** settings screen, under **Custom domain**, enter
   `louisjoyntdefouw.com` and save. This writes the `CNAME` file already
   included here back into the repo automatically, you don't need to
   duplicate it.
7. In Squarespace DNS settings for `louisjoyntdefouw.com`, replace the four
   Adobe A records with GitHub Pages' A records instead:

   | Type | Host | Value           |
   |------|------|-----------------|
   | A    | @    | 185.199.108.153 |
   | A    | @    | 185.199.109.153 |
   | A    | @    | 185.199.110.153 |
   | A    | @    | 185.199.111.153 |
   | CNAME| www  | yourusername.github.io |

   (Double check these four IPs against GitHub's current docs at
   https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site
   before adding them, GitHub has changed these in the past.)
8. Wait for DNS to propagate (minutes to a day), then tick **Enforce HTTPS**
   back in the Pages settings once it becomes available, GitHub issues the
   SSL certificate automatically, same as Adobe did.
9. Once it's live, open Google Search Console, add the property, and request
   indexing for the homepage so Google doesn't have to find it on its own.

## File structure

```
index.html                              homepage (showreel, work list, about, contact)
style.css                               shared styles
CNAME                                   custom domain for GitHub Pages
assets/badges/                          festival badge images (add these)
projects/
  dlr-events.html                       Imagined Futures: A Live Art Series
  the-big-sing.html                     The Big Sing
  shan-tuyet.html                       Shan Tuyet Tea Production
  short-content.html                    Short Content
  adobe-after-effects.html              Adobe After Effects
  around-me-in-the-here-and-now.html    Around me, in the here and now
```

## Editing content

Each project page is a plain HTML file, edit text directly, or add another
`.html` file in `projects/` and link it from the work list in `index.html`
to add a new project.
