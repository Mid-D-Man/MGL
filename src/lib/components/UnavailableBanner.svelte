<!-- Scrolling red ticker shown when a download is unavailable -->
<div class="unavail-wrap" role="status" aria-label="Currently unavailable">
  <div class="unavail-track">
    {#each Array(16) as _}
      <span class="unavail-item">
        <svg width="11" height="11" viewBox="0 0 24 24" fill="none" stroke="currentColor"
             stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
          <path d="M10.29 3.86L1.82 18a2 2 0 0 0 1.71 3h16.94a2 2 0 0 0 1.71-3L13.71 3.86a2 2 0 0 0-3.42 0z"/>
          <line x1="12" y1="9" x2="12" y2="13"/>
          <line x1="12" y1="17" x2="12.01" y2="17"/>
        </svg>
        CURRENTLY UNAVAILABLE
      </span>
    {/each}
  </div>
</div>

<style>
  .unavail-wrap {
    overflow: hidden;
    width: 100%;
    background: rgba(220, 20, 60, 0.07);
    border-top: 1px solid rgba(220, 20, 60, 0.35);
    border-bottom: 1px solid rgba(220, 20, 60, 0.35);
    padding: 7px 0;
  }

  .unavail-track {
    display: flex;
    gap: 48px;
    width: max-content;
    animation: ticker 22s linear infinite;
  }

  .unavail-item {
    display: flex;
    align-items: center;
    gap: 9px;
    font-family: var(--font-mono);
    font-size: 9px;
    color: var(--crimson);
    letter-spacing: 3px;
    text-transform: uppercase;
    white-space: nowrap;
    flex-shrink: 0;
    text-shadow: var(--glow-crimson);
  }

  .unavail-item svg {
    color: var(--crimson);
    flex-shrink: 0;
    filter: drop-shadow(0 0 4px rgba(220, 20, 60, 0.6));
  }

  @keyframes ticker {
    from { transform: translateX(0); }
    to   { transform: translateX(-50%); }
  }
</style>
