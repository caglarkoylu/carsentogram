# CarSenToGram

Geovisual text analytics for exploring spatiotemporal variation in public discourse on Twitter.

**Live app:** https://caglarkoylu.github.io/carsentogram/

The app shows tweets about immigration from before and after the 2017 U.S. travel ban as a
tile-grid cartogram of U.S. states, with topic, sentiment and weekly-distribution views.

> Koylu, C., Larson, R., Dietrich, B. J., & Lee, K.-P. (2019). CarSenToGram: geovisual text
> analytics for exploring spatiotemporal variation in public discourse on Twitter.
> *Cartography and Geographic Information Science*, 46(1), 57–71.
> https://doi.org/10.1080/15230406.2018.1510343

## About this deployment

The original React app was hosted at `ryan-p-larson.github.io/paper/`. Its source repository
was later replaced with a placeholder, so the original source code isn't available. This
deployment restores the **compiled production build** captured by the Internet Archive on
2020-09-19:

https://web.archive.org/web/20200919063532/https://ryan-p-larson.github.io/paper/

All data (state tiles, topics, sentiments, sample tweets) is embedded in the JavaScript
bundle, so the site is fully static.

### Changes from the archived build

The files in [`docs/`](docs/) are byte-for-byte the archived files, except:

- `docs/index.html`: asset paths changed from `/paper/...` to relative `./...`.
- `docs/static/js/main.243aca32.js`: two minimal patches
  - webpack public path `"/paper/"` → `"./"`
  - service-worker registration disabled (`if("serviceWorker"in navigator)` → `if(!1)`),
    because the original `service-worker.js` wasn't archived.
- `docs/.nojekyll` added so GitHub Pages serves the files as is.

External dependencies loaded at runtime: Bootstrap 3.3.7 CSS (maxcdn.bootstrapcdn.com) and
the Roboto font (Google Fonts).

## Hosting

GitHub Pages serves the site from the `main` branch, `/docs` folder.

To preview locally:

```bash
python -m http.server 8765 --directory docs
```
