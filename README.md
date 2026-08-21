# Stratford Writes — website

A plain static site. No build step, no framework, no dependencies. Five HTML files and one stylesheet.

```
index.html      Home
calendar.html   Google Calendar embed
about.html      About Us
resources.html  Resources
contact.html    Contact
style.css       Shared styles for all pages
```

To preview locally, just double-click `index.html`. Every page links to the others with plain relative links, so it works straight from a folder.

---

## 1. Fill in the placeholders

Search the folder for these and replace them:

| What | Where | Notes |
|---|---|---|
| `hello@stratfordwrites.ca` | `contact.html` — **5 occurrences** | Two `mailto:` hrefs and three bits of visible link text. Do a find-and-replace on the whole string. |
| Group history paragraph | `about.html`, under "Our story" | Marked with an *Editor's note* — replace and delete the note. |
| Meeting rhythm / length | `about.html`, "How a meeting works" | Written as a two-hour workshop format; adjust to what you actually do. |
| Local resources | `resources.html`, "Local" section | Marked with an editor's note — add bookshops, festivals, open mics, then delete the note. |
| `&copy; 2026` | Footer of all five pages | Update the year when it rolls over. |

### ⚠️ Read this before the site goes public

Two of the editor's notes are **visible on the live page**, not HTML comments — deliberately, so
they're impossible to miss, but that means visitors will read them if you publish first and edit
later. They are the yellow boxes on `calendar.html` and `resources.html`, plus the italic line
under "Our story" on `about.html`.

More importantly, **most of the body copy is invented placeholder written in the group's voice.**
It reads as fact but nobody has confirmed it. Specifically, these are all assumptions:

- "Free to attend" and "no application, no portfolio, no audition" (`about.html` fact list)
- The whole two-hour meeting structure and the "circulated a week ahead" convention
- "The group is intended for adults" (`contact.html` FAQ)
- "Members have published in journals and anthologies" (`about.html`)
- The four ground rules, including the confidentiality one
- "The one most members end up recommending" about *Bird by Bird* (`resources.html`)

Read every page start to finish and correct anything the group hasn't actually agreed to. The
confidentiality rule and the cost line are the two most worth getting right before strangers
read them as a promise.

---

## 2. Paste in the Google Calendar embed

1. Open **Google Calendar** on the web.
2. Go to **Settings** (gear icon) → under **Settings for my calendars**, pick the Stratford Writes calendar.
3. Under **Access permissions for events**, tick **Make available to public**. *(Without this, visitors see an empty box.)* Set the dropdown beside it to **See all event details** if you want event descriptions and locations visible.
4. Scroll to **Integrate calendar** and copy the **Embed code** — it's an `<iframe …>` tag.
5. Open `calendar.html` and search for the comment `GOOGLE CALENDAR EMBED`. Just below it, delete the `<div class="embed-placeholder"> … </div>` that sits inside `<div class="calendar-frame">`, and paste your iframe in its place. (There's a commented-out example iframe right underneath showing what the finished markup looks like.)
6. On the pasted `<iframe>`, **delete the `width="800"` and `height="600"` attributes**. The stylesheet makes it full-width and responsive, but only if those hard-coded sizes are gone.
7. Optional: add `title="Stratford Writes calendar"` to the iframe for screen readers.

Handy embed URL parameters you can append to the iframe's `src`:

- `&ctz=America%2FToronto` — force Eastern time (recommended).
- `&mode=AGENDA` — show a list of upcoming events instead of a month grid. Often reads better on phones.
- `&showTitle=0&showPrint=0&showTabs=0&showCalendars=0` — strip Google's chrome for a cleaner look.

---

## 3. Publish it

Any static host works. Two free options:

**GitHub Pages**

1. Create a repository and upload these files to the root of the `main` branch.
2. Repo **Settings → Pages** → Source: *Deploy from a branch* → `main` / `/ (root)`.
3. Your site appears at `https://<username>.github.io/<repo>/` within a minute or two.

**Netlify Drop**

1. Go to <https://app.netlify.com/drop>.
2. Drag the whole folder onto the page. It deploys immediately at a random subdomain you can rename in site settings.

**Custom domain** — both hosts let you point a domain you own (e.g. `stratfordwrites.ca`) at the site from their dashboard, with HTTPS included.

---

## Notes

- **Spam:** a plain `mailto:` address on a public page will get scraped eventually. If it becomes a problem, the usual fix is to switch the Contact page to a form service (Formspree or Netlify Forms) — say the word and it's a small change.
- **Adding a page:** copy any existing page, change the `<title>`, the `<h1>`, and move the `aria-current="page"` attribute in the nav to the new page's link. Then add that link to the nav on all the other pages.
- **Colours:** everything lives in the `:root` block at the top of `style.css`. Change `--green` and `--gold` and the whole site follows.
- **External links** on the Resources page were checked at build time; it's worth a quick click-through once a year.
