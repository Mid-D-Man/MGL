<script lang="ts">
  import StarCanvas from '$lib/components/StarCanvas.svelte';
  import Nav        from '$lib/components/Nav.svelte';

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
      desc: 'Track your Best and Current scores to prove your dominance. Chase the number. That\'s all there is.',
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
      desc: 'Fight against massive pixelated planets and shimmering starfields across the infinite void.',
    },
    {
      icon: 'M12 2a10 10 0 1 0 0 20 10 10 0 0 0 0-20z M12 8 L12 12 M12 16 L12 16',
      name: 'BULLET-HELL PATTERNS',
      desc: 'Weave through neon nebulae and dodge escalating patterns that demand full focus every single second.',
    },
  ];

  const downloads = [
    { cls: 'android', platform: 'ANDROID', format: 'APK File', href: 'android/ForeignProtocol.apk', label: 'Download APK' },
    { cls: 'ios',     platform: 'iOS',     format: 'IPA File', href: 'ios/ForeignProtocol.ipa',     label: 'Download IPA' },
    { cls: 'windows', platform: 'WINDOWS', format: 'EXE Installer', href: 'windows/ForeignProtocol_Setup.exe', label: 'Download .EXE' },
    { cls: 'mac',     platform: 'macOS',   format: 'DMG File', href: 'mac/ForeignProtocol.dmg',     label: 'Download .DMG' },
  ];
</script>

<svelte:head>
  <title>Foreign Protocol — MGL</title>
  <meta name="description" content="Foreign Protocol — infinite arcade shooter. Download for Android, iOS, Windows, macOS." />
</svelte:head>

<StarCanvas count={120} />
<Nav backHref="/" backLabel="MGL" breadcrumb="Foreign Protocol" />

<!-- ── HERO ── -->
<div class="hero">
  <div class="hero-left">
    <div class="live-badge">
      <span class="live-dot"></span>
      Now Available
    </div>

    <h1 class="hero-title">FOREIGN<br/>PROTOCOL</h1>
    <p class="hero-subtitle">// The Stars Are No Longer Silent //</p>

    <p class="hero-quote">
      You are the <em>last pilot standing</em> between a relentless alien armada
      and total galactic silence. This isn't just a flight —<br/>
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
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
        <line x1="12" y1="5" x2="12" y2="19"/>
        <polyline points="5 12 12 19 19 12"/>
      </svg>
    </a>
  </div>

  <!-- Mini game screen preview -->
  <div class="game-screen-wrap">
    <div class="game-screen">
      <div class="gs-stars"></div>
      <div class="gs-planet"></div>

      <!-- HUD -->
      <div class="gs-hud">
        <div class="hud-item">
          <span class="hud-label">Score</span>
          <span class="hud-val">004280</span>
        </div>
        <div class="hud-item">
          <span class="hud-label">Best</span>
          <span class="hud-val white">012450</span>
        </div>
        <div class="hud-item">
          <span class="hud-label">Lives</span>
          <span class="hud-lives">
            <!-- 2 filled hearts -->
            {#each [0,1] as _}
              <svg width="10" height="10" viewBox="0 0 24 24" fill="#dc143c" stroke="#dc143c" stroke-width="1" style="display:inline">
                <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/>
              </svg>
            {/each}
            <!-- 1 empty heart -->
            <svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="#dc143c" stroke-width="1.5" style="display:inline">
              <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/>
            </svg>
          </span>
        </div>
      </div>

      <!-- Enemy rows -->
      <div class="gs-enemies row1">
        {#each [0,1,2] as _}
          <svg width="18" height="18" viewBox="0 0 10 10" fill="none" style="filter:drop-shadow(0 0 3px #dc143c)">
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

      <div class="gs-enemies row2">
        {#each [0,1,2] as _}
          <svg width="18" height="12" viewBox="0 0 14 8" fill="none" style="filter:drop-shadow(0 0 3px #dc143c)">
            <ellipse cx="7" cy="6" rx="7" ry="2" fill="#dc143c"/>
            <ellipse cx="7" cy="4" rx="4" ry="2" fill="#8b0a1e"/>
            <circle cx="4" cy="6" r="1" fill="#ff4060"/>
            <circle cx="7" cy="6" r="1" fill="#ff4060"/>
            <circle cx="10" cy="6" r="1" fill="#ff4060"/>
          </svg>
        {/each}
      </div>

      <div class="gs-doom-warning">⚠ DOOM SPHERE INCOMING ⚠</div>

      <!-- Bullets -->
      <div class="gs-bullet b1"></div>
      <div class="gs-bullet b2"></div>
      <div class="gs-bullet b3"></div>
      <div class="gs-ebullet e1"></div>
      <div class="gs-ebullet e2"></div>

      <!-- Player ship -->
      <svg class="gs-player" width="30" height="30" viewBox="0 0 24 24" fill="none">
        <polygon points="12,2 18,18 12,15 6,18" fill="#4169e1" stroke="#6a8fff" stroke-width="0.5"/>
        <polygon points="12,6 16,17 12,14.5 8,17" fill="#0047ab"/>
        <circle cx="12" cy="10" r="2" fill="#6a8fff" opacity="0.85"/>
        <polygon points="6,18 4,22 12,19" fill="rgba(65,105,225,0.4)"/>
        <polygon points="18,18 20,22 12,19" fill="rgba(65,105,225,0.4)"/>
      </svg>
    </div>
  </div>
</div>

<!-- ── BOSS STRIP ── -->
<div class="boss-strip">
  <div class="boss-inner">
    <div class="boss-skull">
      <svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="#dc143c" stroke-width="1.2" stroke-linecap="round" stroke-linejoin="round">
        <path d="M12 2a9 9 0 0 1 9 9 8.9 8.9 0 0 1-3 6.6V20a1 1 0 0 1-1 1H7a1 1 0 0 1-1-1v-2.4A8.9 8.9 0 0 1 3 11a9 9 0 0 1 9-9z" fill="rgba(220,20,60,0.08)"/>
        <line x1="9" y1="15" x2="9" y2="21"/>
        <line x1="12" y1="15" x2="12" y2="21"/>
        <line x1="15" y1="15" x2="15" y2="21"/>
        <circle cx="9" cy="10" r="2" fill="rgba(220,20,60,0.3)"/>
        <circle cx="15" cy="10" r="2" fill="rgba(220,20,60,0.3)"/>
      </svg>
    </div>
    <div>
      <div class="boss-label">⚠ Threat Level: Unclassified</div>
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
<div class="downloads" id="downloads">
  <div class="dl-header">
    <div class="dl-eyebrow">// download_protocol.init</div>
    <h2 class="dl-title">CHOOSE YOUR PLATFORM</h2>
    <p class="dl-version">v1.0.0 &mdash; Initial Release</p>
  </div>

  <div class="dl-grid">
    {#each downloads as dl}
      <div class="dl-card {dl.cls}">
        <div class="dl-platform">{dl.platform}</div>
        <div class="dl-format">{dl.format}</div>
        <a href={dl.href} class="dl-btn" download>
          <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
            <line x1="12" y1="5" x2="12" y2="19"/>
            <polyline points="5 12 12 19 19 12"/>
          </svg>
          {dl.label}
        </a>
      </div>
    {/each}
  </div>
</div>

<!-- ── FEATURES ── -->
<div class="features">
  <div class="features-eyebrow">// key_features.log</div>
  <h2 class="features-title">WHAT YOU'RE GETTING INTO</h2>
  <div class="features-grid">
    {#each features as f}
      <div class="feature-item">
        <svg class="feature-icon {f.red ? 'red' : ''}" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round">
          <path d={f.icon}/>
        </svg>
        <div class="feature-name">{f.name}</div>
        <p class="feature-desc">{f.desc}</p>
      </div>
    {/each}
  </div>
</div>

<!-- ── FOOTER ── -->
<footer>
  <div class="footer-back">
    <a href="/">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
        <line x1="19" y1="12" x2="5" y2="12"/>
        <polyline points="12 19 5 12 12 5"/>
      </svg>
      Back to MGL Library
    </a>
  </div>
  <div class="footer-copy">&copy; 2025 MidMan Studio. All rights reserved.</div>
</footer>

<style>
  /* ── Hero ── */
  .hero {
    position: relative; z-index: 1;
    display: grid; grid-template-columns: 1fr 1fr;
    align-items: center; gap: 60px;
    padding: 140px 80px 80px;
    max-width: 1280px; margin: 0 auto;
  }

  .live-badge {
    display: inline-flex; align-items: center; gap: 8px;
    font-family: var(--font-mono); font-size: 9px; color: var(--green);
    letter-spacing: 3px; text-transform: uppercase;
    padding: 5px 12px; border: 1px solid rgba(57,255,20,0.4);
    background: rgba(57,255,20,0.06); margin-bottom: 24px;
    text-shadow: var(--glow-green);
  }

  .live-dot {
    width: 5px; height: 5px; border-radius: 50%;
    background: var(--green); box-shadow: var(--glow-green);
    animation: blink 1.6s ease-in-out infinite;
  }

  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.2} }

  .hero-title {
    font-family: var(--font-head);
    font-size: clamp(24px, 4.5vw, 52px); font-weight: 900;
    line-height: 1.1; color: var(--text);
    margin-bottom: 10px; letter-spacing: -0.02em;
  }

  .hero-subtitle {
    font-family: var(--font-mono); font-size: 11px; color: var(--cobalt-light);
    letter-spacing: 3px; text-transform: uppercase; margin-bottom: 28px;
  }

  .hero-quote {
    font-size: 14px; line-height: 2; color: var(--text-2);
    border-left: 2px solid var(--cobalt-light); padding-left: 20px;
    margin-bottom: 36px;
  }

  .hero-quote em { font-style: normal; color: var(--text); }

  .stats-row { display: flex; gap: 36px; margin-bottom: 40px; flex-wrap: wrap; }

  .stat { display: flex; flex-direction: column; gap: 4px; }

  .stat-val {
    font-family: var(--font-head); font-size: 22px; font-weight: 900;
    color: var(--cobalt-light);
    text-shadow: 0 0 20px rgba(65,105,225,0.5);
  }
  .stat-val.red { color: var(--crimson); text-shadow: 0 0 20px rgba(220,20,60,0.4); }

  .stat-label {
    font-family: var(--font-mono); font-size: 9px; color: var(--dim);
    letter-spacing: 2px; text-transform: uppercase;
  }

  .hero-cta {
    display: inline-flex; align-items: center; gap: 10px;
    font-family: var(--font-head); font-size: 11px; font-weight: 700;
    letter-spacing: 3px; text-transform: uppercase;
    padding: 16px 40px;
    background: linear-gradient(135deg, var(--cobalt), var(--cobalt-light));
    color: #fff; box-shadow: var(--glow-cobalt);
    clip-path: polygon(10px 0%, 100% 0%, calc(100% - 10px) 100%, 0% 100%);
    transition: all 0.25s var(--ease);
  }
  .hero-cta:hover {
    background: linear-gradient(135deg, var(--cobalt-light), #6a8fff);
    transform: translateY(-2px);
  }
  .hero-cta svg { transition: transform 0.2s; }
  .hero-cta:hover svg { transform: translateY(3px); }

  /* ── Mini game screen ── */
  .game-screen-wrap { display: flex; align-items: center; justify-content: center; }

  .game-screen {
    width: 300px; height: 380px;
    background: linear-gradient(180deg, #010810, #040c1c);
    border: 1px solid rgba(65,105,225,0.3);
    box-shadow: var(--glow-cobalt), inset 0 0 40px rgba(0,0,0,0.6);
    position: relative; overflow: hidden;
  }

  .game-screen::before {
    content: ''; position: absolute; inset: 0; z-index: 5; pointer-events: none;
    background: repeating-linear-gradient(0deg, transparent, transparent 3px, rgba(65,105,225,0.025) 3px, rgba(65,105,225,0.025) 6px);
  }

  .gs-stars {
    position: absolute; inset: 0;
    background-image:
      radial-gradient(1px 1px at 10% 10%, rgba(255,255,255,0.8) 0%, transparent 100%),
      radial-gradient(1px 1px at 25% 40%, rgba(200,210,255,0.6) 0%, transparent 100%),
      radial-gradient(1px 1px at 40% 8%,  rgba(255,255,255,0.7) 0%, transparent 100%),
      radial-gradient(1px 1px at 55% 60%, rgba(200,210,255,0.5) 0%, transparent 100%),
      radial-gradient(1px 1px at 70% 20%, rgba(255,255,255,0.8) 0%, transparent 100%),
      radial-gradient(1px 1px at 82% 75%, rgba(200,210,255,0.6) 0%, transparent 100%),
      radial-gradient(1px 1px at 18% 85%, rgba(255,255,255,0.7) 0%, transparent 100%),
      radial-gradient(1.5px 1.5px at 60% 90%, rgba(65,105,225,0.5) 0%, transparent 100%);
  }

  .gs-planet {
    position: absolute; bottom: -50px; right: -30px;
    width: 170px; height: 170px; border-radius: 50%;
    background: radial-gradient(circle at 28% 28%, #0f2a4a, #020810);
    box-shadow: inset -16px -16px 32px rgba(0,0,0,0.8), 0 0 30px rgba(65,105,225,0.12);
    opacity: 0.45;
  }

  .gs-hud {
    position: absolute; top: 0; left: 0; right: 0; z-index: 4;
    padding: 10px 14px;
    display: flex; justify-content: space-between;
    background: linear-gradient(180deg, rgba(1,8,16,0.9), transparent);
  }

  .hud-item { display: flex; flex-direction: column; gap: 2px; }
  .hud-label { font-family: var(--font-mono); font-size: 7px; color: var(--dim); letter-spacing: 1px; }
  .hud-val { font-family: var(--font-mono); font-size: 11px; color: var(--cobalt-light); }
  .hud-val.white { color: var(--text); }
  .hud-lives { font-size: 11px; color: var(--crimson); }

  .gs-enemies {
    position: absolute; z-index: 3;
    display: flex; gap: 14px;
  }
  .gs-enemies.row1 { top: 55px; left: 24px; animation: em 2.8s ease-in-out infinite alternate; }
  .gs-enemies.row2 { top: 85px; left: 36px; animation: em 2.8s ease-in-out infinite alternate; animation-delay: -1.2s; }
  @keyframes em { from{transform:translateX(0)} to{transform:translateX(24px)} }

  .gs-player {
    position: absolute; bottom: 44px; left: 50%; z-index: 4;
    transform: translateX(-50%);
    animation: pfloat 2s ease-in-out infinite;
    filter: drop-shadow(0 0 6px rgba(65,105,225,0.9));
  }
  @keyframes pfloat { 0%,100%{transform:translateX(-50%) translateY(0)} 50%{transform:translateX(-50%) translateY(-5px)} }

  .gs-bullet {
    position: absolute; z-index: 3;
    width: 2px; height: 12px;
    background: linear-gradient(180deg, #6a8fff, rgba(65,105,225,0));
    border-radius: 1px; animation: bup 0.85s linear infinite;
  }
  .gs-bullet.b1{left:46%;top:200px;animation-delay:0s}
  .gs-bullet.b2{left:36%;top:180px;animation-delay:0.3s}
  .gs-bullet.b3{left:56%;top:190px;animation-delay:0.6s}
  @keyframes bup{from{transform:translateY(0);opacity:1}to{transform:translateY(-240px);opacity:0}}

  .gs-ebullet {
    position: absolute; z-index: 3;
    width: 2px; height: 10px;
    background: linear-gradient(180deg, var(--crimson), rgba(220,20,60,0));
    border-radius: 1px; animation: bdown 1.1s linear infinite;
  }
  .gs-ebullet.e1{left:30%;top:90px;animation-delay:0.2s}
  .gs-ebullet.e2{left:58%;top:100px;animation-delay:0.75s}
  @keyframes bdown{from{transform:translateY(0);opacity:1}to{transform:translateY(300px);opacity:0}}

  .gs-doom-warning {
    position: absolute; top: 160px; left: 50%; transform: translateX(-50%); z-index: 4;
    font-family: var(--font-mono); font-size: 7px; color: var(--crimson);
    white-space: nowrap; letter-spacing: 1px;
    animation: blink 1.2s ease-in-out infinite;
  }

  /* ── Boss strip ── */
  .boss-strip {
    position: relative; z-index: 1;
    background: linear-gradient(135deg, rgba(20,0,5,0.95), rgba(10,0,8,0.9));
    border-top: 1px solid rgba(220,20,60,0.3); border-bottom: 1px solid rgba(220,20,60,0.3);
    padding: 60px 80px;
  }

  .boss-inner {
    max-width: 1000px; margin: 0 auto;
    display: grid; grid-template-columns: auto 1fr;
    gap: 48px; align-items: center;
  }

  .boss-skull {
    width: 80px; height: 80px;
    display: flex; align-items: center; justify-content: center;
    border: 1px solid rgba(220,20,60,0.3);
    animation: rot 6s linear infinite; flex-shrink: 0;
    filter: drop-shadow(0 0 12px rgba(220,20,60,0.5));
  }
  @keyframes rot { from{transform:rotate(0deg)} to{transform:rotate(360deg)} }

  .boss-label {
    font-family: var(--font-mono); font-size: 10px; color: var(--crimson);
    letter-spacing: 4px; text-transform: uppercase; margin-bottom: 12px;
    animation: blink 1.6s ease-in-out infinite;
  }

  .boss-title {
    font-family: var(--font-head);
    font-size: clamp(20px, 3vw, 34px); font-weight: 900;
    color: var(--text); margin-bottom: 16px; line-height: 1.2;
  }

  .boss-quote {
    font-size: 13px; color: rgba(180,100,110,0.9); line-height: 2;
    border-left: 2px solid var(--crimson); padding-left: 20px;
    font-style: italic;
  }
  .boss-quote cite {
    display: block; font-style: normal;
    font-size: 11px; color: var(--dim); margin-top: 12px;
  }

  /* ── Downloads ── */
  .downloads {
    position: relative; z-index: 1;
    background: linear-gradient(180deg, var(--bg), rgba(6,12,26,0.98));
    border-top: 1px solid var(--border);
    padding: 100px 80px;
  }

  .dl-header { max-width: 1200px; margin: 0 auto 56px; }
  .dl-eyebrow { font-family: var(--font-mono); font-size: 10px; color: var(--cobalt-light); letter-spacing: 4px; text-transform: uppercase; margin-bottom: 8px; }
  .dl-title { font-family: var(--font-head); font-size: clamp(18px,3vw,32px); font-weight: 700; color: var(--text); line-height: 1.3; }
  .dl-version { font-family: var(--font-mono); font-size: 11px; color: var(--dim); margin-top: 12px; letter-spacing: 2px; }

  .dl-grid {
    max-width: 1200px; margin: 0 auto;
    display: grid; grid-template-columns: repeat(auto-fill, minmax(240px, 1fr)); gap: 20px;
  }

  .dl-card {
    background: rgba(7,15,31,0.9); border: 1px solid var(--border);
    padding: 32px 28px; position: relative; overflow: hidden;
    transition: transform 0.3s, border-color 0.3s, box-shadow 0.3s;
  }
  .dl-card::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 2px; }
  .dl-card.android::before { background: var(--green); box-shadow: var(--glow-green); }
  .dl-card.ios::before,
  .dl-card.windows::before { background: var(--cobalt-light); box-shadow: 0 0 8px rgba(65,105,225,0.8); }
  .dl-card.mac::before { background: var(--text-2); }

  .dl-card:hover { transform: translateY(-5px); }
  .dl-card.android:hover { border-color: rgba(57,255,20,0.5); box-shadow: 0 12px 40px rgba(57,255,20,0.1); }
  .dl-card.ios:hover, .dl-card.windows:hover { border-color: var(--cobalt-light); box-shadow: 0 12px 40px rgba(65,105,225,0.15); }
  .dl-card.mac:hover { border-color: rgba(143,160,192,0.4); }

  .dl-platform { font-family: var(--font-head); font-size: 12px; font-weight: 700; margin-bottom: 6px; }
  .dl-card.android .dl-platform { color: var(--green); text-shadow: var(--glow-green); }
  .dl-card.ios .dl-platform, .dl-card.windows .dl-platform { color: var(--cobalt-light); }
  .dl-card.mac .dl-platform { color: var(--text-2); }

  .dl-format { font-family: var(--font-mono); font-size: 10px; color: var(--dim); letter-spacing: 2px; text-transform: uppercase; margin-bottom: 28px; }

  .dl-btn {
    display: flex; align-items: center; justify-content: center; gap: 8px;
    font-family: var(--font-head); font-size: 9px; font-weight: 700;
    letter-spacing: 2px; text-transform: uppercase;
    padding: 13px 20px; border: 1px solid; transition: all 0.2s var(--ease);
  }
  .dl-card.android .dl-btn { color: var(--green); border-color: rgba(57,255,20,0.4); background: rgba(57,255,20,0.06); }
  .dl-card.android .dl-btn:hover { background: var(--green); color: var(--bg); box-shadow: var(--glow-green); }
  .dl-card.ios .dl-btn, .dl-card.windows .dl-btn { color: var(--cobalt-light); border-color: rgba(65,105,225,0.4); background: var(--cobalt-faint); }
  .dl-card.ios .dl-btn:hover, .dl-card.windows .dl-btn:hover { background: var(--cobalt-light); color: #fff; box-shadow: var(--glow-cobalt); }
  .dl-card.mac .dl-btn { color: var(--text-2); border-color: rgba(143,160,192,0.3); background: rgba(143,160,192,0.05); }
  .dl-card.mac .dl-btn:hover { background: var(--text-2); color: var(--bg); }

  /* ── Features ── */
  .features {
    position: relative; z-index: 1;
    padding: 100px 80px;
    max-width: 1200px; margin: 0 auto;
  }

  .features-eyebrow { font-family: var(--font-mono); font-size: 10px; color: var(--cobalt-light); letter-spacing: 4px; text-transform: uppercase; margin-bottom: 8px; }
  .features-title { font-family: var(--font-head); font-size: clamp(18px,2.5vw,26px); font-weight: 700; color: var(--text); margin-bottom: 56px; line-height: 1.3; }

  .features-grid {
    display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 20px;
  }

  .feature-item {
    background: rgba(7,15,31,0.9); border: 1px solid var(--border);
    padding: 28px; transition: border-color 0.3s;
  }
  .feature-item:hover { border-color: rgba(65,105,225,0.35); }

  .feature-icon {
    width: 36px; height: 36px;
    color: var(--cobalt-light);
    margin-bottom: 16px; display: block;
  }
  .feature-icon.red { color: var(--crimson); }

  .feature-name { font-family: var(--font-head); font-size: 10px; font-weight: 700; color: var(--cobalt-light); margin-bottom: 12px; line-height: 1.5; letter-spacing: 1px; }
  .feature-desc { font-size: 13px; color: var(--text-2); line-height: 1.9; }

  /* ── Footer ── */
  footer {
    position: relative; z-index: 1;
    border-top: 1px solid var(--border);
    padding: 36px 80px;
    display: flex; justify-content: space-between; align-items: center;
    flex-wrap: wrap; gap: 16px;
  }

  .footer-back a {
    font-family: var(--font-mono); font-size: 11px; color: var(--dim);
    letter-spacing: 2px; display: flex; align-items: center; gap: 8px;
    transition: color 0.2s;
  }
  .footer-back a:hover { color: var(--cobalt-light); }

  .footer-copy { font-family: var(--font-mono); font-size: 10px; color: var(--dim); }

  /* ── Responsive ── */
  @media (max-width: 900px) {
    .hero { grid-template-columns: 1fr; padding: 120px 24px 60px; }
    .game-screen-wrap { display: none; }
    .boss-strip { padding: 40px 24px; }
    .boss-inner { grid-template-columns: 1fr; text-align: center; }
    .boss-skull { margin: 0 auto; }
    .downloads { padding: 60px 24px; }
    .features { padding: 60px 24px; }
    footer { padding: 28px 24px; }
  }
</style>
