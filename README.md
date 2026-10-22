# sparkly-high-z

Website for **Sparkly**, a monthly online meeting series on star clusters in galaxies across redshift.

Live site: <https://lmowla.github.io/sparkly-high-z/>

The site is built by GitHub Pages with [Jekyll](https://jekyllrb.com/) and the Minima theme. Nothing needs to be installed to edit it: change a file on GitHub, commit, and the site rebuilds within a minute or two.

## Editing pages

| What you want to change | File |
| --- | --- |
| Front page text, "next meeting" note | `index.md` |
| About page | `about.md` |
| Organizers list | `organizers.md` |
| How to join, mailing list, Zoom policy | `join.md` |
| Site title, tagline, navigation order | `_config.yml` |

Pages are written in Markdown. Keep the block between the `---` lines at the top of each file (the "front matter") as it is; edit the text below it.

## Adding a meeting

1. Copy `_meetings/TEMPLATE.md` to a new file in `_meetings/` named `YYYY-MM-short-title.md`, for example `_meetings/2026-12-speaker-name.md`.
2. Fill in the front matter: `title`, `date` (with time in UTC), `speaker`, `affiliation`, and `status`.
3. Write the abstract below the front matter.
4. Set `published: true` (or remove the line) when the entry is ready to appear.

The Meetings page lists entries automatically: those with `status: upcoming` appear under "Upcoming" and those with `status: held` or `status: cancelled` under "Past". After a meeting, change `status` to `held` and add `recording` and `slides` links if the speaker agrees.

The Zoom link is normally sent to the mailing list rather than posted; leave `zoom` empty unless the meeting is public.

## Previewing locally (optional)

Requires Ruby and Bundler.

```sh
bundle install
bundle exec jekyll serve
```

Then open <http://localhost:4000/sparkly-high-z/>.

## Publishing

In the repository settings on GitHub, under **Pages**, set the source to deploy from the `main` branch (root folder). The `url` and `baseurl` in `_config.yml` must match the repository owner and name.
