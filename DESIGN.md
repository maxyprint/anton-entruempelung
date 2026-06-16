# DESIGN.md — Anton - Entrümpelung und Transport e.U.

## 1. Visual Theme
Ton: "Zuverlässig-lokal, unkompliziert, anpackend — Wien 10"
Differenzierung: Dunkles Tannengrün statt dem üblichen Orange-auf-Weiß der Konkurrenz. Sauber, klar, persönlich — "Anton" klingt nach jemandem, dem man vertraut.
Nicht: Kein Corporate-Orange, kein Stock-Foto-Look, keine generische Handwerker-Site.

## 2. Color Palette (CSS Custom Properties)
--color-primary:    #1E3A2F  /* Dunkles Tannengrün — Vertrauen, Sauberkeit */
--color-secondary:  #F4EFE6  /* Warmes Cremeweiß — Wärme, Lokalität */
--color-accent:     #E07B39  /* Bernstein-Orange — CTAs, Notfall, Dringlichkeit */
--color-text:       #1A1A1A
--color-text-light: #6B7280
--color-border:     #E0DAD1
--color-emergency:  #C8392B  /* Für Notfall-Bar + Notfall-Block */

REGEL: Kein einziger Hex-Wert im HTML oder CSS außer in dieser Datei.
Alle Styles nutzen ausschließlich var(--color-*).

## 3. Typography
--font-head: 'Space Grotesk', sans-serif  /* Headlines, Buttons — modern, urban */
--font-body: 'Inter', sans-serif          /* Fließtext — klar, gut lesbar */

Google Fonts URL: https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;600;700&family=Inter:wght@400;500;600&display=swap

--text-scale-hero: clamp(2.2rem, 5vw, 3.8rem)
--text-scale-h2:   clamp(1.6rem, 3vw, 2.4rem)
--text-scale-h3:   clamp(1.1rem, 2vw, 1.4rem)
--text-scale-body: 1rem
--text-scale-small: 0.875rem

## 4. Component States
Buttons:  default → hover (translateY(-2px) + shadow) → active (scale 0.98)
Cards:    default → hover (translateY(-4px) + shadow-lg)
Links:    color → accent color + underline
Nav-CTA:  accent-bg → accent-dark (#C46B2D)

## 5. Layout Principles
- Grid: max-width 1100px, auto-margins
- Leistungen: Bento-Grid (featured span-2 + 3 normale)
- Über-uns: 2-col (portrait links, text rechts)
- Kontakt: 2-col (info + maps links, formular rechts)
- Mobile-Breakpoint: 768px → alle Grids auf 1 Spalte
- Spacing-Scale: 8px base → 16 / 24 / 32 / 48 / 64 / 80px

## 6. Elevation & Depth
--shadow-sm: 0 2px 8px rgba(0,0,0,0.06)
--shadow-md: 0 4px 16px rgba(0,0,0,0.10)
--shadow-lg: 0 8px 32px rgba(0,0,0,0.14)
--radius-sm: 4px
--radius-md: 8px
--radius-lg: 12px

## 7. Animation Tier: L2
L2 Pflicht-Animationen:
  .animate            { opacity: 0; transform: translateY(28px); transition: 0.55s ease; }
  .animate.is-visible { opacity: 1; transform: translateY(0); }
  .animate-delay-1    { transition-delay: 0.10s; }
  .animate-delay-2    { transition-delay: 0.20s; }
  .animate-delay-3    { transition-delay: 0.30s; }
  IntersectionObserver threshold: 0.08, rootMargin: '0px 0px -30px 0px'

Hero: KEIN animate (sofort sichtbar)
Proof-Bar, Reviews, Cards, Über-uns, Notfall-Block: animate ✓

## 8. Design Guardrails
✅ Telefonnummer 0660 919 7350 auf JEDER Seite als tel: Link
✅ Notfall-Bar sticky (var(--color-emergency))
✅ WhatsApp-Button sticky rechts unten (#25D366)
✅ Hamburger-Menu auf Mobile
✅ Bento-Grid: 1 Featured (span-2) + 3 normale
✅ Google Maps Embed: Hebbelgasse 4/11, 1100 Wien
✅ Schema.org LocalBusiness auf index.html
✅ Open Graph Tags auf allen Seiten
✅ Favicon

❌ Kein Lorem ipsum
❌ Keine Placeholder-Öffnungszeiten
❌ Kein sed für HTML-Änderungen

## 9. Responsive Behavior
Mobile (≤768px):
  - .nav-links: display none
  - .hamburger: display flex
  - alle Grids: grid-template-columns: 1fr
  - .bento-card--featured: grid-column span 1
  - Sections: padding 56px 20px
  - Hero: margin-left/right 5%
