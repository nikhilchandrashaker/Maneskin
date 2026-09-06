# Måneskin — A History

A small data/coding project tracing Måneskin's rise from busking on the streets of Rome to a Eurovision win and a Grammy nomination, told through an interactive timeline and three charts.

## What's in here

```
maneskin_timeline.html        interactive HTML page (timeline + charts, single file)
charts/
  01_spotify_growth.svg / .png     monthly Spotify listeners, Apr–Dec 2021
  02_album_reach.svg / .png        album chart peaks by market, 2018–2023
  03_eurovision_vote.svg / .png    jury vs. televote at Eurovision 2021
dataset/
  band_timeline.csv                key events, 2015–2024
  spotify_monthly_listeners.csv    data behind chart 1
  album_chart_peaks.csv            data behind chart 2
  eurovision_2021_final.csv        data behind chart 3
README.md                     this file
```

- **`maneskin_timeline.html`** is self-contained — open it in any browser. It has its own inline copies of the three charts as SVG, so it doesn't depend on the files in `charts/`.
- **`charts/*.svg`** are the same three charts as standalone, editable vector files (open in a browser, Illustrator, Inkscape, Figma, etc.).
- **`charts/*.png`** are flattened raster exports of the SVGs, rendered at 2.5x scale (1600px wide) for use in slides, docs, or social posts.
- **`dataset/*.csv`** is the raw data behind every number in the charts and the timeline, so you can re-plot it, check it, or extend it yourself.

## The three charts

**Fan support before and after Eurovision** — Måneskin's monthly Spotify listeners went from 2.4 million right before the Eurovision final to a peak of 50.3 million five weeks later, before settling around 29 million by the end of 2021.

**How far each album travelled** — Chart peak positions in Italy, the UK, and the US for all three studio albums. The 2018 debut never charted outside Italy; by 2023's *Rush!*, they were Top 5 in the UK and had entered the Billboard 200 in the US for the first time.

**The night the televote decided it** — Italy was only 4th place after Eurovision juries voted (208 points). The public televote — worth half the final score — gave them 316 more points and the win, 524 total.

## Sources

- Band history and timeline: Wikipedia (Måneskin), MusicBrainz, Eurovision Song Contest Wiki, Official Charts Company
- Album chart peaks: [Måneskin discography — Wikipedia](https://en.wikipedia.org/wiki/M%C3%A5neskin_discography) (citing FIMI, Official Charts Company, Billboard)
- Spotify monthly listeners: Chartmetric's 2021 H1 report, Music Business Worldwide, Music Ally, Music Week, and the Stream & Destroy newsletter — all published between July and December 2021
- Eurovision 2021 jury/televote breakdown: official Eurovision Song Contest 2021 results (Rotterdam Ahoy, 22 May 2021), reported by ABC News and ESCplus

Some Spotify listener figures (particularly the December 2021 data point) are approximate, as reported in contemporary press coverage rather than pulled from Spotify's own historical API.

## Regenerating the PNGs

The PNGs were rendered from the SVGs with [CairoSVG](https://cairosvg.org/):

```bash
pip install cairosvg
python3 -c "import cairosvg; cairosvg.svg2png(url='charts/01_spotify_growth.svg', write_to='charts/01_spotify_growth.png', scale=2.5)"
```

The SVGs reference two Google Fonts (Big Shoulders Display, Source Serif 4). If you re-render and see a fallback font, install those families first — the HTML file loads them automatically from Google Fonts, but local SVG-to-PNG rendering needs them installed on your system.
