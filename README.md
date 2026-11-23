# AIMH website

Source for **[ai-mh.github.io](https://ai-mh.github.io)**, the website of AIMH (AI for Mental Health). AIMH is a research community that builds natural language processing and broader AI methods for mental health. It releases open datasets, language models and shared tasks grounded in clinical practice.

- Models and datasets: [huggingface.co/AIMH](https://huggingface.co/AIMH)
- Code: [github.com/AI-MH](https://github.com/AI-MH)
- Community: [Discord](https://discord.gg/AhuspeXNkM)

## Pages

| File | Page |
| --- | --- |
| `index.html` | Home: mission, events, projects and contributors |
| `SQPsych.html` | Project page for *Roleplaying with Structure: Synthetic Therapist-Client Conversation Generation from Questionnaires* (SQPsychConv datasets, SQPsychLLM models) |

## Layout

```
index.html, SQPsych.html   pages
static/css/index.css       site theme (loaded after Bulma)
static/js/theme.js         light / night theme toggle
static/js/site.js          mobile nav, scroll reveal, BibTeX copy button
static/images/logos/       AIMH and partner logos
llms.txt, sitemap.xml, robots.txt
```

The site is plain static HTML with no build step. GitHub Pages serves `main` directly, and `.nojekyll` turns off Jekyll processing.

## Local preview

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

## Editing

- **Adding a project page:** copy `SQPsych.html` and keep the `<nav class="site-nav">` block and the `<head>` includes. Link the new page from the Projects section of `index.html`, and add it to `sitemap.xml` and `llms.txt`.
- **Colours:** every colour is a CSS variable at the top of `static/css/index.css`. Change it in the `:root` block for light mode, and in **both** night blocks (`@media (prefers-color-scheme: dark)` and `:root[data-theme="dark"]`) for night mode. Avoid hard-coding colours in rules or inline styles, or they will not switch with the theme.
- **Night theme:** by default the site follows the visitor's OS setting. The navbar button overrides it, and the choice is saved in `localStorage` under `aimh-theme`. `theme.js` must load synchronously in `<head>` before the stylesheets so the page does not flash the wrong theme.

## Acknowledgments

The visual style follows [OLA Research](https://github.com/OLAResearch/olaresearch.github.io). The page structure began from the [Academic Project Page Template](https://github.com/eliahuhorwitz/Academic-project-page-template), which adopted parts of [Nerfies](https://nerfies.github.io/).

## License

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />This website is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
