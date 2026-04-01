<script lang="ts">
  import { page } from '$app/stores';

  interface NavLink {
    label: string;
    href: string;
    external?: boolean;
  }

  export let links: NavLink[] = [];
  export let backHref: string | null = null;
  export let backLabel: string | null = null;
  export let breadcrumb: string | null = null;
</script>

<nav>
  <div class="nav-left">
    {#if backHref}
      <a href={backHref} class="nav-back">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
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
        MidMan Game Library
        <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
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
    {/if}
  </div>
</nav>

<style>
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 16px 48px;
    background: rgba(4, 8, 18, 0.85);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--border);
  }

  .nav-left, .nav-right {
    display: flex;
    align-items: center;
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

  .nav-links {
    display: flex;
    gap: 32px;
  }

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

  @media (max-width: 600px) {
    nav { padding: 14px 20px; }
    .nav-links { display: none; }
    .nav-breadcrumb { display: none; }
  }
</style>
