<script lang="ts">
  export let eyebrow: string;
  export let title: string;
  export let subtitle: string | null = null;
</script>

<div class="section-header">
  <div class="eyebrow">// {eyebrow}</div>
  <h2 class="title">{title}</h2>
  {#if subtitle}
    <p class="subtitle">{subtitle}</p>
  {/if}
</div>

<style>
  .section-header { margin-bottom: 48px; }

  .eyebrow {
    font-family: var(--font-mono);
    font-size: 10px;
    color: var(--cobalt-light);
    letter-spacing: 4px;
    text-transform: uppercase;
    margin-bottom: 8px;
  }

  .title {
    font-family: var(--font-head);
    font-size: clamp(18px, 3vw, 30px);
    font-weight: 700;
    color: var(--text);
    line-height: 1.3;
  }

  .subtitle {
    margin-top: 12px;
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--dim);
    letter-spacing: 2px;
  }
</style>
