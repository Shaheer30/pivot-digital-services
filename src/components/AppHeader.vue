<script setup lang="ts">
import { ref, watch, onMounted, onUnmounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const menuOpen = ref(false)
const scrolled = ref(false)
let scrollRaf = 0

watch(
  () => route.fullPath,
  () => {
    menuOpen.value = false
  },
)

watch(menuOpen, (open) => {
  document.body.classList.toggle('menu-open', open)
})

function toggleMenu() {
  menuOpen.value = !menuOpen.value
}

function onScroll() {
  if (scrollRaf) return
  scrollRaf = requestAnimationFrame(() => {
    scrolled.value = window.scrollY > 16
    scrollRaf = 0
  })
}

onMounted(() => {
  onScroll()
  window.addEventListener('scroll', onScroll, { passive: true })
})

onUnmounted(() => {
  window.removeEventListener('scroll', onScroll)
  cancelAnimationFrame(scrollRaf)
  document.body.classList.remove('menu-open')
})
</script>

<template>
  <header class="header" :class="{ 'header--open': menuOpen, 'header--scrolled': scrolled }">
    <div class="header__inner container">
      <RouterLink to="/" class="header__brand" aria-label="Pivot Digital Services home">
        <img
          class="header__logo"
          src="/pivot-logo.png?v=3"
          alt="Pivot Digital Services"
          width="160"
          height="64"
        />
      </RouterLink>

      <button
        class="header__toggle"
        type="button"
        :aria-expanded="menuOpen"
        aria-controls="site-nav"
        :aria-label="menuOpen ? 'Close menu' : 'Open menu'"
        @click="toggleMenu"
      >
        <span class="header__toggle-bar" />
        <span class="header__toggle-bar" />
      </button>

      <nav id="site-nav" class="header__nav" :class="{ 'header__nav--open': menuOpen }">
        <RouterLink
          to="/"
          class="header__link"
          active-class=""
          exact-active-class="header__link--active"
          >Home</RouterLink
        >
        <RouterLink to="/services" class="header__link" active-class="header__link--active"
          >Services</RouterLink
        >
        <a href="mailto:pivotdigitalservices@gmail.com" class="header__cta">
          Contact us
          <span aria-hidden="true">↗</span>
        </a>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.header {
  position: sticky;
  top: 0;
  z-index: 100;
  height: var(--header-height);
  background: rgba(243, 245, 244, 0.92);
  border-bottom: 1px solid transparent;
  transition:
    background 0.25s ease,
    border-color 0.25s ease;
}

.header--scrolled {
  background: rgba(255, 255, 255, 0.96);
  border-bottom-color: var(--color-line);
}

.header__inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 100%;
  gap: var(--space-md);
}

.header__brand {
  display: flex;
  align-items: center;
  z-index: 110;
  border-radius: 0.4rem;
  overflow: hidden;
  transition: opacity 0.2s ease;
}

.header__brand:hover {
  opacity: 0.9;
}

.header__logo {
  display: block;
  height: 3.25rem;
  width: auto;
  object-fit: contain;
}

.header__toggle {
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 6px;
  width: 2.75rem;
  height: 2.75rem;
  z-index: 110;
  border-radius: 0.4rem;
}

.header__toggle-bar {
  display: block;
  width: 1.2rem;
  height: 2px;
  background: var(--color-ink);
  margin-inline: auto;
  transition: transform 0.3s var(--ease-out);
}

.header--open .header__toggle-bar:first-child {
  transform: translateY(4px) rotate(45deg);
}

.header--open .header__toggle-bar:last-child {
  transform: translateY(-4px) rotate(-45deg);
}

.header__nav {
  display: none;
  align-items: center;
  gap: 1.5rem;
}

.header__nav--open {
  display: flex;
  flex-direction: column;
  position: fixed;
  inset: 0;
  padding: calc(var(--header-height) + 2rem) 1.5rem 2rem;
  background: var(--color-bg);
  gap: 0.5rem;
}

.header__link {
  font-size: 1.6rem;
  font-weight: 600;
  color: var(--color-ink-muted);
  padding-block: 0.5rem;
  transition: color 0.2s ease;
}

.header__link:hover,
.header__link--active {
  color: var(--color-ink);
}

.header__link--active {
  color: var(--color-accent);
}

.header__cta {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  margin-top: 1rem;
  padding: 0.85rem 1.25rem;
  font-size: 0.9rem;
  font-weight: 600;
  background: var(--color-accent);
  color: var(--color-white);
  border-radius: 0.35rem;
  width: fit-content;
  transition: background 0.2s ease;
}

.header__cta:hover {
  background: var(--color-accent-hover);
}

@media (min-width: 768px) {
  .header__toggle {
    display: none;
  }

  .header__nav {
    display: flex;
  }

  .header__nav--open {
    position: static;
    inset: auto;
    padding: 0;
    background: transparent;
    flex-direction: row;
    gap: 1.5rem;
  }

  .header__link {
    font-size: 0.925rem;
    padding-block: 0;
  }

  .header__cta {
    margin-top: 0;
    font-size: 0.8125rem;
    padding: 0.55rem 1rem;
  }
}
</style>
