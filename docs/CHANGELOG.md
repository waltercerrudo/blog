---
title: CHANGELOG
layout: default
nav_exclude: true
---

## Release v0.4.0

We're so excited to release Just the Docs `v0.4.0`. This release has been almost a year in the making - after our new maintenance team has taken over the project, we've added two years of backlogged features and bugfixes to modernize the theme. This CHANGELOG will summarize some of the key changes, discuss migrations strategies, and outline broad future plans for this theme.

### Brief Overview - Highlighted Changes

`v0.4.0` contains many new features and bugfixes. We enumerate all of them in further sections in this changelog; however, we'd like to call out some of the most-requested changes:

- better support for dark theme: dark highlighting, search input color
- [callouts](https://just-the-docs.com/docs/ui-components/callouts/), a new design component to highlight content
- [configuring mermaid.js](https://just-the-docs.com/docs/ui-components/code/#mermaid-diagram-code-blocks), a markdown-native diagram visualization library
- [copy code button](https://just-the-docs.com/docs/ui-components/code/#copy-button) for code snippets
- external navigation links
- major improvements to nav generation efficiency and robustness
- minor improvements to built-in accessibility (SVG icons, nav titles, skip to main content)
- [modularized site components](https://just-the-docs.com/docs/customization/#custom-layouts-and-includes) (advanced feature)
- [new custom includes](https://just-the-docs.com/docs/customization/#override-includes): table of contents heading, navigation panel footer, search placeholder, lunr search indices
- bugfixes involving WEBrick and Ruby 3, Liquid processing in CSS comments, nested task lists, relative URLs, scroll navigation, corrupted search data from rake, breadcrumbs, and more!
- more documentation for [custom includes](https://just-the-docs.com/docs/customization/#override-includes), this changelog, and the [migration guide](https://just-the-docs.com/MIGRATION/)

*After usage instructions and the roadmap, we enumerate all changes from `v0.3.3`.*

### Using Release `v0.4.0`

Unlike pre-releases, `v0.4.0` is a new semver minor release for the theme. That means that users who have not pinned the theme version will be **automatically upgraded to `v0.4.0` the next time they build their site**.

To use this release explicitly as a remote theme:

```yml
remote_theme: just-the-docs/just-the-docs@v0.4.0
```

To use this RC explicitly as a gem-based theme, pin the version in your `Gemfile` and re-run `bundle install` or `bundle update just-the-docs`:

```ruby
gem "just-the-docs", "0.4.0"
```

If you would prefer to not upgrade, you can enforce that explicitly:

1. pin your gem version in your `Gemfile`, like so
```ruby
gem "just-the-docs", "0.3.3"
```
2. freeze the `remote_theme`, like so
```yml
remote_theme: just-the-docs/just-the-docs@v0.3.3
```

### Migration Guide and Strategies

We've developed a new [migration guide](https://just-the-docs.com/MIGRATION/) for users to migrate from version `v0.3.3` to `v0.4.0`. It outlines major changes in project maintenance (e.g. new repository link, team) as well as breaking changes that may break your site (and potential solutions). We suggest that all users refer to the guide before manually upgrading their site.

**For the vast majority of users, we do not anticipate that this will be a breaking change.** The major touch points are surrounding new includes, navigation (ordering, pages, and collections), the favicon, and a shift to relative URLs. However, users who heavily customize the theme (primarily by overriding includes) will likely have to make minor changes.

Given the length of features added in this release, users may want to incrementally upgrade through the pre-releases. To follow this approach, read this changelog from `v0.4.0.rc1` to `v0.4.0.rc5`; this breaks down the release into small chunks, each of which should be easier to upgrade. `v0.4.0.rc5` is identical to this release.

For support with migrating to `v0.4.0`, [open an issue](https://github.com/just-the-docs/just-the-docs/issues) or [start a discussion](https://github.com/just-the-docs/just-the-docs/discussions) and let us know!

### Roadmap (What's Next?)

Moving forward, we plan to release more frequently with smaller, bite-sized changes. This should make it easier for users to upgrade in the future!

Broadly, many features are still on the radar. We anticipate the rest of `v0.4.x` to be bugfixes surrounding this new release.

For version `v0.5`, our roadmap includes:

- a theme toggle (light/dark mode), with automatic theme switching based on browser preferences
- better GDPR compliance for analytics
- multi-level/recursive navigation (unlimited hierarchy of child pages)

In future versions, we also plan on:

- adding better dark theme defaults
- adding better internationalization support
- exploring offline PDF generation
- improving accessibility within the theme
- improving search functionality
- refactoring and improving the robustness of our codebase

Have ideas for what's next, or want to get involved? [Open an issue](https://github.com/just-the-docs/just-the-docs/issues) or [start a discussion](https://github.com/just-the-docs/just-the-docs/discussions) and let us know! We're looking for more contributors and maintainers to help us develop the theme.

### New Features

- Added: Combination by [@pdmosses] in [#578]
  - Added: dark highlighting in [#463]
  - Added: pages and collections in [#448]
  - Added: callouts in [#466]
  - Fixed: breadcrumb behaviour … by [@AdityaTiwari2102] in [#477]
  - Fixed: prevent rake command corrupting search data in [#495] (also listed below)
  - Fixed: nested lists in [#496]
  - Fixed: set color for search input in [#498] (also listed below)
  - Fixed: sites with no child pages (no PR)
  - Fixed: TOC/breadcrumbs for multiple collections in [#494]
  - Added: collection configuration option `nav_fold` (no PR)
  - Fixed: indentation and color for folded collection navigation (no PR)
  - Fixed: scroll navigation to show the link to the current page in [#639]
  - Fixed: Replace all uses of `absolute_url` by `relative_url`, by [@svrooij] in [#544]
- Added: custom favicon `_includes` by [@burner1024] in [#364]
- Added: set color for search input by [@pdmosses] in [#498]
- Added: search placeholder configuration by [@mattxwang] in [#613]
- Added: 'child_nav_order' front matter to be able to sort navigation pages in reverse by [@jmertic] in [#726]
- Added: `nav_footer_custom` include by [@nathanjessen] in [#474]
- Added: style fixes for jekyll-asciidoc by [@alyssais] in [#829]
- Added: mermaid.js support by [@nascosto] in [#857]
- Added: support for external navigation links by [@SPGoding] in [#876]
- Added: refactor `mermaid` config to use `mermaid_config.js` include, only require `mermaid.version` in `_config.yml` by [@mattxwang] in [#909]
- Added: accessible titles to nested page nav toggle by [@JPrevost] in [#950]
- Added: better title styling for AsciiDoc examples by [@alyssais] in [#944]
- Added: docs for custom search placeholder by [@mattxwang] in [#939]
- Added: provide ability to skip to main content by [@JPrevost] in [#949]
- Added: styling for `<blockquote>` by [@mattxwang] in [#965]
- Added: custom include for TOC heading by [@pdmosses] in [#980]
- Added: experimental nav optimization for simple cases by [@pdmosses] in [#992]
- Added: support multiple Google Analytics tracking IDs, document UA -> GA4 switch by [@MichelleBlanchette] in [#1029]
- Added: copy code button to code snippets by [@simonebortolin] in [#945]
- Added: restore simple configuration of `favicon.ico` via `site.static_files` by [@pdmosses] in [#1095]
- Added: modularize site components by [@mattxwang] in [#1058]
- Added: includes for custom `lunr` Liquid and JS code by [@diablodale] in [#1068]
- Added: new `_sass/custom/setup.scss` for variable definition by [@mattxwang] in [#1135]
- Added: configuration key to load a local version of mermaid by [@fabrik42] in [#1153]

### Bugfixes

- Fixed: prepend `site.collections_dir` if exists by [@alexsegura] in [#519]
- Fixed: nested task lists (#517) by [@pdmosses] in [#855]
- Fixed: suppress Liquid processing in CSS comments by [@pdmosses] in [#686]
- Fixed: prevent rake command from corrupting search data by [@pdmosses] in [#495]
- Fixed: anchor heading links should be visible on focus by [@jacobhq] in [#846]
- Fixed: add `overflow-x: auto` to `figure.highlight` by [@iridazzle] in [#727]
- Fixed: add `overflow-wrap: word-break` to `body` by [@iridazzle] in [#889]
- Fixed: vertical alignment for consecutive labels by [@Eisverygoodletter] in [#893]
- Fixed: allow links to wrap by [@pdmosses] in [#905]
- Fixed: nav scroll feature and absolute/relative URLs by [@pdmosses] in [#898]
- Fixed: exclude `vendor/` in Jekyll config by [@manuelhenke] in [#941]
- Fixed: improve build time of navigation panel by [@pdmosses] in [#956]
- Fixed: spacing issue when search is disabled by [@henryiii] in [#960]
- Fixed: active grandchild link class by [@pdmosses] in [#962]
- Fixed: HTML validation issues (W3C validator) by [@mattxwang] in [#964]
- Fixed: link styling now uses `text-decoration` values by [@mattxwang] in [#967]
- Fixed: cleaning up Jekyll excludes by [@pdmosses] in [#985]
- Fixed: docs, narrow styling for code highlighting with line numbers by [@pdmosses] in [#974]
- Fixed: default syntax highlighting in custom color schemes [@pdmosses] in [#986]
- Fixed: incorrect disambiguation in generated TOCs by [@pdmosses] in [#999]
- Fixed: duplicated external links in collections by [@pdmosses] in [#1001]
- Fixed: import order of `custom.scss`; puts at end by [@deseo] in [#1010]
- Fixed: top-level active link styling by [@pdmosses] in [#1015]
- Fixed: external links for sites with no pages by [@pdmosses] in [#1021]
- Fixed: duplicate `title` if `jekyll-seo-tag` not in users's plugins by [@Tom-Brouwer] in [#1040]
- Fixed: removes (duplicate) `favicon.html`, shifts content to `head_custom.html` by [@mattxwang] in [#1027]
- Fixed: add `reversed`, deprecate `desc` for nav `child_nav_order` by [@jmertic] in [#1061]
- Fixed: `child.child_nav_order` to `node.child_nav_order` by [@mattxwang] in [#1065]
- Fixed: remove all uses of `/` as SASS division by [@mattxwang] in [#1074]
    - note: this was originally merged as [#1074] with a bug; it was reverted in [#1076], and then reimplemented in [#1077]
- Fixed: skip nav collection generation when site has no pages by [@pdmosses] in [#1092]
- Fixed: standardize SCSS with `declaration-block-no-redundant-longhand-properties` by [@simonebortolin] in [#1102]
- Fixed: incorrect `padding` property value pair in `labels.scss` by [@SConaway] in [#1104]
- Fixed: various bugs with copy code button by [@simonebortolin] in [#1096]
- Fixed: replace inline styling for `<svg>` icons by [@captn3m0] in [#1110]
- Fixed: incorrect `padding` property value pair in `search.scss` by [@kevinlin1] in [#1123]
- Fixed: minor spacing and comment nits by [@EricFromCanada] in [#1128]
- Fixed: exclude images from being bundled with gem by [@m-r-mccormick] in [#1142]
- Fixed: dark theme code block background, line number colors by [@m-r-mccormick] in [#1124]
- Fixed: copy code button interaction with kramdown line numbers by [@mattxwang] in [#1143]

### Maintenance

- Added: VScode devcontainer by [@max06] in [#783]
- Added: `webrick` to `Gemfile` by [@mattxwang] in [#799]
- Added: 'This site is powered by Netlify.' to the footer by [@mattxwang] in [#797]
- Updated: new repo path by [@pmarsceill] in [#775]
- Updated: rename `master` -> `main` by [@pmarsceill] in [#776]
- Updated: README by [@pmarsceill] in [#777]
- Updated: Code of Conduct to Contributor Covenant v2.1 by [@mattxwang] in [#790]
- Updated: CI files, Ruby & Node Versions by [@mattxwang] in [#820]
- Updated: Stylelint to v14, extend SCSS plugins, remove primer-* configs, resolve issues by [@mattxwang] in [#821]
- Deleted: unused script directory by [@mattxwang] in [#937]
- Vendor: update `jekyll-anchor-headings`, `lunr.js` by [@mattxwang] in [#1071]

### Documentation

- Added: docs on how to break an `ol` by [@pdmosses] in [#856]
- Added: docs for custom includes by [@nathanjessen] in [#806]
- Added: document caveat about variable dependencies by [@waldyrious] in [#555]
- Added: docs on how to use `custom_head` to add a custom favicon by [@UnclassedPenguin] in [#814]
- Added: docs load mermaid.js by default by [@mattxwang] in [#935]
- Added: warning about mandatory `_`-prefix for collections by [@max06] in [#1091]
- Added:  migration guide by [@pdmosses] in [#1059]
- Added: label new features introduced in `v0.4` by [@mattxwang] in [#1138]
- Fixed: `ol` on `index.md` by [@pmarsceill] in [#778]
- Fixed: image link in Markdown kitchen sink by [@JeffGuKang] in [#221]
- Fixed: images in Markdown kitchen sink by [@dougaitken] in [#782]
- Fixed: clearer label of link to Jekyll quickstart by [@waldyrious] in [#549]
- Fixed: remove extra spaces in component docs by [@MichelleBlanchette] in [#554]
- Fixed: double "your" typo in `index.md` by [@sehilyi] in [#499]
- Fixed: "you" -> "your" typo in `index.md` by [@nathanjessen] in [#473]
- Fixed: spacing in toc example by [@henryiii] in [#835]
- Fixed: typo in `README` on `_config.yml` by [@ivanskodje] in [#891]
- Fixed: missing code fence in navigation structure docs by [@mattxwang] in [#906]
- Fixed: table of contents on search docs by [@robinpokorny] in [#940]
- Fixed: broken docs link (custom footer) by [@olgarithms] in [#951]
- Fixed: clarify version docs by [@pdmosses] in [#955]
- Fixed: typo in changelog links [@koppor] in [#1000]
- Fixed: two bugs in "Customization" (custom favicon, new annotation) by [@mattxwang] in [#1090]
- Fixed: "View Typography Utilities" link by [@agabrys] in [#1130]
- Fixed: broken relative page links by [@mattxwang] in [#1106]
- Fixed: clarify steps to add custom `lunr` index code by [@diablodale] in [#1139]
- Updated: homepage (focus: new features, conciseness, deduplication) by [@pdmosses] in [#1018]
- Updated: README (focus: new features, conciseness, deduplication) by [@pdmosses] in [#1019]
- Updated: `README` demo video by [@codewithfan] in [#1097]

### New Contributors

- [@AdityaTiwari2102] made their first contribution in [#477]
- [@svrooij] made their first contribution in [#544]
- [@alexsegura] made their first contribution in [#519]
- [@burner1024] made their first contribution in [#364]
- [@JeffGuKang] made their first contribution in [#221]
- [@dougaitken] made their first contribution in [#782]
- [@max06] made their first contribution in [#783]
- [@sehilyi] made their first contribution in [#499]
- [@nathanjessen] made their first contribution in [#473]
- [@waldyrious] made their first contribution in [#549]
- [@MichelleBlanchette] made their first contribution in [#554]
- [@henryiii] made their first contribution in [#835]
- [@jmertic] made their first contribution in [#726]
- [@jacobhq] made their first contribution in [#846]
- [@UnclassedPenguin] made their first contribution in [#814]
- [@alyssais] made their first contribution in [#829]
- [@nascosto] made their first contribution in [#857]
- [@SPGoding] made their first contribution in [#876]
- [@iridazzle] made their first contribution in [#727]
- [@ivanskodje] made their first contribution in [#891]
- [@Eisverygoodletter] made their first contribution in [#893]
- [@robinpokorny] made their first contribution in [#940]
- [@olgarithms] made their first contribution in [#951]
- [@manuelhenke] made their first contribution in [#941]
- [@JPrevost] made their first contribution in [#950]
- [@koppor] made their first contribution in [#1000]
- [@deseo] made their first contribution in [#1010]
- [@Tom-Brouwer] made their first contribution in [#1040]
- [@simonebortolin] made their first contribution in [#945]
- [@SConaway] made their first contribution in [#1104]
- [@captn3m0] made their first contribution in [#1110]
- [@kevinlin1] made their first contribution in [#1123]
- [@codewithfan] made their first contribution in [#1097]
- [@agabrys] made their first contribution in [#1130]
- [@diablodale] made their first contribution in [#1068]
- [@m-r-mccormick] made their first contribution in [#1142]
- [@fabrik42] made their first contribution in [#1153]
