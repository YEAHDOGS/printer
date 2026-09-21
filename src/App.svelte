<script>
  import { onMount } from "svelte";
  import badge from "./assets/made-by-dogs.png";

  onMount(() => {
    const io = new IntersectionObserver(
      (entries) => {
        for (const e of entries) {
          if (e.isIntersecting) {
            e.target.querySelectorAll(".rv").forEach((el) => el.classList.add("in"));
          }
        }
      },
      { threshold: 0.3 }
    );
    document.querySelectorAll(".panel").forEach((p) => io.observe(p));
    return () => io.disconnect();
  });
</script>

<svelte:head>
  <title>Printer — by DOGS</title>
  <meta name="description" content="The printer, reinvented. No tracking watermarks, no spyware, ink by the gallon, no drivers, native on every device." />
</svelte:head>

<!-- reusable ink-drop backdrop -->
{#snippet inkdrop(uid)}
  <svg class="bg-art drift" viewBox="0 0 400 800" preserveAspectRatio="xMidYMid slice" aria-hidden="true">
    <defs>
      <linearGradient id="deep-{uid}" x1="0" y1="0" x2="0" y2="1">
        <stop offset="0" stop-color="#07121e" />
        <stop offset="0.55" stop-color="#04070c" />
        <stop offset="1" stop-color="#020409" />
      </linearGradient>
      <linearGradient id="sheet-{uid}" x1="0" y1="0" x2="1" y2="1">
        <stop offset="0" stop-color="#eef4fb" />
        <stop offset="1" stop-color="#9fb6d4" />
      </linearGradient>
      <linearGradient id="drop-{uid}" x1="0" y1="0" x2="0" y2="1">
        <stop offset="0" stop-color="#67e8f9" />
        <stop offset="1" stop-color="#0e7490" />
      </linearGradient>
      <radialGradient id="glow-{uid}" cx="0.5" cy="0.5" r="0.5">
        <stop offset="0" stop-color="#22d3ee" stop-opacity="0.16" />
        <stop offset="1" stop-color="#22d3ee" stop-opacity="0" />
      </radialGradient>
      <filter id="soft-{uid}" x="-50%" y="-50%" width="200%" height="200%">
        <feGaussianBlur stdDeviation="9" />
      </filter>
    </defs>
    <rect width="400" height="800" fill="url(#deep-{uid})" />
    <ellipse cx="200" cy="420" rx="240" ry="200" fill="url(#glow-{uid})" />
    <!-- the sheet -->
    <g opacity="0.9" transform="rotate(-6 200 430)">
      <rect x="120" y="250" width="160" height="230" rx="6" fill="url(#sheet-{uid})" opacity="0.92" />
      <rect x="136" y="280" width="128" height="8" rx="4" fill="#0e7490" opacity="0.55" />
      <rect x="136" y="300" width="96" height="8" rx="4" fill="#0e7490" opacity="0.35" />
      <rect x="136" y="320" width="112" height="8" rx="4" fill="#0e7490" opacity="0.45" />
      <rect x="136" y="352" width="128" height="64" rx="4" fill="url(#drop-{uid})" opacity="0.75" />
    </g>
    <!-- falling ink -->
    <g filter="url(#soft-{uid})" opacity="0.7">
      <path d="M200 120 c14 20 22 34 22 46 a22 22 0 1 1 -44 0 c0 -12 8 -26 22 -46" fill="url(#drop-{uid})" />
      <circle cx="150" cy="560" r="26" fill="url(#drop-{uid})" opacity="0.5" />
      <circle cx="262" cy="610" r="15" fill="url(#drop-{uid})" opacity="0.6" />
      <circle cx="96" cy="200" r="10" fill="url(#drop-{uid})" opacity="0.5" />
      <circle cx="312" cy="180" r="18" fill="url(#drop-{uid})" opacity="0.4" />
    </g>
    <g opacity="0.9">
      <path d="M200 330 c10 15 16 25 16 34 a16 16 0 1 1 -32 0 c0 -9 6 -19 16 -34" fill="url(#drop-{uid})" />
      <circle cx="238" cy="250" r="7" fill="#67e8f9" opacity="0.8" />
      <circle cx="168" cy="470" r="9" fill="#22d3ee" opacity="0.55" />
    </g>
  </svg>
{/snippet}

<main>
  <!-- HERO -->
  <section class="panel" id="top" aria-label="Printer by DOGS">
    {@render inkdrop("hero")}
    <div class="scrim"></div>
    <div class="wrap">
      <p class="kicker rv">DOGS &middot; printing</p>
      <h1 class="rv d1">PRINTER<span class="dot">.</span></h1>
      <p class="sub rv d2">The printer, <b>reinvented.</b></p>
    </div>
    <span class="cue" aria-hidden="true">scroll</span>
  </section>

  <!-- CLEAN -->
  <section class="panel" id="clean" aria-label="No tracking, no spyware">
    {@render inkdrop("clean")}
    <div class="scrim"></div>
    <div class="wrap">
      <p class="kicker rv">01 &middot; Clean</p>
      <h2 class="rv d1">NO TRACKING.<br />NO <em>SPYWARE.</em></h2>
      <p class="sub rv d2">No watermark dots. No phone-home.</p>
      <p class="sub rv d3">Legally clean, <b>by design.</b></p>
    </div>
  </section>

  <!-- INK -->
  <section class="panel" id="ink" aria-label="Ink by the gallon">
    {@render inkdrop("ink")}
    <div class="scrim"></div>
    <div class="wrap">
      <p class="kicker rv">02 &middot; Ink</p>
      <h2 class="rv d1">INK BY<br />THE <em>GALLON.</em></h2>
      <p class="sub rv d2">Giant-capacity tanks. <b>Entire jugs.</b></p>
      <p class="sub rv d3">Subscriptions that <b>never bind</b> to the hardware.</p>
    </div>
  </section>

  <!-- OUTPUT -->
  <section class="panel" id="output" aria-label="Fast and sharp output">
    {@render inkdrop("output")}
    <div class="scrim"></div>
    <div class="wrap">
      <p class="kicker rv">03 &middot; Output</p>
      <h2 class="rv d1">FAST.<br /><em>SHARP.</em></h2>
      <p class="sub rv d2">High DPI. <b>Insane speed</b> for the quality.</p>
      <p class="sub rv d3">Starts <b>instantly.</b> Like all DOGS tech.</p>
    </div>
  </section>

  <!-- NATIVE -->
  <section class="panel" id="native" aria-label="No drivers, no apps">
    {@render inkdrop("native")}
    <div class="scrim"></div>
    <div class="wrap">
      <p class="kicker rv">04 &middot; Native</p>
      <h2 class="rv d1">NO DRIVERS.<br />NO <em>APPS.</em></h2>
      <p class="sub rv d2">Speaks the protocols <b>every device already has.</b></p>
      <p class="sub rv d3">Plug it in. <b>Print.</b></p>
    </div>
  </section>

  <!-- MACHINE -->
  <section class="panel" id="machine" aria-label="Silent models and colors">
    {@render inkdrop("machine")}
    <div class="scrim"></div>
    <div class="wrap">
      <p class="kicker rv">05 &middot; Machine</p>
      <h2 class="rv d1">SILENT.<br />ANY <em>COLOR.</em></h2>
      <p class="sub rv d2">Silent models. <b>Custom colors.</b></p>
      <p class="sub rv d3">A printer that looks like <b>it belongs to you.</b></p>
    </div>
  </section>

  <!-- FOOTER: badge only, zero copy, reveal-free -->
  <footer class="panel" aria-label="Made by DOGS">
    {@render inkdrop("foot")}
    <div class="wrap">
      <a class="badge" href="https://wearedogs.net" aria-label="Made by DOGS">
        <img src={badge} alt="Made by DOGS" />
      </a>
    </div>
  </footer>

</main>
