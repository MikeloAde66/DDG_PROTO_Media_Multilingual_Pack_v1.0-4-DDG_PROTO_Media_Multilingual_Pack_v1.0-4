
# DDG‑PROTO Media — Multilingual Pack v1.0

Included languages: Spanish (es), French (fr), Arabic (ar), Hindi (hi), Chinese Simplified (zh‑CN).

## Contents
- `<lang>/YANI_*.txt` — TTS scripts for ElevenLabs/Play.ht
- `<lang>/YANI_Subtitles_<lang>.srt` — Captions aligned to v2 timestamps
- `ui_strings.json` — UI labels for Elementor/JS i18n

## WordPress / Elementor Setup
1. **Language plugin:** Install WPML or Polylang. Create pages per language and assign hreflang.
2. **Fonts:** Use Google Noto family for broad glyph coverage. Add fallback for Arabic/Hindi/Chinese.
3. **RTL:** For Arabic pages, add `dir="rtl"` on the `<html>` tag or Elementor page settings.
4. **Audio per language:** Upload the rendered MP3 files and map buttons to each language’s audio IDs.
5. **Subtitles:** Attach the corresponding `YANI_Subtitles_<lang>.srt` in your player for that language.
6. **UI strings:** Load `ui_strings.json` and swap text by `lang` key. Example snippet:

```html
<script>
async function loadUI(lang){
  const res = await fetch('/wp-content/uploads/ui_strings.json');
  const dict = await res.json();
  document.querySelector('#headline').textContent = dict.headline[lang];
  document.querySelector('#cta-demo').textContent = dict.cta_demo[lang];
}
</script>
```
7. **SEO:** Add hreflang tags in the head:
```html
<link rel="alternate" hreflang="en" href="https://ddg.com/page" />
<link rel="alternate" hreflang="es" href="https://ddg.com/es/page" />
<link rel="alternate" hreflang="fr" href="https://ddg.com/fr/page" />
<link rel="alternate" hreflang="ar" href="https://ddg.com/ar/page" />
<link rel="alternate" hreflang="hi" href="https://ddg.com/hi/page" />
<link rel="alternate" hreflang="zh-cn" href="https://ddg.com/zh-cn/page" />
```
8. **Currency:** Show localized currency with the JS Intl API:
```html
<script>
function price(amount, locale, currency){
  return new Intl.NumberFormat(locale,{style:'currency',currency}).format(amount);
}
</script>
```

— End —
