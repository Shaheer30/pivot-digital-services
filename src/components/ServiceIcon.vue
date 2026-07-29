<script setup lang="ts">
defineProps<{
  name: 'web' | 'uiux' | 'brand' | 'seo' | 'mobile' | 'commerce'
}>()
</script>

<template>
  <svg
    class="icon"
    viewBox="0 0 48 48"
    fill="none"
    xmlns="http://www.w3.org/2000/svg"
    aria-hidden="true"
  >
    <!-- Web development -->
    <g v-if="name === 'web'">
      <rect x="6" y="10" width="36" height="26" rx="3" stroke="currentColor" stroke-width="1.75" />
      <path d="M6 18h36" stroke="currentColor" stroke-width="1.75" />
      <circle cx="11" cy="14" r="1.25" fill="currentColor" />
      <circle cx="15.5" cy="14" r="1.25" fill="currentColor" />
      <path
        d="M18 26l-4 4 4 4M30 26l4 4-4 4M26 24l-4 12"
        stroke="currentColor"
        stroke-width="1.75"
        stroke-linecap="round"
        stroke-linejoin="round"
      />
    </g>

    <!-- UI/UX -->
    <g v-else-if="name === 'uiux'">
      <rect x="8" y="8" width="20" height="32" rx="3" stroke="currentColor" stroke-width="1.75" />
      <rect x="12" y="14" width="12" height="8" rx="1.5" stroke="currentColor" stroke-width="1.5" />
      <path d="M12 28h12M12 32h8" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" />
      <circle cx="34" cy="18" r="8" stroke="currentColor" stroke-width="1.75" />
      <path
        d="M34 14v4l3 2"
        stroke="currentColor"
        stroke-width="1.5"
        stroke-linecap="round"
        stroke-linejoin="round"
      />
    </g>

    <!-- Branding -->
    <g v-else-if="name === 'brand'">
      <path
        d="M24 8l3.5 10.5H38l-8.5 6.5 3.5 10.5L24 29l-9 6.5 3.5-10.5L10 18.5h10.5L24 8z"
        stroke="currentColor"
        stroke-width="1.75"
        stroke-linejoin="round"
      />
      <circle cx="24" cy="22" r="3.5" stroke="currentColor" stroke-width="1.5" />
    </g>

    <!-- SEO -->
    <g v-else-if="name === 'seo'">
      <circle cx="20" cy="20" r="11" stroke="currentColor" stroke-width="1.75" />
      <path
        d="M28 28l10 10"
        stroke="currentColor"
        stroke-width="1.75"
        stroke-linecap="round"
      />
      <path
        d="M15 20h10M20 15v10"
        stroke="currentColor"
        stroke-width="1.5"
        stroke-linecap="round"
      />
    </g>

    <!-- Mobile -->
    <g v-else-if="name === 'mobile'">
      <rect x="14" y="6" width="20" height="36" rx="3.5" stroke="currentColor" stroke-width="1.75" />
      <path d="M20 10h8" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" />
      <circle cx="24" cy="36" r="1.75" fill="currentColor" />
      <path
        d="M19 18h10v10H19z"
        stroke="currentColor"
        stroke-width="1.5"
        stroke-linejoin="round"
      />
    </g>

    <!-- E-commerce -->
    <g v-else>
      <path
        d="M10 14h4l3.2 16h17.5l3-12H16"
        stroke="currentColor"
        stroke-width="1.75"
        stroke-linecap="round"
        stroke-linejoin="round"
      />
      <circle cx="20" cy="36" r="2.25" stroke="currentColor" stroke-width="1.5" />
      <circle cx="32" cy="36" r="2.25" stroke="currentColor" stroke-width="1.5" />
      <path
        d="M28 18v8M24 22h8"
        stroke="currentColor"
        stroke-width="1.5"
        stroke-linecap="round"
      />
    </g>
  </svg>
</template>

<style scoped>
.icon {
  width: 100%;
  height: 100%;
  display: block;
}
</style>
