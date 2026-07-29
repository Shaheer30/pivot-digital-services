<template>
  <svg
    class="hero-art"
    viewBox="0 0 520 480"
    fill="none"
    xmlns="http://www.w3.org/2000/svg"
    aria-hidden="true"
  >
    <!-- Bold geometric composition using logo colors -->
    <rect x="48" y="56" width="300" height="220" rx="18" fill="#1a1a1a" />
    <rect x="48" y="56" width="300" height="48" rx="18" fill="#4fa123" />
    <rect x="48" y="86" width="300" height="18" fill="#4fa123" />

    <circle cx="78" cy="80" r="5" fill="#f1590b" />
    <circle cx="96" cy="80" r="5" fill="#177acf" />
    <circle cx="114" cy="80" r="5" fill="#ffffff" opacity="0.85" />

    <rect x="76" y="132" width="120" height="14" rx="4" fill="#4fa123" opacity="0.95" />
    <rect x="76" y="158" width="180" height="8" rx="3" fill="#2d2d2d" />
    <rect x="76" y="176" width="150" height="8" rx="3" fill="#2d2d2d" />
    <rect x="76" y="210" width="88" height="34" rx="8" fill="#f3f5f4" />

    <rect x="250" y="132" width="74" height="112" rx="10" fill="#0c0c0c" />
    <circle cx="287" cy="168" r="16" fill="#177acf" />
    <path d="M270 210h34v18H270z" fill="#f1590b" />

    <!-- Overlapping card -->
    <g transform="translate(40 250)">
      <rect width="170" height="120" rx="16" fill="#f3f5f4" />
      <rect x="18" y="22" width="48" height="48" rx="10" fill="#4fa123" />
      <path d="M30 54l10-13 7 9 5-6 10 16H30z" fill="#ffffff" opacity="0.9" />
      <rect x="80" y="28" width="68" height="10" rx="3" fill="#0b1220" opacity="0.85" />
      <rect x="80" y="48" width="54" height="7" rx="2" fill="#5a6578" opacity="0.45" />
      <rect x="80" y="64" width="44" height="7" rx="2" fill="#5a6578" opacity="0.35" />
    </g>

    <!-- Accent ring -->
    <circle cx="390" cy="300" r="78" fill="#f1590b" />
    <circle cx="390" cy="300" r="52" fill="#0c0c0c" />
    <path
      d="M370 300h40M390 280v40"
      stroke="#4fa123"
      stroke-width="4"
      stroke-linecap="round"
    />

    <!-- Orbit lines -->
    <path
      d="M120 40c70-36 180-28 240 34"
      stroke="#177acf"
      stroke-width="1.5"
      stroke-dasharray="5 8"
      opacity="0.85"
    />
    <path
      d="M420 80c48 40 56 130 18 190"
      stroke="#4fa123"
      stroke-width="1.5"
      stroke-dasharray="5 8"
      opacity="0.7"
    />

    <circle cx="100" cy="48" r="5" fill="#177acf" />
    <circle cx="448" cy="140" r="6" fill="#f1590b" />
    <circle cx="280" cy="400" r="4" fill="#4fa123" />

    <!-- Small floating chip -->
    <rect x="320" y="56" width="110" height="44" rx="12" fill="#f3f5f4" />
    <circle cx="344" cy="78" r="10" fill="#177acf" />
    <rect x="362" y="70" width="48" height="7" rx="2" fill="#0b1220" opacity="0.8" />
    <rect x="362" y="84" width="34" height="5" rx="2" fill="#5a6578" opacity="0.4" />
  </svg>
</template>

<style scoped>
.hero-art {
  width: 100%;
  height: auto;
  display: block;
  max-width: 34rem;
}
</style>
