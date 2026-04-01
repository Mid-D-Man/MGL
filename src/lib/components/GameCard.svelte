<!--
  GameCard.svelte
  Props:
    href        – link destination (omit for "coming soon")
    title       – game title
    genre       – genre string
    desc        – description
    platforms   – array of platform strings
    tag         – badge label (e.g. "LIVE")
    gif         – optional gif URL
    gifAlt      – alt text for gif
  Slot "visual" – animated SVG content when no gif
-->
<script lang="ts">
  export let href: string | null  = null;
  export let title: string        = 'Unknown Title';
  export let genre: string        = '';
  export let desc: string         = '';
  export let platforms: string[]  = [];
  export let tag: string | null   = null;
  export let gif: string | null   = null;
  export let gifAlt: string       = 'Game preview';

  $: isComingSoon = !href;
</script>

{#if isComingSoon}
  <div class="game-card card-soon">
    <div class="card-visual">
      <div class="card-soon-inner">
        <div class="lock-icon">
          <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor"
               stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
            <rect x="3" y="11" width="18" height="11" rx="2"/>
            <path d="M7 11V7a5 5 0 0 1 10 0v4"/>
          </svg>
        </div>
        <span class="soon-label">Classified</span>
      </div>
    </div>
    <div class="card-body">
      <div class="card-genre dim">{genre || '??? · Unknown'}</div>
      <h3 class="card-title dim">{title}</h3>
      <p class="card-desc dim">{desc || 'Transmission intercepted. Details classified. Stand by for further signal.'}</p>
      <div class="card-platforms">
        {#each platforms as p}
          <span class="chip dim-chip">{p}</span>
        {/each}
        {#if platforms.length === 0}
          <span class="chip dim-chip">TBA</span>
        {/if}
      </div>
      <div class="card-action dim">Coming Soon</div>
    </div>
  </div>

{:else}
  <a {href} class="game-card">
    <div class="card-visual">
      {#if gif}
        <img src={gif} alt={gifAlt} class="card-gif" />
      {:else}
        <slot name="visual">
          <div class="card-stars"></div>
          <div class="card-planet"></div>
        </slot>
      {/if}

      {#if tag}
        <div class="card-tag">{tag}</div>
      {/if}
    </div>

    <div class="card-body">
      {#if genre}
        <div class="card-genre">{genre}</div>
      {/if}
      <h3 class="card-title">{title}</h3>
      <p class="card-desc">{desc}</p>
      <div class="card-platforms">
        {#each platforms as p}
          <span class="chip">{p}</span>
        {/each}
      </div>
      <div class="card-action">
        View &amp; Download
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor"
             stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
          <line x1="5" y1="12" x2="19" y2="12"/>
          <polyline points="12 5 19 12 12 19"/>
        </svg>
      </div>
    </div>
  </a>
{/if}

<style>
  .game-card {
    background: rgba(7, 15, 31, 0.9);
    border: 1px solid var(--border);
    display: block;
    color: inherit;
    transition: border-color 0.3s, transform 0.3s, box-shadow 0.3s;
    position: relative;
    overflow: hidden;
  }

  .game-card:not(.card-soon)::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(65, 105, 225, 0.05) 0%, transparent 60%);
    opacity: 0;
    transition: opacity 0.3s;
  }

  .game-card:not(.card-soon):hover {
    border-color: var(--cobalt-light);
    transform: translateY(-5px);
    box-shadow: 0 16px 48px rgba(65, 105, 225, 0.2), var(--glow-cobalt);
  }
  .game-card:not(.card-soon):hover::before { opacity: 1; }

  .card-soon { cursor: default; }

  .card-visual {
    height: 200px;
    background: linear-gradient(160deg, #050c1a 0%, #0a1528 50%, #050c1a 100%);
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    overflow: hidden;
  }

  .card-soon .card-visual {
    background: linear-gradient(160deg, #060606, #0e0e0e);
  }

  .card-gif {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
  }

  .card-stars {
    position: absolute;
    inset: 0;
    background-image:
      radial-gradient(1px 1px at 12% 20%, rgba(255,255,255,0.7) 0%, transparent 100%),
      radial-gradient(1px 1px at 28% 65%, rgba(180,200,255,0.5) 0%, transparent 100%),
      radial-gradient(1px 1px at 48% 15%, rgba(255,255,255,0.6) 0%, transparent 100%),
      radial-gradient(1px 1px at 65% 75%, rgba(180,200,255,0.4) 0%, transparent 100%),
      radial-gradient(1px 1px at 78% 30%, rgba(255,255,255,0.7) 0%, transparent 100%),
      radial-gradient(1.5px 1.5px at 20% 85%, rgba(65,105,225,0.5) 0%, transparent 100%);
  }

  .card-planet {
    position: absolute;
    bottom: -30px; right: -20px;
    width: 130px; height: 130px;
    border-radius: 50%;
    background: radial-gradient(circle at 30% 30%, #0f2a4a, #020810);
    box-shadow: inset -12px -12px 28px rgba(0,0,0,0.7), 0 0 30px rgba(65,105,225,0.15);
    opacity: 0.5;
  }

  .card-tag {
    position: absolute;
    top: 12px; left: 12px;
    font-family: var(--font-mono);
    font-size: 9px;
    letter-spacing: 2px;
    text-transform: uppercase;
    padding: 4px 10px;
    background: rgba(57, 255, 20, 0.1);
    border: 1px solid rgba(57, 255, 20, 0.5);
    color: var(--green);
    text-shadow: var(--glow-green);
    z-index: 2;
  }

  .card-soon-inner {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
    position: relative;
    z-index: 2;
  }

  .lock-icon {
    width: 56px; height: 56px;
    display: flex;
    align-items: center;
    justify-content: center;
    border: 1px solid rgba(65, 105, 225, 0.12);
    color: var(--dim);
    opacity: 0.4;
  }

  .soon-label {
    font-family: var(--font-head);
    font-size: 9px;
    color: var(--dim);
    letter-spacing: 4px;
    text-transform: uppercase;
    opacity: 0.4;
  }

  .card-body { padding: 24px; }

  .card-genre {
    font-family: var(--font-mono);
    font-size: 10px;
    color: var(--cobalt-light);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 10px;
  }

  .card-title {
    font-family: var(--font-head);
    font-size: 16px;
    font-weight: 700;
    color: var(--text);
    margin-bottom: 12px;
    line-height: 1.4;
  }

  .card-desc {
    font-size: 13px;
    line-height: 1.85;
    color: var(--text-2);
    margin-bottom: 20px;
  }

  .card-platforms {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
    margin-bottom: 20px;
  }

  .chip {
    font-family: var(--font-mono);
    font-size: 9px;
    letter-spacing: 1px;
    text-transform: uppercase;
    padding: 3px 8px;
    border: 1px solid var(--border);
    color: var(--dim);
  }

  .dim-chip {
    color: rgba(74, 88, 128, 0.3);
    border-color: rgba(74, 88, 128, 0.15);
  }

  .card-action {
    font-family: var(--font-mono);
    font-size: 10px;
    color: var(--cobalt-light);
    letter-spacing: 2px;
    text-transform: uppercase;
    display: flex;
    align-items: center;
    gap: 8px;
    transition: gap 0.2s;
  }

  .game-card:hover .card-action { gap: 12px; }

  .dim { color: var(--dim); opacity: 0.4; }

  @media (max-width: 480px) {
    .card-body { padding: 20px 16px; }
    .card-title { font-size: 15px; }
  }
</style>
