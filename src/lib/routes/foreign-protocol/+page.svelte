<script lang="ts">
  import StarCanvas    from '$lib/components/StarCanvas.svelte';
  import Nav           from '$lib/components/Nav.svelte';
  import DownloadCard  from '$lib/components/DownloadCard.svelte';
  import SectionHeader from '$lib/components/SectionHeader.svelte';
  import Footer        from '$lib/components/Footer.svelte';

  const features = [
    {
      icon: 'M10 14h4M12 12v4 M6 9H4.5a2.5 2.5 0 0 0 0 5H6 M18 9h1.5a2.5 2.5 0 0 1 0 5H18',
      name: 'RETRO SOUL',
      desc: 'Crisp pixel art aesthetics paired with modern, fluid movement. The golden age of arcade shooters — reborn.',
    },
    {
      icon: 'M12 12c-2-2.5-4-4-6-4a4 4 0 0 0 0 8c2 0 4-1.5 6-4z M12 12c2 2.5 4 4 6 4a4 4 0 0 0 0-8c-2 0-4 1.5-6 4z',
      name: 'INFINITE SCALING',
      desc: 'The further you go, the faster they come. There is no end — only the glory of a higher score.',
    },
    {
      icon: 'M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z',
      name: "THREE LIVES. THAT'S IT.",
      desc: 'You start with three hearts. Every hit counts. Every dodge is a victory. Die once and feel it.',
      red: true,
    },
    {
      icon: 'M6 9H4.5a2.5 2.5 0 0 0 0 5H6 M18 9h1.5a2.5 2.5 0 0 1 0 5H18 M4 22h16M9 22v-3M15 22v-3M12 19v-7M6 3h12v6a6 6 0 0 1-12 0V3z',
      name: 'CLASSIC ARCADE SCORING',
      desc: "Track your Best and Current scores to prove your dominance. Chase the number. That's all there is.",
    },
    {
      icon: 'M12 2a9 9 0 0 1 9 9 8.9 8.9 0 0 1-3 6.6V20a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1v-2.4A8.9 8.9 0 0 1 3 11a9 9 0 0 1 9-9z M9 15 L9 21 M12 15 L12 21 M15 15 L15 21',
      name: 'INSANE DIFFICULTY',
      desc: 'For players who find normal shooters too easy. A level of difficulty that borders on the impossible.',
      red: true,
    },
    {
      icon: 'M13 2 3 14 12 14 11 22 21 10 12 10 13 2',
      name: 'POWER & PRECISION',
      desc: 'Collect energy fragments to keep your offensive protocol online. Run dry and the tide turns fast.',
    },
    {
      icon: 'M12 2a9 9 0 1 0 0 18 9 9 0 0 0 0-18z M3.6 9h16.8 M3.6 15h16.8 M11.5 2a17 17 0 0 0 0 20 M12.5 2a17 17 0 0 1 0 20',
      name: 'DYNAMIC ENVIRONMENTS',
      desc: 'Fight across infinite void with shifting backdrops, parallax starfields, and escalating visual intensity.',
    },
    {
      icon: 'M12 2a10 10 0 1 0 0 20 10 10 0 0 0 0-20z M12 8 L12 12 M12 16 L12 16',
      name: 'BULLET-HELL PATTERNS',
      desc: 'Weave through neon nebulae and dodge escalating patterns that demand full focus every single second.',
    },
  ];

  // Set available: true for each platform once the download file is in place
  const downloads = [
    {
      cls:       'android' as const,
      platform:  'ANDROID',
      format:    'APK File',
      href:      '/games/android/ForeignProtocol.apk',
      label:     'Download APK',
      available: false,
    },
    {
      cls:       'ios' as const,
      platform:  'iOS',
      format:    'IPA File',
      href:      '/games/ios/ForeignProtocol.ipa',
      label:     'Download IPA',
      available: false,
    },
    {
      cls:       'windows' as const,
      platform:  'WINDOWS',
      format:    'EXE Installer',
      href:      '/games/windows/ForeignProtocol_Setup.exe',
      label:     'Download .EXE',
      available: false,
    },
    {
      cls:       'mac' as const,
      platform:  'macOS',
      format:    'DMG File',
      href:      '/games/mac/ForeignProtocol.dmg',
      label:     'Download .DMG',
      available: false,
    },
  ];
</script>

<svelte:head>
  <title>Foreign Protocol — MGL</title>
  <meta name="description" content="Foreign Protocol — infinite arcade shooter. Download for Android, iOS, Windows, macOS." />
</svelte:head>

<StarCanvas count={120} />
<Nav backHref="/" backLabel="MGL" breadcrumb="Foreign Protocol" />

<!-- ── HERO ── -->
<section class="hero">
  <div class="hero-inner">
    <div class="live-badge">
      <span class="live-dot" aria-hidden="true"></span>
      Now Available
    </div>

    <h1 class="hero-title">FOREIGN<br/>PROTOCOL</h1>
    <p class="hero-subtitle">// The Stars Are No Longer Silent //</p>

    <p class="hero-quote">
      You are the <em>last pilot standing</em> between a relentless alien armada
      and total galactic silence. This isn't just a flight —
      it's a <em>suicide mission into the infinite</em>.
    </p>

    <div class="stats-row">
      <div class="stat">
        <span class="stat-val">3</span>
        <span class="stat-label">Lives</span>
      </div>
      <div class="stat">
        <span class="stat-val">&infin;</span>
        <span class="stat-label">Waves</span>
      </div>
      <div class="stat">
        <span class="stat-val red">0</span>
        <span class="stat-label">Boss Clears</span>
      </div>
    </div>

    <a href="#downloads" class="hero-cta">
      Download Now
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor"
           stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
        <line x1="12" y1="5" x2="12" y2="19"/>
        <polyline points="5 12 12 19 19 12"/>
      </svg>
    </a>
  </div>
</section>

<!-- ── BOSS STRIP ── -->
<div class="boss-strip">
  <div class="boss-inner">
    <div class="boss-skull" aria-hidden="true">
      <svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="#dc143c"
           stroke-width="1.2" stroke-linecap="round" stroke-linejoin="round">
        <path d="M12 2a9 9 0 0 1 9 9 8.9 8.9 0 0 1-3 6.6V20a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1v-2.4A8.9 8.9 0 0 1 3 11a9 9 0 0 1 9-9z"
              fill="rgba(220,20,60,0.08)"/>
        <line x1="9"  y1="15" x2="9"  y2="21"/>
        <line x1="12" y1="15" x2="12" y2="21"/>
        <line x1="15" y1="15" x2="15" y2="21"/>
        <circle cx="9"  cy="10" r="2" fill="rgba(220,20,60,0.3)"/>
        <circle cx="15" cy="10" r="2" fill="rgba(220,20,60,0.3)"/>
      </svg>
    </div>

    <div class="boss-content">
      <div class="boss-label">
        <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor"
             stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
          <path d="M10.29 3.86L1.82 18a2 2 0 0 0 1.71 3h16.94a2 2 0 0 0 1.71-3L13.71 3.86a2 2 0 0 0-3.42 0z"/>
          <line x1="12" y1="9" x2="12" y2="13"/>
          <line x1="12" y1="17" x2="12.01" y2="17"/>
        </svg>
        Threat Level: Unclassified
      </div>
      <h2 class="boss-title">THE DOOM SPHERE</h2>
      <blockquote class="boss-quote">
        "I built this game, I programmed the patterns, and I've played it hundreds of times...
        and I still haven't beaten this boss on Insane difficulty.
        It is quite literally the ultimate wall."
        <cite>— Developer, MidMan Studio</cite>
      </blockquote>
    </div>
  </div>
</div>

<!-- ── DOWNLOADS ── -->
<section class="downloads" id="downloads">
  <div class="downloads-inner">
    <SectionHeader
      eyebrow="download_protocol.init"
      title="CHOOSE YOUR PLATFORM"
      subtitle="v1.0.0 — Initial Release"
    />

    <div class="dl-grid">
      {#each downloads as dl}
        <DownloadCard
          cls={dl.cls}
          platform={dl.platform}
          format={dl.format}
          href={dl.href}
          label={dl.label}
          available={dl.available}
        />
      {/each}
    </div>
  </div>
</section>

<!-- ── FEATURES ── -->
<section class="features">
  <div class="features-inner">
    <SectionHeader
      eyebrow="key_features.log"
      title="WHAT YOU'RE GETTING INTO"
    />

    <div class="features-grid">
      {#each features as f}
        <div class="feature-item">
          <svg class="feature-icon" class:red={f.red} viewBox="0 0 24 24" fill="none"
               stroke="currentColor" stroke-width="1.6"
               stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
            <path d={f.icon}/>
          </svg>
          <div class="feature-name">{f.name}</div>
          <p class="feature-desc">{f.desc}</p>
        </div>
      {/each}
    </div>
  </div>
</section>

<Footer backHref="/" backLabel="Back to MGL Library" />

<style>
  /* ── Hero ── */
  .hero {
    position: relative; z-index: 1;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 140px 24px 80px;
  }

  .hero-inner {
    max-width: 680px;
    width: 100%;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .live-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-family: var(--font-mono);
    font-size: 9px;
    color: var(--green);
    letter-spacing: 3px;
    text-transform: uppercase;
    padding: 5px 12px;
    border: 1px solid rgba(57, 255, 20, 0.4);
    background: rgba(57, 255, 20, 0.06);
    margin-bottom: 24px;
    text-shadow: var(--glow-green);
  }

  .live-dot {
    width: 5px; height: 5px;
    border-radius: 50%;
    background: var(--green);
    box-shadow: var(--glow-green);
    animation: blink 1.6s ease-in-out infinite;
  }

  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.2} }

  .hero-title {
    font-family: var(--font-head);
    font-size: clamp(36px, 8vw, 72px);
    font-weight: 900;
    line-height: 1.05;
    color: var(--text);
    margin-bottom: 12px;
    letter-spacing: -0.02em;
  }

  .hero-subtitle {
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--cobalt-light);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 32px;
  }

  .hero-quote {
    font-size: 15px;
    line-height: 2;
    color: var(--text-2);
    border-left: 2px solid var(--cobalt-light);
    padding-left: 20px;
    margin-bottom: 40px;
    text-align: left;
    max-width: 540px;
  }

  .hero-quote em { font-style: normal; color: var(--text); }

  .stats-row {
    display: flex;
    gap: 48px;
    margin-bottom: 44px;
    justify-content: center;
    flex-wrap: wrap;
  }

  .stat { display: flex; flex-direction: column; align-items: center; gap: 4px; }

  .stat-val {
    font-family: var(--font-head);
    font-size: 28px;
    font-weight: 900;
    color: var(--cobalt-light);
    text-shadow: 0 0 20px rgba(65,105,225,0.5);
  }
  .stat-val.red { color: var(--crimson); text-shadow: 0 0 20px rgba(220,20,60,0.4); }

  .stat-label {
    font-family: var(--font-mono);
    font-size: 9px;
    color: var(--dim);
    letter-spacing: 2px;
    text-transform: uppercase;
  }

  .hero-cta {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    font-family: var(--font-head);
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 3px;
    text-transform: uppercase;
    padding: 16px 44px;
    background: linear-gradient(135deg, var(--cobalt), var(--cobalt-light));
    color: #fff;
    box-shadow: var(--glow-cobalt);
    clip-path: polygon(10px 0%, 100% 0%, calc(100% - 10px) 100%, 0% 100%);
    transition: all 0.25s var(--ease);
  }
  .hero-cta:hover {
    background: linear-gradient(135deg, var(--cobalt-light), #6a8fff);
    transform: translateY(-2px);
  }
  .hero-cta svg { transition: transform 0.2s; }
  .hero-cta:hover svg { transform: translateY(3px); }

  /* ── Boss strip ── */
  .boss-strip {
    position: relative; z-index: 1;
    background: linear-gradient(135deg, rgba(20,0,5,0.95), rgba(10,0,8,0.9));
    border-top: 1px solid rgba(220,20,60,0.3);
    border-bottom: 1px solid rgba(220,20,60,0.3);
    padding: 60px 48px;
  }

  .boss-inner {
    max-width: 900px;
    margin: 0 auto;
    display: flex;
    gap: 48px;
    align-items: center;
  }

  .boss-skull {
    width: 80px; height: 80px;
    display: flex;
    align-items: center;
    justify-content: center;
    border: 1px solid rgba(220,20,60,0.3);
    animation: rot 6s linear infinite;
    flex-shrink: 0;
    filter: drop-shadow(0 0 12px rgba(220,20,60,0.5));
  }
  @keyframes rot { from{transform:rotate(0deg)} to{transform:rotate(360deg)} }

  .boss-label {
    display: flex;
    align-items: center;
    gap: 8px;
    font-family: var(--font-mono);
    font-size: 10px;
    color: var(--crimson);
    letter-spacing: 4px;
    text-transform: uppercase;
    margin-bottom: 12px;
    animation: blink 1.6s ease-in-out infinite;
  }

  .boss-title {
    font-family: var(--font-head);
    font-size: clamp(20px, 3vw, 34px);
    font-weight: 900;
    color: var(--text);
    margin-bottom: 16px;
    line-height: 1.2;
  }

  .boss-quote {
    font-size: 13px;
    color: rgba(180, 100, 110, 0.9);
    line-height: 2;
    border-left: 2px solid var(--crimson);
    padding-left: 20px;
    font-style: italic;
  }
  .boss-quote cite {
    display: block;
    font-style: normal;
    font-size: 11px;
    color: var(--dim);
    margin-top: 12px;
  }

  /* ── Downloads ── */
  .downloads {
    position: relative; z-index: 1;
    background: linear-gradient(180deg, var(--bg), rgba(6,12,26,0.98));
    border-top: 1px solid var(--border);
    padding: 100px 48px;
  }

  .downloads-inner {
    max-width: 1200px;
    margin: 0 auto;
  }

  .dl-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 20px;
  }

  /* ── Features ── */
  .features {
    position: relative; z-index: 1;
    padding: 100px 48px;
  }

  .features-inner {
    max-width: 1200px;
    margin: 0 auto;
  }

  .features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 20px;
  }

  .feature-item {
    background: rgba(7,15,31,0.9);
    border: 1px solid var(--border);
    padding: 28px;
    transition: border-color 0.3s;
  }
  .feature-item:hover { border-color: rgba(65,105,225,0.35); }

  .feature-icon {
    width: 36px; height: 36px;
    color: var(--cobalt-light);
    margin-bottom: 16px;
    display: block;
  }
  .feature-icon.red { color: var(--crimson); }

  .feature-name {
    font-family: var(--font-head);
    font-size: 10px;
    font-weight: 700;
    color: var(--cobalt-light);
    margin-bottom: 12px;
    line-height: 1.5;
    letter-spacing: 1px;
  }

  .feature-desc {
    font-size: 13px;
    color: var(--text-2);
    line-height: 1.9;
  }

  /* ── Responsive ── */
  @media (max-width: 768px) {
    .hero           { padding: 120px 24px 60px; min-height: auto; }
    .hero-quote     { font-size: 14px; }
    .boss-strip     { padding: 40px 24px; }
    .boss-inner     { flex-direction: column; text-align: center; }
    .boss-skull     { margin: 0 auto; }
    .boss-quote     { text-align: left; }
    .downloads      { padding: 60px 24px; }
    .features       { padding: 60px 24px; }
    .dl-grid        { grid-template-columns: 1fr; }
    .features-grid  { grid-template-columns: 1fr; }
    .stats-row      { gap: 32px; }
  }

  @media (max-width: 480px) {
    .hero           { padding: 110px 16px 48px; }
    .hero-title     { font-size: clamp(32px, 10vw, 52px); }
    .hero-quote     { padding-left: 14px; font-size: 13px; }
    .boss-strip     { padding: 32px 16px; }
    .downloads      { padding: 48px 16px; }
    .features       { padding: 48px 16px; }
    .hero-cta       { padding: 14px 28px; font-size: 10px; }
    .stats-row      { gap: 24px; }
    .stat-val       { font-size: 22px; }
  }
</style>
