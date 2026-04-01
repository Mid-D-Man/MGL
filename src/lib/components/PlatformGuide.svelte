<script lang="ts">
  export let platform: 'android' | 'ios' | 'windows' | 'mac';

  const guides: Record<string, { title: string; steps: string[] }> = {
    android: {
      title: 'Android Installation',
      steps: [
        'Open Settings on your device and navigate to Security or Privacy.',
        'Enable "Install Unknown Apps" or "Unknown Sources" for your browser or file manager.',
        'Download the APK file using the button above.',
        'Open your Downloads folder and tap the APK file.',
        'Tap Install when prompted and wait for installation to complete.',
        'Launch Foreign Protocol from your app drawer.',
      ],
    },
    ios: {
      title: 'iOS Sideload Installation',
      steps: [
        'Install AltStore on your Mac or PC by visiting altstore.io and following their setup guide.',
        'Connect your iPhone or iPad to your computer via USB.',
        'Open AltStore on your computer and navigate to My Apps.',
        'Tap the + button and select the downloaded IPA file.',
        'AltStore will sign and install the app. Free Apple ID apps expire every 7 days.',
        'On your device: Settings → General → VPN & Device Management → trust the developer certificate.',
        'Launch Foreign Protocol from your home screen.',
      ],
    },
    windows: {
      title: 'Windows Installation',
      steps: [
        'Download the EXE installer using the button above.',
        'Locate the file in your Downloads folder and double-click to run.',
        'If Windows SmartScreen appears, click "More info" then "Run anyway" — this is expected for unsigned indie software.',
        'Follow the installation wizard steps.',
        'Launch Foreign Protocol from your Desktop shortcut or Start Menu.',
      ],
    },
    mac: {
      title: 'macOS Installation',
      steps: [
        'Download the DMG file using the button above.',
        'Double-click the DMG to mount it — a Finder window will open.',
        'Drag Foreign Protocol into your Applications folder.',
        'On first launch, right-click the app icon and select Open (do not double-click).',
        'If macOS Gatekeeper blocks the app: System Preferences → Security & Privacy → General → click "Open Anyway".',
        'Launch Foreign Protocol from your Applications folder or Launchpad.',
      ],
    },
  };

  const guide = guides[platform];
</script>

<div class="guide">
  <div class="guide-title">{guide.title}</div>
  <ol class="guide-steps">
    {#each guide.steps as step, i}
      <li class="guide-step">
        <span class="step-num">{String(i + 1).padStart(2, '0')}</span>
        <span class="step-text">{step}</span>
      </li>
    {/each}
  </ol>
</div>

<style>
  .guide {
    margin-top: 20px;
    padding: 20px;
    background: rgba(4, 8, 18, 0.8);
    border: 1px solid var(--border);
    animation: fadein 0.2s ease;
  }

  @keyframes fadein { from { opacity: 0; transform: translateY(-4px); } to { opacity: 1; transform: translateY(0); } }

  .guide-title {
    font-family: var(--font-mono);
    font-size: 9px;
    color: var(--cobalt-light);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 16px;
  }

  .guide-steps {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .guide-step {
    display: flex;
    gap: 14px;
    align-items: flex-start;
  }

  .step-num {
    font-family: var(--font-mono);
    font-size: 9px;
    color: var(--cobalt-light);
    letter-spacing: 1px;
    flex-shrink: 0;
    margin-top: 2px;
    opacity: 0.7;
  }

  .step-text {
    font-size: 12px;
    line-height: 1.8;
    color: var(--text-2);
  }
</style>
