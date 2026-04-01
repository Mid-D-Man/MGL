<script lang="ts">
  export let backHref: string | null = null;
  export let backLabel: string = 'Back';

  let legalOpen = false;
</script>

<footer>
  <div class="footer-top">
    <div class="footer-brand">
      <span class="brand-m">M</span><span class="brand-gl">GL</span>
      <span class="brand-tag">An Independent Game Library by MidMan Studio</span>
    </div>

    {#if backHref}
      <a href={backHref} class="footer-back">
        <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor"
             stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
          <line x1="19" y1="12" x2="5" y2="12"/>
          <polyline points="12 19 5 12 12 5"/>
        </svg>
        {backLabel}
      </a>
    {/if}

    <div class="footer-copy">&copy; {new Date().getFullYear()} MidMan Studio. All rights reserved.</div>
  </div>

  <!-- Legal -->
  <div class="legal-section">
    <button class="legal-toggle" on:click={() => legalOpen = !legalOpen}
            aria-expanded={legalOpen}>
      <svg width="11" height="11" viewBox="0 0 24 24" fill="none" stroke="currentColor"
           stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
        <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/>
      </svg>
      Legal Disclaimer &amp; Liability Notice
      <svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor"
           stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
           style="transform: rotate({legalOpen ? 180 : 0}deg); transition: transform 0.2s;"
           aria-hidden="true">
        <polyline points="6 9 12 15 18 9"/>
      </svg>
    </button>

    {#if legalOpen}
      <div class="legal-body">
        <h3 class="legal-title">Disclaimer of Liability</h3>

        <p>All software, games, and downloadable content provided through the MidMan Game Library (MGL) platform is offered strictly on an <strong>"as-is"</strong> and <strong>"as-available"</strong> basis, without warranties of any kind, express or implied, including but not limited to implied warranties of merchantability, fitness for a particular purpose, or non-infringement.</p>

        <p>By downloading, installing, accessing, or otherwise using any software or content distributed through this platform, you expressly acknowledge and agree that:</p>

        <ul>
          <li>MidMan Studio, its developers, contributors, and all affiliated parties <strong>shall not be held liable</strong> for any direct, indirect, incidental, special, consequential, or punitive damages arising from your use of, or inability to use, any software obtained through this platform.</li>
          <li>This includes, without limitation, any loss of data, device damage, software conflicts, security vulnerabilities, personal injury, financial loss, or any other harm whatsoever, regardless of whether MidMan Studio was advised of the possibility of such damages.</li>
          <li>You are solely responsible for evaluating the suitability of any software for your device and use case, and for complying with all applicable laws and regulations in your jurisdiction.</li>
          <li>Sideloading applications (particularly on iOS) may void device warranties, violate platform terms of service, or introduce security risks. You assume all risks associated with such actions.</li>
          <li>MidMan Studio makes no representations regarding the continuous availability, accuracy, or error-free operation of any software distributed through this platform.</li>
          <li>All trademarks, game titles, and associated assets are the intellectual property of MidMan Studio. Redistribution, modification, or reverse engineering without explicit written consent is prohibited.</li>
        </ul>

        <p class="legal-close">Your use of this platform constitutes your full acceptance of this disclaimer. If you do not agree to these terms, do not download or use any software distributed through MGL.</p>

        <div class="legal-ver">Effective: 2025 &mdash; MidMan Studio</div>
      </div>
    {/if}
  </div>
</footer>

<style>
  footer {
    position: relative;
    z-index: 1;
    border-top: 1px solid var(--border);
  }

  .footer-top {
    padding: 36px 48px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 16px;
  }

  .footer-brand {
    display: flex;
    align-items: center;
    gap: 12px;
    flex-wrap: wrap;
  }

  .brand-m  { font-family: var(--font-head); font-size: 13px; font-weight: 900; color: var(--text); letter-spacing: 2px; }
  .brand-gl { font-family: var(--font-head); font-size: 13px; font-weight: 900; color: var(--cobalt-light); letter-spacing: 2px; }

  .brand-tag {
    font-family: var(--font-mono);
    font-size: 9px;
    color: var(--dim);
    letter-spacing: 2px;
    text-transform: uppercase;
    padding-left: 12px;
    border-left: 1px solid var(--border);
  }

  .footer-back {
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--dim);
    letter-spacing: 2px;
    display: flex;
    align-items: center;
    gap: 8px;
    transition: color 0.2s;
    text-transform: uppercase;
  }
  .footer-back:hover { color: var(--cobalt-light); }

  .footer-copy {
    font-family: var(--font-mono);
    font-size: 10px;
    color: var(--dim);
  }

  /* Legal */
  .legal-section {
    border-top: 1px solid rgba(65, 105, 225, 0.08);
  }

  .legal-toggle {
    width: 100%;
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 14px 48px;
    font-family: var(--font-mono);
    font-size: 9px;
    color: rgba(74, 88, 128, 0.5);
    letter-spacing: 2px;
    text-transform: uppercase;
    background: none;
    border: none;
    cursor: pointer;
    transition: color 0.2s;
    text-align: left;
  }
  .legal-toggle:hover { color: var(--dim); }

  .legal-body {
    padding: 32px 48px 40px;
    border-top: 1px solid rgba(65, 105, 225, 0.06);
    animation: fadein 0.2s ease;
    display: flex;
    flex-direction: column;
    gap: 16px;
    max-width: 900px;
  }

  @keyframes fadein { from { opacity: 0; } to { opacity: 1; } }

  .legal-title {
    font-family: var(--font-head);
    font-size: 11px;
    font-weight: 700;
    color: var(--dim);
    letter-spacing: 2px;
    margin-bottom: 4px;
  }

  .legal-body p {
    font-size: 11px;
    line-height: 1.9;
    color: rgba(74, 88, 128, 0.7);
  }

  .legal-body strong { color: var(--dim); }

  .legal-body ul {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 10px;
    padding-left: 16px;
  }

  .legal-body li {
    font-size: 11px;
    line-height: 1.9;
    color: rgba(74, 88, 128, 0.65);
    position: relative;
  }

  .legal-body li::before {
    content: '//';
    position: absolute;
    left: -20px;
    font-family: var(--font-mono);
    font-size: 9px;
    color: rgba(65, 105, 225, 0.25);
  }

  .legal-body li strong { color: var(--dim); }

  .legal-close {
    font-style: italic;
  }

  .legal-ver {
    font-family: var(--font-mono);
    font-size: 9px;
    color: rgba(74, 88, 128, 0.35);
    letter-spacing: 2px;
    padding-top: 8px;
    border-top: 1px solid rgba(65, 105, 225, 0.06);
  }

  @media (max-width: 768px) {
    .footer-top        { padding: 28px 20px; flex-direction: column; align-items: center; text-align: center; }
    .footer-brand      { justify-content: center; flex-direction: column; align-items: center; gap: 8px; }
    .brand-tag         { padding-left: 0; border-left: none; border-top: 1px solid var(--border); padding-top: 8px; text-align: center; }
    .legal-toggle      { padding: 14px 20px; justify-content: center; }
    .legal-body        { padding: 24px 20px 32px; }
  }
</style>
