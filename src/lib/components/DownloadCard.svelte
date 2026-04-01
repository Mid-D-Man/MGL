<script lang="ts">
  import UnavailableBanner from './UnavailableBanner.svelte';
  import PlatformGuide     from './PlatformGuide.svelte';

  export let platform: string;
  export let format: string;
  export let href: string;
  export let label: string;
  export let cls: 'android' | 'ios' | 'windows' | 'mac';
  export let available: boolean = false;

  let guideOpen = false;
</script>

<div class="dl-card {cls}" class:unavailable={!available}>
  <div class="top-bar"></div>

  {#if !available}
    <UnavailableBanner />
  {/if}

  <div class="card-inner">
    <div class="dl-platform">{platform}</div>
    <div class="dl-format">{format}</div>

    {#if available}
      <a {href} class="dl-btn" download>
        <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor"
             stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
          <line x1="12" y1="5" x2="12" y2="19"/>
          <polyline points="5 12 12 19 19 12"/>
        </svg>
        {label}
      </a>
    {:else}
      <div class="dl-btn-disabled" aria-disabled="true">
        <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor"
             stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
          <circle cx="12" cy="12" r="10"/>
          <line x1="4.93" y1="4.93" x2="19.07" y2="19.07"/>
        </svg>
        Unavailable
      </div>
    {/if}

    <button class="guide-toggle" on:click={() => guideOpen = !guideOpen}
            aria-expanded={guideOpen}>
      <svg width="11" height="11" viewBox="0 0 24 24" fill="none" stroke="currentColor"
           stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
        <circle cx="12" cy="12" r="10"/>
        <line x1="12" y1="8" x2="12" y2="12"/>
        <line x1="12" y1="16" x2="12.01" y2="16"/>
      </svg>
      Installation Guide
      <svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor"
           stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
           style="transform: rotate({guideOpen ? 180 : 0}deg); transition: transform 0.2s;"
           aria-hidden="true">
        <polyline points="6 9 12 15 18 9"/>
      </svg>
    </button>

    {#if guideOpen}
      <PlatformGuide platform={cls} />
    {/if}
  </div>
</div>

<style>
  .dl-card {
    background: rgba(7, 15, 31, 0.92);
    border: 1px solid var(--border);
    position: relative;
    overflow: hidden;
    transition: transform 0.3s, border-color 0.3s, box-shadow 0.3s;
    display: flex;
    flex-direction: column;
  }

  .dl-card:not(.unavailable):hover { transform: translateY(-4px); }

  .top-bar {
    height: 2px;
    flex-shrink: 0;
  }

  .dl-card.android .top-bar    { background: var(--green); box-shadow: 0 0 8px rgba(57,255,20,0.8); }
  .dl-card.ios .top-bar,
  .dl-card.windows .top-bar    { background: var(--cobalt-light); box-shadow: 0 0 8px rgba(65,105,225,0.8); }
  .dl-card.mac .top-bar        { background: var(--text-2); }

  .dl-card.android:not(.unavailable):hover  { border-color: rgba(57,255,20,0.5);     box-shadow: 0 12px 40px rgba(57,255,20,0.1); }
  .dl-card.ios:not(.unavailable):hover,
  .dl-card.windows:not(.unavailable):hover  { border-color: var(--cobalt-light);      box-shadow: 0 12px 40px rgba(65,105,225,0.15); }
  .dl-card.mac:not(.unavailable):hover      { border-color: rgba(143,160,192,0.4); }

  .card-inner { padding: 28px; }

  .dl-platform {
    font-family: var(--font-head);
    font-size: 12px;
    font-weight: 700;
    margin-bottom: 6px;
  }

  .dl-card.android .dl-platform  { color: var(--green);       text-shadow: var(--glow-green); }
  .dl-card.ios .dl-platform,
  .dl-card.windows .dl-platform  { color: var(--cobalt-light); }
  .dl-card.mac .dl-platform      { color: var(--text-2); }

  .unavailable .dl-platform { opacity: 0.45; }

  .dl-format {
    font-family: var(--font-mono);
    font-size: 10px;
    color: var(--dim);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 24px;
  }

  /* Active download button */
  .dl-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    font-family: var(--font-head);
    font-size: 9px;
    font-weight: 700;
    letter-spacing: 2px;
    text-transform: uppercase;
    padding: 13px 20px;
    border: 1px solid;
    transition: all 0.2s var(--ease);
    margin-bottom: 16px;
    cursor: pointer;
    text-decoration: none;
  }

  .dl-card.android .dl-btn   { color: var(--green);       border-color: rgba(57,255,20,0.4);    background: rgba(57,255,20,0.06); }
  .dl-card.ios .dl-btn,
  .dl-card.windows .dl-btn   { color: var(--cobalt-light); border-color: rgba(65,105,225,0.4);   background: var(--cobalt-faint); }
  .dl-card.mac .dl-btn       { color: var(--text-2);       border-color: rgba(143,160,192,0.3);  background: rgba(143,160,192,0.05); }

  .dl-card.android .dl-btn:hover  { background: var(--green);       color: var(--bg);  box-shadow: var(--glow-green); }
  .dl-card.ios .dl-btn:hover,
  .dl-card.windows .dl-btn:hover  { background: var(--cobalt-light); color: #fff;       box-shadow: var(--glow-cobalt); }
  .dl-card.mac .dl-btn:hover      { background: var(--text-2);       color: var(--bg); }

  /* Disabled state */
  .dl-btn-disabled {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    font-family: var(--font-head);
    font-size: 9px;
    font-weight: 700;
    letter-spacing: 2px;
    text-transform: uppercase;
    padding: 13px 20px;
    border: 1px solid rgba(220, 20, 60, 0.2);
    background: rgba(220, 20, 60, 0.04);
    color: rgba(220, 20, 60, 0.4);
    margin-bottom: 16px;
    cursor: not-allowed;
    user-select: none;
  }

  /* Guide toggle */
  .guide-toggle {
    display: flex;
    align-items: center;
    gap: 7px;
    font-family: var(--font-mono);
    font-size: 9px;
    color: var(--dim);
    letter-spacing: 2px;
    text-transform: uppercase;
    background: none;
    border: none;
    cursor: pointer;
    padding: 0;
    transition: color 0.2s;
  }

  .guide-toggle:hover { color: var(--cobalt-light); }
</style>
