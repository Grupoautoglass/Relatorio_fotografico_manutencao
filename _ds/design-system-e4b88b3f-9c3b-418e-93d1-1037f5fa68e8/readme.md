# Sally Design System

Sally is the shared design system of **Grupo Autoglass** — the visual and interaction language behind its internal products. This project is a code recreation of the Sally kit: tokens, iconography, brand marks, reusable components and a working product screen.

## Sources

- Figma: **Sally Design System.fig** — the full library (brand identity, colour palettes, typography, iconography, and 241 component sets). Attached as a mounted file; no public URL was provided.
- Figma: **Figma jLaavYSuZvHYDtr7ofBDBE.fig** — the "Consulta e Gerenciamento de CEP" flow (5 frames) built on the Sally library. This file is the source of every component and token currently implemented here.

Both files are the authority for values in this project. Where the code and a published convention disagree, the file wins.

## Products represented

One product surface is represented so far: an internal **Consulta e Gerenciamento de CEP** tool — search Brazilian postal addresses, register new CEPs, sort and paginate results. Copy is Brazilian Portuguese.

## Content fundamentals

- **Language**: Brazilian Portuguese throughout. English survives only in component names inside Figma, never in the UI.
- **Voice**: second person, formal-neutral imperative. Instructions address the user directly: "Busque por endereços brasileiros", "Busque e selecione um endereço para cadastrar um novo CEP no banco de dados da empresa."
- **Casing**: sentence case everywhere — page titles ("Consulta e Gerenciamento de CEP" is the exception, title-cased), buttons ("Novo cadastro", "Consultar", "Limpar", "Salvar", "Voltar"), labels ("Localidade/UF", "Bairro/Distrito", "Logradouro/Nome"). Never all-caps, never ALL-CAPS micro-labels.
- **Buttons** are one or two words, verb-first. No "Clique aqui", no trailing punctuation.
- **Feedback copy** is a short noun-phrase title plus one explanatory sentence ending in a period: "CEP não encontrado" / "O CEP informado não foi encontrado em nossa base de dados. Por favor, realize o cadastro para continuar."
- **Counts** are spelled as full sentences: "Mostrando 20 de 20 itens".
- **No emoji.** No exclamation marks. No first person.
- Placeholders show the shape of the answer, not an instruction: "00000000", "Digite o CEP, nome da rua, avenida...".

## Visual foundations

**Colour.** Brand blue rgb(10,100,255) is the action colour; rgb(13,75,215) is the darker chrome blue used for the Navbar and semantic borders; rgb(224,237,254) is the tint used for secondary buttons, selected table rows and info alerts. Ink is rgb(27,30,43) for body text and rgb(12,13,21) for page titles; secondary text is rgb(99,106,121); disabled is rgb(126,134,150). Structure lines are rgb(221,223,228). Two surface neutrals only: page background rgb(231,236,244) and the zebra/tertiary fill rgb(246,246,251); cards are pure white. Semantics: success rgb(35,113,38) on rgb(217,242,231), danger rgb(194,52,43), warning rgb(245,94,9).

**Type.** Onest at four weights — Light 300 (Navbar dividers), Regular 400 (body, buttons, inputs, cells), Medium 500, SemiBold 600 (titles, table headers, alert titles). Scale in use: 24px/1.2 page and section titles, 20px/1.5 filter and alert titles, 16px/1.5 the workhorse size for body, inputs, buttons and table cells, 14px/1.5 breadcrumbs, subtitles and counts, 12px/1.5 badges. No serif, no mono.

**Spacing and layout.** 1440×900 desktop canvas. Page content sits in a 32px padded column with 24px between blocks. Cards use 24px padding (filter) or 24px/32px (tables). Field rows gap 16px; button groups gap 8px or 16px. Inputs are 44px tall, buttons 40px, table headers 56px, data rows 44px, the Navbar 56px, the table footer 60px.

**Corners.** 4px on buttons and pagination cells, 8px on cards, inputs and alerts, 32px on the Navbar, fully round (3600px) on avatars and circular badges. Nothing else.

**Borders and shadows.** The system draws borders as inset box-shadows: `inset 0 0 0 1px rgb(221,223,228)` on inputs and cells, `inset 0 0 0 1px rgb(13,75,215)` on info alerts, `inset 0 0 0 0.5px rgb(238,238,238)` for the hairline inside the filter card. Cards carry no drop shadow — they separate from the rgb(231,236,244) page by fill alone. The only real elevation in use is the floating save-confirmation, `0 8px 24px rgba(141,144,165,0.2)`.

**Backgrounds.** Flat colour only. No gradients, no photography, no illustration, no pattern or texture in the source.

**States.** Hover darkens a fill slightly (about 6–8% brightness) and keeps geometry fixed — nothing scales or lifts. Press is a further darkening, not a shrink. Disabled swaps a primary fill for rgb(126,134,150) and drops the pointer cursor. Selected table rows fill rgb(224,237,254); checked boxes fill rgb(10,100,255). Focus keeps the native outline off and relies on the field border.

**Motion.** Almost none. Filter collapse and screen changes are instant. The one animation is the confirmation feedback, a 220ms ease-out fade with a 12px upward slide. No bounce, no spring, no loaders in this flow.

**Transparency and blur.** Not used. Every surface is opaque; the only alpha values in the system are inside the shadow colour.

**Imagery.** None in the source. Avatars are typographic — an initial in blue on rgb(224,237,254) — so no photo, illustration or generic stock placeholder belongs in a Sally screen.

## Iconography

Icons come from the kit itself: 21 glyphs materialized out of the Figma file into `assets/icons/icon-data.js` and rendered through `<Icon name="…" size={…} />`. They are solid/regular single-path FontAwesome-family glyphs on a 32×32 box, painted with `currentColor`, used at 14px (pagination), 16px (buttons, fields, filter header), 20px (Navbar icon buttons) and 24px (alerts, filter toggle). Available: Search, Filter, Sort, PlusSolid, ArrowRotateLeft, AngleUp, AngleDown, AngleLeft, AngleRight, CaretLeft, CaretRight, ChevronLeftSolid, IconCheck, Xmark, CirculoInformacaoSolido, HouseChimneySolid, Gear, BellRegular, UserSolid, plus the two brand marks LogoGrupoAutoglassWhiteTypeWhite and LogoAutoglassWhiteTypeWhite.

No icon font, no CDN set, no emoji, no unicode characters standing in for icons. `|` is used as a literal typographic divider in the Navbar — that is type, not an icon. When a glyph is missing, take it from the Figma file rather than substituting a library.

**Brand marks.** The Grupo Autoglass and Autoglass logos are extracted verbatim from the kit as single-colour vector data (`LogoGrupoAutoglass`, `LogoAutoglass`). They are white on brand blue and ink on light surfaces. Never redraw or recolour them beyond that single fill. The Sally wordmark itself ships in the larger Sally file as type, not as a separate mark file — `thumbnail.html` renders it in Onest SemiBold.

## Index

| File | What it is |
| --- | --- |
| `styles.css` | Global CSS entry point — imports every token and font file |
| `tokens/fig-tokens.css` | 751 tokens from the kit's variable collections, including dark and mobile scopes |
| `tokens/fig-typography.css` | Text style classes (the kit defines no named text styles) |
| `tokens/fonts.css` | Onest webfont |
| `assets/icons/` | `icon-data.js`, `Icon.jsx`, iconography card |
| `components/` | Reusable components, grouped by concern |
| `ui_kits/cep/` | Navigable recreation of the Consulta e Gerenciamento de CEP flow |
| `thumbnail.html` | Homepage tile |
| `SKILL.md` | Agent-skill entry point |

### Components

**core** — `Button`, `IconButtons`, `Badges`, `Input`, `CheckBox`, `Separator`, `Slot`, `SymbolAvatar`

**navigation** — `Navbar`, `Breadcrumb`, `ButtonFooter`, `Scroll`

**feedback** — `Alerts`

**data** — `Filter`, `FilterLine`, `Molecules`, `TableInColumn`, `TableFooter`, `SortTable`

**brand** — `LogoGrupoAutoglass`, `LogoAutoglass`

**icons** — `Icon`

### Naming

Component names follow the kit's own family names: `Alerts`, `Badges`, `IconButtons`, `SymbolAvatar` (Symbol (avatar) [1.0.0]), `TableInColumn` (Table in column [1.0.0]/Columns), `Molecules` (the table-cell atom), `Slot` (Slot [2.0.0]/Default) and `FilterLine` (.Filter [1.1.0]/Line).

### Intentional additions

- `Icon` — a wrapper over the glyph data extracted from the kit. The kit has no Icon component; components need one API to render its glyphs.

## UI kits

`ui_kits/cep/index.html` — the Consulta e Gerenciamento de CEP flow, navigable: filter and sort the registered list, land on the not-found state, open the new-registration screen, search the address base, select a row, save, and see the confirmation feedback.

## Gaps

- The larger **Sally Design System.fig** library (241 component sets, ~1951 icons, 542 variables across 9 collections) is only partially represented. What is here comes from the CEP flow file. The remaining families, the full icon set, and the Primitives/Modes/Scale/Space token collections still need importing.
- The kit defines no named Figma text styles, so `tokens/fig-typography.css` is empty and the type scale above is transcribed from the frames.
- Onest is loaded from Google Fonts, not from kit-supplied font binaries. If Grupo Autoglass licenses specific Onest files, drop them in and swap `tokens/fonts.css` for real `@font-face` rules.
