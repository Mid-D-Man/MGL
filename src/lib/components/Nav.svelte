<script lang="ts">
  interface NavLink {
    label: string;
    href: string;
    external?: boolean;
  }

  export let links: NavLink[]        = [];
  export let backHref: string | null = null;
  export let backLabel: string | null = null;
  export let breadcrumb: string | null = null;

  let menuOpen = false;
</script>

<nav>
  <div class="nav-left">
    {#if backHref}
      <a href={backHref} class="nav-back">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor"
             stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
          <line x1="19" y1="12" x2="5" y2="12"/>
          <polyline points="12 19 5 12 12 5"/>
        </svg>
        {backLabel ?? 'Back'}
      </a>
    {:else}
      <a href="/" class="nav-logo">M<span>GL</span></a>
    {/if}
  </div>

  <div class="nav-right">
    {#if breadcrumb}
      <div class="nav-breadcrumb">
        <span class="bc-parent">MidMan Game Library</span>
        <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor"
             stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
          <polyline points="9 18 15 12 9 6"/>
        </svg>
        <strong>{breadcrumb}</strong>
      </div>
    {:else if links.length > 0}
      <div class="nav-links">
        {#each links as link}
          <a
            href={link.href}
            class="nav-link"
            target={link.external ? '_blank' : undefined}
            rel={link.external ? 'noopener noreferrer' : undefined}
          >
            {link.label}
          </a>
        {/each}
      </div>

      <!-- Mobile hamburger -->
      <button class="nav-burger" aria-label="Toggle navigation" aria-expanded={menuOpen}
              on:click={() => menuOpen = !menuOpen}>
        <span class:open={menuOpen}></span>
        <span class:open={menuOpen}></span>
        <span class:open={menuOpen}></span>
      </button>
    {/if}
  </div>
</nav>

<!-- Mobile dropdown -->
{#if menuOpen && links.length > 0}
  <div class="mobile-menu">
    {#each links as link}
      
        href={link.href}
        class="mobile-link"
        target={link.external ? '_blank' : undefined}
        rel={link.external ? 'noopener noreferrer' : undefined}
        on:click={() => menuOpen = false}
      >
        {link.label}
      </a>
    {/each}
  </div>
{/if}

<style>
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 16px 48px;
    background: rgba(4, 8, 18, 0.9);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--border);
  }

  .nav-left, .nav-right {
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .nav-logo {
    font-family: var(--font-head);
    font-size: 14px;
    font-weight: 900;
    color: var(--text);
    letter-spacing: 3px;
  }
  .nav-logo span { color: var(--cobalt-light); }

  .nav-back {
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--dim);
    letter-spacing: 2px;
    text-transform: uppercase;
    display: flex;
    align-items: center;
    gap: 8px;
    transition: color 0.2s;
  }
  .nav-back:hover { color: var(--cobalt-light); }

  .nav-links { display: flex; gap: 32px; }

  .nav-link {
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--dim);
    letter-spacing: 2px;
    text-transform: uppercase;
    transition: color 0.2s;
  }
  .nav-link:hover { color: var(--cobalt-light); }

  .nav-breadcrumb {
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--dim);
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .nav-breadcrumb strong { color: var(--cobalt-light); }
  .bc-parent { display: inline; }

  /* Hamburger */
  .nav-burger {
    display: none;
    flex-direction: column;
    gap: 5px;
    background: none;
    border: none;
    cursor: pointer;
    padding: 4px;
  }

  .nav-burger span {
    display: block;
    width: 22px;
    height: 1.5px;
    background: var(--dim);
    transition: all 0.25s;
    transform-origin: center;
  }

  .nav-burger span.open:nth-child(1) { transform: translateY(6.5px) rotate(45deg); background: var(--cobalt-light); }
  .nav-burger span.open:nth-child(2) { opacity: 0; }
  .nav-burger span.open:nth-child(3) { transform: translateY(-6.5px) rotate(-45deg); background: var(--cobalt-light); }

  /* Mobile menu dropdown */
  .mobile-menu {
    position: fixed;
    top: 57px; left: 0; right: 0;
    z-index: 99;
    background: rgba(4, 8, 18, 0.97);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--border);
    display: flex;
    flex-direction: column;
    padding: 8px 0;
    animation: slide-down 0.2s ease;
  }

  @keyframes slide-down { from { transform: translateY(-8px); opacity: 0; } to { transform: translateY(0); opacity: 1; } }

  .mobile-link {
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--dim);
    letter-spacing: 2px;
    text-transform: uppercase;
    padding: 14px 24px;
    border-bottom: 1px solid rgba(65, 105, 225, 0.06);
    transition: color 0.2s, background 0.2s;
  }
  .mobile-link:hover { color: var(--cobalt-light); background: rgba(65, 105, 225, 0.04); }
  .mobile-link:last-child { border-bottom: none; }

  @media (max-width: 768px) {
    nav { padding: 14px 20px; }
    .nav-links { display: none; }
    .nav-burger { display: flex; }
    .bc-parent { display: none; }
    .nav-breadcrumb { font-size: 10px; }
  }
</style>
