<script lang="ts">
  import StarCanvas from '$lib/components/StarCanvas.svelte';
  import Nav        from '$lib/components/Nav.svelte';
  import GameCard   from '$lib/components/GameCard.svelte';
  import Footer     from '$lib/components/Footer.svelte';

  const navLinks = [
    { label: 'Library',          href: '#library'          },
    { label: 'Studio',           href: '#about'            },
    { label: 'Foreign Protocol', href: '/foreign-protocol' },
  ];
</script>

<svelte:head>
  <title>MGL — MidMan Game Library</title>
  <meta name="description" content="MidMan Game Library — independent games built to push back." />
</svelte:head>

<StarCanvas count={160} />
<Nav links={navLinks} />

<!-- ── HERO ── -->
<section class="hero">
  <div class="hero-eyebrow">
    <span class="eyebrow-pulse" aria-hidden="true"></span>
    Transmission Active
  </div>

  <h1 class="hero-title">
    MIDMAN
    <span class="hero-title-accent">GAME LIBRARY</span>
  </h1>

  <p class="hero-sub">An Independent Game Library by MidMan Studio</p>

  <p class="hero-desc">
    Independent games forged in the dark. Raw mechanics, unapologetic challenge,
    and worlds that don't let go. Download. Play. Survive.
  </p>

  <a href="#library" class="hero-cta">
    Enter the Library
    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor"
         stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
      <line x1="5" y1="12" x2="19" y2="12"/>
      <polyline points="12 5 19 12 12 19"/>
    </svg>
  </a>
</section>

<!-- ── LIBRARY ── -->
<section class="library" id="library">
  <div class="section-eyebrow">// game_library.exe</div>
  <h2 class="section-title">AVAILABLE TITLES</h2>

  <div class="games-grid">
    <GameCard
      href="/foreign-protocol"
      title="FOREIGN PROTOCOL"
      genre="Arcade Shooter · Infinite Run"
      desc="The last pilot standing between an alien armada and total galactic silence. Survive. Score. Find the boss no one has ever beaten."
      platforms={['Android', 'iOS', 'Windows', 'macOS']}
      tag="LIVE"
      gif={null}
    >
      <svelte:fragment slot="visual">
        <div class="card-stars"></div>
        <div class="card-planet"></div>
        <div class="card-enemies">
          {#each [0,1,2] as _}
            <svg width="20" height="20" viewBox="0 0 10 10" fill="none"
                 style="filter:drop-shadow(0 0 4px #dc143c)" aria-hidden="true">
              <rect x="1" y="0" width="8" height="2" fill="#dc143c"/>
              <rect x="0" y="2" width="10" height="4" fill="#dc143c"/>
              <rect x="2" y="3" width="2" height="2" fill="#040812"/>
              <rect x="6" y="3" width="2" height="2" fill="#040812"/>
              <rect x="0" y="6" width="2" height="2" fill="#dc143c"/>
              <rect x="8" y="6" width="2" height="2" fill="#dc143c"/>
              <rect x="3" y="8" width="1" height="2" fill="#dc143c"/>
              <rect x="6" y="8" width="1" height="2" fill="#dc143c"/>
            </svg>
          {/each}
        </div>
        <svg class="card-ship" width="40" height="40" viewBox="0 0 24 24" fill="none" aria-hidden="true">
          <polygon points="12,2 18,18 12,15 6,18" fill="#4169e1" stroke="#6a8fff" stroke-width="0.4"/>
          <polygon points="12,6 16,17 12,14.5 8,17" fill="#0047ab"/>
          <circle cx="12" cy="10" r="2" fill="#6a8fff" opacity="0.85"/>
          <polygon points="6,18 4,22 12,19" fill="rgba(65,105,225,0.35)"/>
          <polygon points="18,18 20,22 12,19" fill="rgba(65,105,225,0.35)"/>
        </svg>
        <div class="card-bullet b1"></div>
        <div class="card-bullet b2"></div>
        <div class="card-bullet b3"></div>
      </svelte:fragment>
    </GameCard>

    <GameCard title="Title Redacted" />
  </div>
</section>

<div class="section-divider" role="separator"></div>

<!-- ── ABOUT ── -->
<section class="about-strip" id="about">
  <p>
    <strong>MidMan Studio</strong> is an independent developer building
    experiences that push back. No hand-holding. No easy clears.
    Just <em>pure gameplay</em>, relentless challenge, and the satisfaction
    of earning every inch — <strong>pixel by pixel, pattern by pattern</strong>.
  </p>
</section>

<Footer />

<style>
  /* ── Hero ── */
  .hero {
    position: relative; z-index: 1;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 130px 24px 80px;
  }

  .hero-eyebrow {
    display: flex;
    align-items: center;
    gap: 10px;
    font-family: var(--font-mono);
    font-size: 10px;
    color: var(--dim);
    letter-spacing: 4px;
    text-transform: uppercase;
    margin-bottom: 28px;
  }

  .eyebrow-pulse {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--crimson);
    box-shadow: var(--glow-crimson);
    animation: blink 1.8s ease-in-out infinite;
  }

  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.25} }

  .hero-title {
    font-family: var(--font-head);
    font-size: clamp(32px, 7vw, 76px);
    font-weight: 900;
    line-height: 1.05;
    letter-spacing: -0.02em;
    margin-bottom: 8px;
    color: var(--text);
  }

  .hero-title-accent {
    display: block;
    background: linear-gradient(90deg, var(--cobalt-light), #6a8fff);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-sub {
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--dim);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 32px;
  }

  .hero-desc {
    max-width: 520px;
    font-size: 16px;
    line-height: 1.85;
    color: var(--text-2);
    margin-bottom: 48px;
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
    padding: 16px 40px;
    background: linear-gradient(135deg, var(--cobalt), var(--cobalt-light));
    color: #fff;
    box-shadow: var(--glow-cobalt);
    clip-path: polygon(10px 0%, 100% 0%, calc(100% - 10px) 100%, 0% 100%);
    transition: all 0.25s var(--ease);
  }

  .hero-cta:hover {
    background: linear-gradient(135deg, var(--cobalt-light), #6a8fff);
    transform: translateY(-2px);
    box-shadow: var(--glow-cobalt), 0 8px 32px rgba(65,105,225,0.3);
  }

  .hero-cta svg { transition: transform 0.2s; }
  .hero-cta:hover svg { transform: translateX(4px); }

  /* ── Library ── */
  .library {
    position: relative; z-index: 1;
    padding: 80px 48px;
    max-width: 1200px;
    margin: 0 auto;
  }

  .section-eyebrow {
    font-family: var(--font-mono);
    font-size: 10px;
    color: var(--cobalt-light);
    letter-spacing: 4px;
    text-transform: uppercase;
    margin-bottom: 8px;
  }

  .section-title {
    font-family: var(--font-head);
    font-size: clamp(20px, 3vw, 30px);
    font-weight: 700;
    color: var(--text);
    margin-bottom: 48px;
    line-height: 1.3;
  }

  .games-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
    gap: 24px;
  }

  /* Card slot visuals */
  :global(.card-stars) {
    position: absolute; inset: 0;
    background-image:
      radial-gradient(1px 1px at 12% 20%, rgba(255,255,255,0.7) 0%, transparent 100%),
      radial-gradient(1px 1px at 28% 65%, rgba(180,200,255,0.5) 0%, transparent 100%),
      radial-gradient(1px 1px at 48% 15%, rgba(255,255,255,0.6) 0%, transparent 100%),
      radial-gradient(1px 1px at 65% 75%, rgba(180,200,255,0.4) 0%, transparent 100%),
      radial-gradient(1px 1px at 78% 30%, rgba(255,255,255,0.7) 0%, transparent 100%),
      radial-gradient(1.5px 1.5px at 20% 85%, rgba(65,105,225,0.5) 0%, transparent 100%);
  }

  :global(.card-planet) {
    position: absolute;
    bottom: -30px; right: -20px;
    width: 130px; height: 130px;
    border-radius: 50%;
    background: radial-gradient(circle at 30% 30%, #0f2a4a, #020810);
    box-shadow: inset -12px -12px 28px rgba(0,0,0,0.7), 0 0 30px rgba(65,105,225,0.15);
    opacity: 0.5;
  }

  :global(.card-enemies) {
    position: absolute; top: 20px; left: 20px;
    display: flex; gap: 12px; z-index: 2;
    animation: march 2.5s ease-in-out infinite alternate;
  }

  @keyframes march { from{transform:translateX(0)} to{transform:translateX(20px)} }

  :global(.card-ship) {
    position: relative; z-index: 2;
    animation: shipfloat 3s ease-in-out infinite;
    filter: drop-shadow(0 0 8px rgba(65,105,225,0.8));
  }

  @keyframes shipfloat { 0%,100%{transform:translateY(0) rotate(-4deg)} 50%{transform:translateY(-10px) rotate(4deg)} }

  :global(.card-bullet) {
    position: absolute;
    width: 2px; height: 14px;
    background: linear-gradient(180deg, #6a8fff, rgba(65,105,225,0));
    border-radius: 1px;
    animation: bulletup 0.9s linear infinite;
    z-index: 2;
  }

  :global(.card-bullet.b1) { left: 48%; top: 120px; animation-delay: 0s; }
  :global(.card-bullet.b2) { left: 38%; top: 100px; animation-delay: 0.35s; }
  :global(.card-bullet.b3) { left: 58%; top: 110px; animation-delay: 0.65s; }

  @keyframes bulletup { from{transform:translateY(0);opacity:1} to{transform:translateY(-160px);opacity:0} }

  /* ── Divider ── */
  .section-divider {
    position: relative; z-index: 1;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--cobalt-light), transparent);
    opacity: 0.2;
    margin: 0 48px;
  }

  /* ── About ── */
  .about-strip {
    position: relative; z-index: 1;
    background: linear-gradient(135deg, rgba(7,15,31,0.9), rgba(4,8,18,0.9));
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
    padding: 64px 48px;
    text-align: center;
  }

  .about-strip p {
    max-width: 600px;
    margin: 0 auto;
    font-size: 15px;
    line-height: 2;
    color: var(--text-2);
  }

  .about-strip :global(strong) { color: var(--cobalt-light); font-weight: 600; }
  .about-strip :global(em)     { font-style: normal; color: var(--text); }

  /* ── Responsive ── */
  @media (max-width: 768px) {
    .library        { padding: 60px 24px; }
    .about-strip    { padding: 48px 24px; }
    .section-divider { margin: 0 24px; }
    .games-grid     { grid-template-columns: 1fr; }
    .hero-desc      { font-size: 14px; }
  }

  @media (max-width: 480px) {
    .hero           { padding: 110px 20px 60px; }
    .library        { padding: 48px 16px; }
    .about-strip    { padding: 40px 16px; }
    .section-divider { margin: 0 16px; }
    .hero-sub       { font-size: 9px; letter-spacing: 2px; }
    .hero-cta       { padding: 14px 28px; font-size: 10px; }
  }
</style>
