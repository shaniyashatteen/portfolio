<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Shaniya Shatteen — Brand Marketing Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;0,700;1,400;1,500&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --ivory: #FAF8F5;
    --espresso: #1C1410;
    --gold: #C9A96E;
    --gold-light: #E8D9BE;
    --blush: #E8D5CC;
    --blush-deep: #C4A99E;
    --warm-gray: #8A7F78;
    --cream: #F2EDE7;
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Inter', sans-serif;
    background: var(--ivory);
    color: var(--espresso);
    font-size: 16px;
    line-height: 1.7;
    overflow-x: hidden;
  }

  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    padding: 1.25rem 3rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: rgba(250, 248, 245, 0.92);
    backdrop-filter: blur(8px);
    border-bottom: 1px solid rgba(201, 169, 110, 0.2);
    transform: translateY(-100%);
    transition: transform 0.5s ease;
  }
  nav.visible { transform: translateY(0); }
  .nav-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.1rem;
    letter-spacing: 0.05em;
    color: var(--espresso);
    text-decoration: none;
  }
  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a {
    font-size: 0.8rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--warm-gray);
    text-decoration: none;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--gold); }

  section { padding: 7rem 3rem; max-width: 1100px; margin: 0 auto; }

  .hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 0 3rem;
    max-width: none;
    position: relative;
    overflow: hidden;
  }
  .hero-bg-text {
    position: absolute;
    top: 50%;
    right: -2rem;
    transform: translateY(-50%);
    font-family: 'Playfair Display', serif;
    font-size: clamp(8rem, 18vw, 20rem);
    font-weight: 700;
    color: transparent;
    -webkit-text-stroke: 1px rgba(201, 169, 110, 0.12);
    line-height: 1;
    pointer-events: none;
    user-select: none;
    white-space: nowrap;
  }
  .hero-inner { max-width: 1100px; margin: 0 auto; width: 100%; position: relative; z-index: 1; }
  .hero-eyebrow {
    font-size: 0.75rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1.5rem;
    opacity: 0;
    transform: translateY(16px);
    animation: fadeUp 0.8s ease 0.2s forwards;
  }
  .hero-name {
    font-family: 'Playfair Display', serif;
    font-size: clamp(3.5rem, 8vw, 7.5rem);
    font-weight: 700;
    line-height: 1.02;
    letter-spacing: -0.02em;
    color: var(--espresso);
    opacity: 0;
    transform: translateY(24px);
    animation: fadeUp 0.9s ease 0.4s forwards;
  }
  .hero-name em {
    font-style: italic;
    color: var(--gold);
  }
  .hero-rule {
    width: 0;
    height: 2px;
    background: var(--gold);
    margin: 2rem 0;
    animation: expandRule 1s ease 1s forwards;
  }
  .hero-tagline {
    font-size: clamp(1rem, 2vw, 1.2rem);
    font-weight: 300;
    color: var(--warm-gray);
    max-width: 520px;
    opacity: 0;
    transform: translateY(16px);
    animation: fadeUp 0.8s ease 1.1s forwards;
  }
  .hero-cta {
    display: inline-flex;
    align-items: center;
    gap: 0.75rem;
    margin-top: 3rem;
    padding: 1rem 2rem;
    border: 1px solid var(--gold);
    color: var(--espresso);
    text-decoration: none;
    font-size: 0.8rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    transition: all 0.3s ease;
    opacity: 0;
    animation: fadeUp 0.8s ease 1.4s forwards;
  }
  .hero-cta:hover { background: var(--gold); color: var(--ivory); }
  .hero-cta svg { transition: transform 0.3s ease; }
  .hero-cta:hover svg { transform: translateX(4px); }

  @keyframes fadeUp {
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes expandRule {
    to { width: 80px; }
  }

  .section-label {
    font-size: 0.7rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1rem;
  }
  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 4vw, 3rem);
    font-weight: 500;
    line-height: 1.15;
    color: var(--espresso);
    margin-bottom: 1.5rem;
  }
  .section-title em { font-style: italic; color: var(--gold); }
  .section-body {
    font-size: 1rem;
    font-weight: 300;
    color: var(--warm-gray);
    max-width: 580px;
    line-height: 1.8;
  }

  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 5rem;
    align-items: center;
    margin-top: 4rem;
  }
  .about-portrait {
    aspect-ratio: 3/4;
    background: var(--cream);
    border: 1px solid var(--gold-light);
    display: flex;
    align-items: flex-end;
    padding: 2rem;
    position: relative;
    overflow: hidden;
  }
  .about-portrait-placeholder {
    position: absolute;
    inset: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 1rem;
  }
  .portrait-monogram {
    font-family: 'Playfair Display', serif;
    font-size: 5rem;
    font-weight: 700;
    color: var(--gold-light);
    line-height: 1;
  }
  .portrait-hint {
    font-size: 0.75rem;
    letter-spacing: 0.1em;
    color: var(--blush-deep);
    text-align: center;
  }
  .about-portrait-label {
    position: absolute;
    bottom: 1.5rem;
    left: 1.5rem;
    right: 1.5rem;
    background: rgba(250, 248, 245, 0.95);
    padding: 1rem 1.25rem;
    border-left: 2px solid var(--gold);
  }
  .about-portrait-label strong {
    display: block;
    font-family: 'Playfair Display', serif;
    font-size: 1rem;
    font-weight: 500;
    color: var(--espresso);
  }
  .about-portrait-label span {
    font-size: 0.75rem;
    color: var(--warm-gray);
    letter-spacing: 0.05em;
  }
  .about-content { }
  .about-stats {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
    margin-top: 2.5rem;
  }
  .stat-item { border-top: 1px solid var(--gold-light); padding-top: 1rem; }
  .stat-number {
    font-family: 'Playfair Display', serif;
    font-size: 2.2rem;
    font-weight: 700;
    color: var(--espresso);
    line-height: 1;
  }
  .stat-label {
    font-size: 0.75rem;
    letter-spacing: 0.08em;
    color: var(--warm-gray);
    margin-top: 0.25rem;
  }

  .work-section { background: var(--espresso); color: var(--ivory); max-width: none; padding: 7rem 3rem; }
  .work-inner { max-width: 1100px; margin: 0 auto; }
  .work-section .section-label { color: var(--gold); }
  .work-section .section-title { color: var(--ivory); }
  .work-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
    margin-top: 3.5rem;
  }
  .work-card {
    background: rgba(255, 255, 255, 0.04);
    border: 1px solid rgba(201, 169, 110, 0.2);
    padding: 2rem;
    transition: all 0.3s ease;
    cursor: default;
  }
  .work-card:hover {
    background: rgba(201, 169, 110, 0.08);
    border-color: rgba(201, 169, 110, 0.5);
    transform: translateY(-4px);
  }
  .work-card-tag {
    font-size: 0.65rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1rem;
  }
  .work-card-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.25rem;
    font-weight: 500;
    color: var(--ivory);
    line-height: 1.3;
    margin-bottom: 0.75rem;
  }
  .work-card-body {
    font-size: 0.85rem;
    font-weight: 300;
    color: rgba(250, 248, 245, 0.6);
    line-height: 1.7;
  }
  .work-card-metric {
    margin-top: 1.5rem;
    padding-top: 1.5rem;
    border-top: 1px solid rgba(201, 169, 110, 0.15);
    font-size: 0.75rem;
    color: var(--gold);
    letter-spacing: 0.05em;
  }

  .campaign-section { background: var(--cream); max-width: none; padding: 7rem 3rem; }
  .campaign-inner { max-width: 1100px; margin: 0 auto; }
  .campaign-card {
    margin-top: 3.5rem;
    border: 1px solid var(--gold-light);
    overflow: hidden;
  }
  .campaign-header {
    background: var(--blush);
    padding: 3rem;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    gap: 2rem;
  }
  .campaign-brand {
    font-size: 0.7rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--blush-deep);
    margin-bottom: 0.75rem;
  }
  .campaign-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.8rem, 3vw, 2.8rem);
    font-weight: 700;
    color: var(--espresso);
    line-height: 1.1;
  }
  .campaign-title em { font-style: italic; color: var(--blush-deep); }
  .campaign-badge {
    background: var(--espresso);
    color: var(--gold);
    padding: 0.5rem 1.25rem;
    font-size: 0.7rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    white-space: nowrap;
    flex-shrink: 0;
  }
  .campaign-body { padding: 3rem; background: var(--ivory); }
  .campaign-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2rem;
    margin-bottom: 2.5rem;
  }
  .campaign-pillar { }
  .campaign-pillar-num {
    font-family: 'Playfair Display', serif;
    font-size: 2.5rem;
    font-weight: 700;
    color: var(--gold-light);
    line-height: 1;
    margin-bottom: 0.5rem;
  }
  .campaign-pillar-title {
    font-size: 0.8rem;
    font-weight: 500;
    letter-spacing: 0.08em;
    color: var(--espresso);
    text-transform: uppercase;
    margin-bottom: 0.5rem;
  }
  .campaign-pillar-body {
    font-size: 0.85rem;
    font-weight: 300;
    color: var(--warm-gray);
    line-height: 1.65;
  }
  .campaign-tactics {
    background: var(--cream);
    padding: 2rem;
    border-left: 3px solid var(--gold);
  }
  .campaign-tactics-title {
    font-size: 0.7rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1rem;
  }
  .tactics-list {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    list-style: none;
  }
  .tactics-list li {
    background: var(--ivory);
    border: 1px solid var(--gold-light);
    padding: 0.35rem 0.85rem;
    font-size: 0.78rem;
    color: var(--espresso);
    letter-spacing: 0.04em;
  }

  .experience-section { }
  .exp-list { margin-top: 3rem; display: flex; flex-direction: column; gap: 0; }
  .exp-item {
    display: grid;
    grid-template-columns: 200px 1fr;
    gap: 3rem;
    padding: 2.5rem 0;
    border-top: 1px solid var(--cream);
    transition: all 0.2s ease;
  }
  .exp-item:last-child { border-bottom: 1px solid var(--cream); }
  .exp-date {
    font-size: 0.75rem;
    letter-spacing: 0.08em;
    color: var(--warm-gray);
    padding-top: 0.25rem;
  }
  .exp-company {
    font-size: 0.7rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 0.4rem;
  }
  .exp-role {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem;
    font-weight: 500;
    color: var(--espresso);
    margin-bottom: 0.75rem;
  }
  .exp-desc {
    font-size: 0.88rem;
    font-weight: 300;
    color: var(--warm-gray);
    line-height: 1.75;
  }

  .skills-section { background: var(--espresso); max-width: none; padding: 7rem 3rem; }
  .skills-inner { max-width: 1100px; margin: 0 auto; }
  .skills-section .section-label { color: var(--gold); }
  .skills-section .section-title { color: var(--ivory); }
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1px;
    background: rgba(201, 169, 110, 0.15);
    margin-top: 3.5rem;
    border: 1px solid rgba(201, 169, 110, 0.15);
  }
  .skill-block {
    background: var(--espresso);
    padding: 2.5rem;
    transition: background 0.3s;
  }
  .skill-block:hover { background: rgba(201, 169, 110, 0.05); }
  .skill-block-title {
    font-size: 0.7rem;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1rem;
  }
  .skill-tags { display: flex; flex-wrap: wrap; gap: 0.5rem; }
  .skill-tag {
    background: transparent;
    border: 1px solid rgba(201, 169, 110, 0.25);
    color: rgba(250, 248, 245, 0.7);
    padding: 0.3rem 0.8rem;
    font-size: 0.78rem;
    letter-spacing: 0.04em;
    transition: all 0.2s;
  }
  .skill-tag:hover { border-color: var(--gold); color: var(--gold); }

  .contact-section { text-align: center; padding: 8rem 3rem; max-width: none; }
  .contact-inner { max-width: 600px; margin: 0 auto; }
  .contact-section .section-title { font-size: clamp(2.2rem, 5vw, 3.5rem); }
  .contact-links {
    display: flex;
    justify-content: center;
    gap: 2rem;
    margin-top: 3rem;
    flex-wrap: wrap;
  }
  .contact-link {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.9rem 2rem;
    font-size: 0.8rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    text-decoration: none;
    transition: all 0.3s;
  }
  .contact-link.primary {
    background: var(--espresso);
    color: var(--ivory);
    border: 1px solid var(--espresso);
  }
  .contact-link.primary:hover { background: var(--gold); border-color: var(--gold); }
  .contact-link.secondary {
    background: transparent;
    color: var(--espresso);
    border: 1px solid var(--gold);
  }
  .contact-link.secondary:hover { background: var(--gold); }

  footer {
    background: var(--espresso);
    color: rgba(250, 248, 245, 0.4);
    text-align: center;
    padding: 2rem 3rem;
    font-size: 0.75rem;
    letter-spacing: 0.08em;
  }
  footer span { color: var(--gold); }

  .reveal {
    opacity: 0;
    transform: translateY(28px);
    transition: opacity 0.8s ease, transform 0.8s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  @media (max-width: 768px) {
    nav { padding: 1rem 1.5rem; }
    .nav-links { gap: 1rem; }
    section { padding: 5rem 1.5rem; }
    .hero { padding: 0 1.5rem; }
    .about-grid { grid-template-columns: 1fr; gap: 3rem; }
    .work-grid { grid-template-columns: 1fr; }
    .campaign-grid { grid-template-columns: 1fr; }
    .skills-grid { grid-template-columns: 1fr; }
    .exp-item { grid-template-columns: 1fr; gap: 0.5rem; }
    .campaign-header { flex-direction: column; align-items: flex-start; }
    .work-section, .campaign-section, .skills-section, .contact-section { padding: 5rem 1.5rem; }
  }
</style>
</head>
<body>

<nav id="nav">
  <a href="#" class="nav-logo">S. Shatteen</a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#work">Work</a></li>
    <li><a href="#campaign">Campaign</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<div class="hero" id="top">
  <div class="hero-bg-text" aria-hidden="true">Beauty</div>
  <div class="hero-inner">
    <p class="hero-eyebrow">Brand Marketing &nbsp;&middot;&nbsp; Influencer Relations &nbsp;&middot;&nbsp; Creative Strategy</p>
    <h1 class="hero-name">Shaniya<br><em>Shatteen</em></h1>
    <div class="hero-rule"></div>
    <p class="hero-tagline">Beauty-obsessed brand marketer crafting campaigns, building creator partnerships, and telling stories that move people — and product.</p>
    <a href="#work" class="hero-cta">
      View my work
      <svg width="16" height="16" viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="1.5"><line x1="2" y1="8" x2="14" y2="8"/><polyline points="9,3 14,8 9,13"/></svg>
    </a>
  </div>
</div>

<section id="about">
  <div class="reveal">
    <p class="section-label">About me</p>
    <h2 class="section-title">Where strategy meets<br><em>aesthetic</em></h2>
  </div>
  <div class="about-grid">
    <div class="about-portrait reveal">
      <div class="about-portrait-placeholder">
        <div class="portrait-monogram">SS</div>
        <p class="portrait-hint">Add your photo here<br>— replace this placeholder</p>
      </div>
      <div class="about-portrait-label">
        <strong>Shaniya Shatteen</strong>
        <span>Brand Marketer &nbsp;&middot;&nbsp; Atlanta, GA</span>
      </div>
    </div>
    <div class="about-content reveal">
      <p class="section-body">I'm a Howard University alum with 3+ years building brands that people actually talk about. My background spans creator partnerships, social strategy, campaign operations, and visual identity — with a deep love for the beauty industry that goes beyond the job.</p>
      <br>
      <p class="section-body">I keep up with every drop, follow every brand moment, and genuinely obsess over what makes a beauty campaign resonate culturally. That instinct, paired with real executional experience, is what I bring to the table.</p>
      <div class="about-stats">
        <div class="stat-item">
          <div class="stat-number">300+</div>
          <div class="stat-label">Creator partners managed</div>
        </div>
        <div class="stat-item">
          <div class="stat-number">200+</div>
          <div class="stat-label">Brands designed for</div>
        </div>
        <div class="stat-item">
          <div class="stat-number">3+</div>
          <div class="stat-label">Years of experience</div>
        </div>
        <div class="stat-item">
          <div class="stat-number">3.8</div>
          <div class="stat-label">GPA — Howard University</div>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="work-section" id="work">
  <div class="work-inner">
    <div class="reveal">
      <p class="section-label">Selected work</p>
      <h2 class="section-title" style="color:#FAF8F5;">Campaigns, content,<br>and <em>creator strategy</em></h2>
    </div>
    <div class="work-grid">
      <div class="work-card reveal">
        <p class="work-card-tag">Partner Strategy &nbsp;&middot;&nbsp; CJ Affiliate</p>
        <h3 class="work-card-title">300+ Creator Partner Program</h3>
        <p class="work-card-body">Built and managed the full affiliate partner lifecycle for Dick's Sporting Goods, Golf Galaxy, and Public Lands — from recruiting and onboarding to rate negotiation, campaign activation, and relationship management.</p>
        <p class="work-card-metric">$50K+ revenue generated &nbsp;&middot;&nbsp; 3 brand accounts</p>
      </div>
      <div class="work-card reveal">
        <p class="work-card-tag">Content Compliance &nbsp;&middot;&nbsp; Creator Audits</p>
        <h3 class="work-card-title">Brand Compliance & Creator Content Audits</h3>
        <p class="work-card-body">Reviewed and audited YouTube Shopping creator content across high-traffic campaigns, ensuring visual consistency, messaging alignment, and brand standards were upheld on $1M+ revenue days.</p>
        <p class="work-card-metric">$1M+ revenue days &nbsp;&middot;&nbsp; Brand safety maintained</p>
      </div>
      <div class="work-card reveal">
        <p class="work-card-tag">Social Strategy &nbsp;&middot;&nbsp; The Brand Guild</p>
        <h3 class="work-card-title">Luxury Hospitality Social Presence</h3>
        <p class="work-card-body">Created Instagram content and managed community engagement for Marriott, Royal Sonesta, and The Mayflower — maintaining distinct brand voice across each property while nurturing influencer relationships and tracking UGC.</p>
        <p class="work-card-metric">5 platforms &nbsp;&middot;&nbsp; Multiple luxury clients</p>
      </div>
      <div class="work-card reveal">
        <p class="work-card-tag">Visual Identity &nbsp;&middot;&nbsp; Stormy Dashai</p>
        <h3 class="work-card-title">200+ Brand Identity Projects</h3>
        <p class="work-card-body">Designed visual brand identities, campaign assets, and marketing collateral for beauty, lifestyle, and fashion clients — from indie founders to growing product lines. Known for clean, elevated, on-trend aesthetics.</p>
        <p class="work-card-metric">200+ brands &nbsp;&middot;&nbsp; Beauty, lifestyle, fashion</p>
      </div>
      <div class="work-card reveal">
        <p class="work-card-tag">Campaign Operations &nbsp;&middot;&nbsp; Publicis Media</p>
        <h3 class="work-card-title">30+ Go-to-Market Campaign Launches</h3>
        <p class="work-card-body">Managed creative asset delivery, insertion orders, and campaign documentation across Cadillac, Buick, GMC, and Chevrolet — ensuring brand accuracy and on-time launch execution across North American markets.</p>
        <p class="work-card-metric">30+ campaigns &nbsp;&middot;&nbsp; North American markets</p>
      </div>
      <div class="work-card reveal">
        <p class="work-card-tag">Trend Reporting &nbsp;&middot;&nbsp; Precision Strategies</p>
        <h3 class="work-card-title">Digital Trends Intelligence Program</h3>
        <p class="work-card-body">Founded the company's first internal weekly digital trends report, tracking emerging platform trends via Meltwater and surfacing engagement opportunities across 8 client teams — including the Bill & Melinda Gates Foundation.</p>
        <p class="work-card-metric">200K+ audience reach &nbsp;&middot;&nbsp; 8 client teams</p>
      </div>
    </div>
  </div>
</div>

<div class="campaign-section" id="campaign">
  <div class="campaign-inner">
    <div class="reveal">
      <p class="section-label">Campaign concept</p>
      <h2 class="section-title">How I think about<br><em>beauty marketing</em></h2>
      <p class="section-body">Below is an original campaign concept — showing how I approach strategy, storytelling, and creator activation for a beauty brand.</p>
    </div>
    <div class="campaign-card reveal">
      <div class="campaign-header">
        <div>
          <p class="campaign-brand">e.l.f. Cosmetics &nbsp;&middot;&nbsp; Concept Campaign</p>
          <h3 class="campaign-title">"Your skin,<br><em>your rules</em>"</h3>
        </div>
        <div class="campaign-badge">Original Concept</div>
      </div>
      <div class="campaign-body">
        <div class="campaign-grid">
          <div class="campaign-pillar">
            <div class="campaign-pillar-num">01</div>
            <p class="campaign-pillar-title">The insight</p>
            <p class="campaign-pillar-body">Gen Z beauty consumers reject perfection. They want real skin, real routines, and brands that celebrate individuality over the "Instagram face" era. e.l.f.'s price point and inclusive shade range position it perfectly to own this cultural moment.</p>
          </div>
          <div class="campaign-pillar">
            <div class="campaign-pillar-num">02</div>
            <p class="campaign-pillar-title">The strategy</p>
            <p class="campaign-pillar-body">Partner with 25 micro-influencers (50K–200K) across diverse skin types, tones, and routines. No filters, no ring lights — just real people showing their actual morning routines featuring e.l.f. products, anchored by a TikTok-first content strategy.</p>
          </div>
          <div class="campaign-pillar">
            <div class="campaign-pillar-num">03</div>
            <p class="campaign-pillar-title">The activation</p>
            <p class="campaign-pillar-body">Launch a user-generated challenge #MyElfRoutine with a hero asset from a macro creator, seed product to micro-creators for organic content, and amplify with paid whitelisting on TikTok and Instagram. Track UGC volume, save rate, and conversion.</p>
          </div>
        </div>
        <div class="campaign-tactics">
          <p class="campaign-tactics-title">Tactics &amp; channels</p>
          <ul class="tactics-list">
            <li>TikTok-first content</li>
            <li>Instagram Reels</li>
            <li>Micro-influencer seeding</li>
            <li>UGC challenge</li>
            <li>Paid whitelisting</li>
            <li>Creator rate negotiation</li>
            <li>Brand compliance review</li>
            <li>Performance recaps</li>
            <li>Community engagement</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</div>

<section id="experience">
  <div class="reveal">
    <p class="section-label">Experience</p>
    <h2 class="section-title">The journey<br>so <em>far</em></h2>
  </div>
  <div class="exp-list">
    <div class="exp-item reveal">
      <div class="exp-date">Jan 2025 – Present</div>
      <div>
        <p class="exp-company">CJ Affiliate</p>
        <p class="exp-role">Brand Partnerships & Influencer Associate</p>
        <p class="exp-desc">Managed end-to-end creator and affiliate partner lifecycle for Dick's Sporting Goods, Golf Galaxy, and Public Lands. Developed creative assets, campaign briefs, and partner newsletters. Led weekly performance recaps translating data into narrative insights.</p>
      </div>
    </div>
    <div class="exp-item reveal">
      <div class="exp-date">Jun – Dec 2024</div>
      <div>
        <p class="exp-company">Publicis Media Group</p>
        <p class="exp-role">Associate Campaign Manager</p>
        <p class="exp-desc">Oversaw creative delivery across 30+ campaign launches for Cadillac, Buick, GMC, and Chevrolet. Designed and led the Intern Professional Development Program. Served as Inaugural Operations Manager for the Culture Crew.</p>
      </div>
    </div>
    <div class="exp-item reveal">
      <div class="exp-date">Jan – May 2024</div>
      <div>
        <p class="exp-company">The Brand Guild</p>
        <p class="exp-role">Social Media & Brand Intern</p>
        <p class="exp-desc">Created content and managed community engagement for luxury hospitality clients including Marriott, Royal Sonesta, and The Mayflower across five social platforms. Delivered bi-weekly trend reports shaping client strategy.</p>
      </div>
    </div>
    <div class="exp-item reveal">
      <div class="exp-date">Jun 2020 – Jan 2025</div>
      <div>
        <p class="exp-company">Stormy Dashai Graphics</p>
        <p class="exp-role">Freelance Brand Designer & Social Media Strategist</p>
        <p class="exp-desc">Designed visual brand identities and campaign assets for 200+ brands across beauty, lifestyle, and fashion. Developed paid and organic social strategies for clients building brand awareness and loyal communities.</p>
      </div>
    </div>
    <div class="exp-item reveal">
      <div class="exp-date">Jan – Aug 2023</div>
      <div>
        <p class="exp-company">Precision Strategies</p>
        <p class="exp-role">Digital Strategy Intern</p>
        <p class="exp-desc">Produced organic content reaching 200K+ across 8 client teams. Founded the company's first internal digital trends report tracking emerging platform trends via Meltwater. Contributed to paid media campaigns with $2M+ budgets.</p>
      </div>
    </div>
  </div>
</section>

<div class="skills-section">
  <div class="skills-inner">
    <div class="reveal">
      <p class="section-label">Skills & tools</p>
      <h2 class="section-title" style="color:#FAF8F5;">What I bring<br>to the <em>table</em></h2>
    </div>
    <div class="skills-grid">
      <div class="skill-block reveal">
        <p class="skill-block-title">Beauty & Brand</p>
        <div class="skill-tags">
          <span class="skill-tag">Brand storytelling</span>
          <span class="skill-tag">Campaign development</span>
          <span class="skill-tag">Trend forecasting</span>
          <span class="skill-tag">Creative asset production</span>
          <span class="skill-tag">Visual identity</span>
          <span class="skill-tag">Copywriting</span>
        </div>
      </div>
      <div class="skill-block reveal">
        <p class="skill-block-title">Influencer & Partnerships</p>
        <div class="skill-tags">
          <span class="skill-tag">Creator lifecycle management</span>
          <span class="skill-tag">Influencer relations</span>
          <span class="skill-tag">UGC strategy</span>
          <span class="skill-tag">Rate negotiation</span>
          <span class="skill-tag">Affiliate marketing</span>
          <span class="skill-tag">Partner onboarding</span>
        </div>
      </div>
      <div class="skill-block reveal">
        <p class="skill-block-title">Content & Social</p>
        <div class="skill-tags">
          <span class="skill-tag">TikTok</span>
          <span class="skill-tag">Instagram</span>
          <span class="skill-tag">Pinterest</span>
          <span class="skill-tag">LinkedIn</span>
          <span class="skill-tag">Content calendars</span>
          <span class="skill-tag">Sprout Social</span>
          <span class="skill-tag">Meltwater</span>
          <span class="skill-tag">Community engagement</span>
        </div>
      </div>
      <div class="skill-block reveal">
        <p class="skill-block-title">Campaign & Events</p>
        <div class="skill-tags">
          <span class="skill-tag">Go-to-market planning</span>
          <span class="skill-tag">Event coordination</span>
          <span class="skill-tag">Launch management</span>
          <span class="skill-tag">Creative briefing</span>
          <span class="skill-tag">Adobe Creative Suite</span>
          <span class="skill-tag">Jira</span>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="contact-section" id="contact">
  <div class="contact-inner reveal">
    <p class="section-label" style="text-align:center;">Get in touch</p>
    <h2 class="section-title">Let's build something<br><em>beautiful</em> together</h2>
    <p class="section-body" style="margin: 1.5rem auto 0; text-align:center;">Open to brand marketing, influencer partnerships, and creative strategy roles — especially in beauty, lifestyle, and culture-forward brands.</p>
    <div class="contact-links">
      <a href="mailto:shaniyashatteen@gmail.com" class="contact-link primary">
        <svg width="14" height="14" viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="1" y="3" width="12" height="8" rx="1"/><polyline points="1,3 7,8 13,3"/></svg>
        Send an email
      </a>
      <a href="https://linkedin.com/in/shaniya-shatteen" target="_blank" rel="noopener" class="contact-link secondary">
        <svg width="14" height="14" viewBox="0 0 14 14" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="1" y="1" width="12" height="12" rx="2"/><line x1="4.5" y1="6" x2="4.5" y2="10"/><line x1="4.5" y1="4" x2="4.5" y2="4.5"/><path d="M7 10V7.5C7 6.7 7.7 6 8.5 6S10 6.7 10 7.5V10"/></svg>
        LinkedIn
      </a>
    </div>
  </div>
</div>

<footer>
  <p>Shaniya Shatteen &nbsp;&middot;&nbsp; Brand Marketing Portfolio &nbsp;&middot;&nbsp; <span>&copy; 2026</span></p>
</footer>

<script>
  const nav = document.getElementById('nav');
  window.addEventListener('scroll', () => {
    if (window.scrollY > 80) nav.classList.add('visible');
    else nav.classList.remove('visible');
  });

  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('visible'), 80);
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1 });
  reveals.forEach(el => observer.observe(el));
</script>
</body>
</html>
