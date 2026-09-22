# Configurable academic website — bshepherd.ca visual style

This is a plain static HTML/CSS/JavaScript site designed to reproduce the visual language of the `bshepherd.ca` archive supplied by the user while keeping **your content separate from the layout**.

There is no Ruby, Jekyll, Bundler, Node, npm, or build step.

## 1. Customize your information

Edit the files in `config/`:

- `config/site.js` — name, site description, navigation, and background image
- `config/research.js` — research intro, tags, and publications
- `config/courses.js` — teaching
- `config/students.js` — students
- `config/events.js` — events/workshops
- `config/contact.js` — address, email, links, CV
- `config/bio.js` — biography and portrait

Most normal updates only require changing those configuration files.

## 2. Replace the two placeholder images

Put your own wide background photograph in `assets/images/`, for example:

```
assets/images/background.jpg
```

Then change `backgroundImage` in `config/site.js`:

```js
backgroundImage: "assets/images/background.jpg",
```

For your portrait, put (for example) `assets/images/me.jpg` in the site and update `config/bio.js`:

```js
image: "../assets/images/me.jpg",
```

## 3. Add your CV

Put your CV at:

```
assets/files/cv.pdf
```

The sample config already points there.

## 4. Preview locally (optional)

Because the config is loaded as normal JavaScript, you can also simply double-click `index.html` and most browsers will render the site. For the most reliable local preview, if you already have Python 3:

```bash
python3 -m http.server 8000
```

then open `http://localhost:8000`.

Local preview is optional; GitHub Pages needs no local software.

## 5. Publish with GitHub Pages

Create a repository named `YOURUSERNAME.github.io`, copy these files into it, and push to the `main` branch.

In GitHub:

1. Open the repository.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, select **Deploy from a branch**.
4. Choose `main` and `/ (root)`.
5. Save.

Your site will be available at `https://YOURUSERNAME.github.io/`.

If you use a project repository instead (for example `academic-site`), the relative paths in this template also work at `https://YOURUSERNAME.github.io/academic-site/`.

## Style notes

The core measurements/colors were reconstructed from the supplied saved copy of `bshepherd.ca`, including:

- Raleway body/navigation type
- Roboto Slab headings/name
- `#F9F9F9` page background
- `#026B7E` link accent
- `#7E5F4E` section-heading accent
- translucent navy navigation panel `rgba(29,53,83,.85)`
- 5rem home navigation-panel padding
- 13.5% right offset
- uppercase navigation with 2px letter spacing
- full-screen photographic home background
- fixed 35% photographic sidebar layout for inner pages

The original site's personal content and background photograph are **not** included. Replace the supplied placeholders with your own assets.


## Local preview

You can open `index.html` directly in a browser. Navigation links explicitly target files such as `students/index.html`, so direct `file://` browsing works without showing directory listings.

For a browser environment closer to GitHub Pages, you can also run a tiny local server if Python 3 is installed:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000/`.

## Typography

This version uses **Cabin** site-wide, matching the typeface used by the Andreas Viklund 1024px-style academic website referenced in the customization request. The font is loaded through Google Fonts in `assets/css/fonts.css`.

To change it later, edit `assets/css/fonts.css` and the two `font-family` declarations near the top of `assets/css/main.css`.



## Responsive navigation

On screens 900px wide or narrower, the large photographic sidebar is replaced by a compact navy top navigation bar. At phone widths the navigation links wrap into a small grid. The desktop layout is unchanged.

### Responsive navigation

At widths of 900px and below, inner pages use a compact rectangular navy header. The desktop angled sidebar is explicitly disabled at these widths, so there is no diagonal/sloped right edge on tablets or phones.



## Chinese typography (楷体)

This version keeps **Cabin** for Latin text and automatically uses **草书/brush cursive** for Chinese characters. No special markup is required. The CSS checks common local font names on macOS and Windows: `Liu Jian Mao Cao SC`, `STLiu Jian Mao Cao`, `KaiTi`, and `楷体`.

The font configuration is in `assets/css/fonts.css`; the main font stack is in `assets/css/main.css`.

## Chinese font note

This version uses Cabin for Latin text and a direct native Liu Jian Mao Cao stack for Chinese:

```css
font-family: "Cabin", "Liu Jian Mao Cao SC", "STLiu Jian Mao Cao", "KaiTi", "KaiTi_GB2312", "BiauKai", "DFKai-SB", "楷体", serif;
```

Because Cabin has no Chinese glyphs, the browser automatically moves to the first installed Liu Jian Mao Cao family for Chinese characters. On macOS, `Liu Jian Mao Cao SC` or `STLiu Jian Mao Cao` is preferred; on Windows, `KaiTi` / `楷体` is preferred.

## Chinese font behavior

Chinese text is automatically wrapped in a `.zh-caoshu` span at runtime and is
assigned `Liu Jian Mao Cao SC` / `STLiu Jian Mao Cao` / `KaiTi` directly. This avoids Chromium using a
sans-serif CJK fallback for mixed strings such as `潘宇冲 Yuchong Pan`.

## Chinese calligraphy font

This package uses **Long Cang (龙藏体)** for Chinese characters and **Cabin** for Latin text. Long Cang has a a handwritten Chinese calligraphy style from Google Fonts. Chinese text is rendered in Long Cang while Latin text remains Cabin.

Chinese runs are detected automatically by JavaScript and wrapped in `.zh-caoshu`, so mixed names such as `潘宇冲 Yuchong Pan` require no special markup.

The primary Chinese font is loaded from Google Fonts. If it is unavailable, the CSS falls back to `Xingkai SC`, `STXingkai`, `华文行楷`, and finally generic `cursive`.
