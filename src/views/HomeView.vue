<script setup lang="ts">
import { ref } from 'vue'
import { useReveal } from '../composables/useReveal'
import HeroArt from '../components/HeroArt.vue'
import StudioMark from '../components/StudioMark.vue'
import ServiceIcon from '../components/ServiceIcon.vue'

const page = ref<HTMLElement | null>(null)
useReveal(page)

const teasers = [
  {
    title: 'Web development',
    blurb: 'Fast, reliable sites built to convert and scale.',
    hash: 'web-development',
    icon: 'web' as const,
  },
  {
    title: 'UI/UX design',
    blurb: 'Interfaces that feel effortless and look intentional.',
    hash: 'ui-ux-design',
    icon: 'uiux' as const,
  },
  {
    title: 'Branding & identity',
    blurb: 'Visual systems that make your brand unmistakable.',
    hash: 'branding-identity',
    icon: 'brand' as const,
  },
  {
    title: 'SEO & marketing',
    blurb: 'Visibility and campaigns that compound over time.',
    hash: 'seo-marketing',
    icon: 'seo' as const,
  },
  {
    title: 'Mobile apps',
    blurb: 'Native-feeling experiences for iOS and Android.',
    hash: 'mobile-apps',
    icon: 'mobile' as const,
  },
  {
    title: 'E-commerce',
    blurb: 'Stores designed for trust, clarity, and checkout.',
    hash: 'e-commerce',
    icon: 'commerce' as const,
  },
]
</script>

<template>
  <div ref="page" class="home">
    <section class="hero">
      <div class="hero__copy">
        <div class="hero__copy-inner">
          <p class="hero__brand">Pivot</p>
          <h1 class="hero__headline">Digital craft that moves brands forward.</h1>
          <p class="hero__support">
            We design, build, and grow digital experiences with quiet confidence and clear results.
          </p>
          <div class="hero__actions">
            <RouterLink to="/services" class="btn btn--primary">
              View services
              <span aria-hidden="true">→</span>
            </RouterLink>
            <a href="mailto:hello@pivotdigitalservices.com" class="btn btn--ghost">Get in touch</a>
          </div>
        </div>
      </div>
      <div class="hero__panel" aria-hidden="true">
        <div class="hero__panel-glow" />
        <HeroArt />
      </div>
    </section>

    <section id="intro" class="section intro">
      <div class="container intro__grid">
        <div class="reveal">
          <p class="section__eyebrow">Who we are</p>
          <h2 class="section__title">A studio for brands that care how they show up.</h2>
          <div class="intro__mark">
            <StudioMark />
          </div>
        </div>
        <div class="reveal intro__copy" style="transition-delay: 0.08s">
          <p>
            Pivot Digital Services partners with founders and teams who want work that feels refined—
            not loud. From first impression to everyday product moments, we shape the digital layer
            of your business with clarity and technical care.
          </p>
          <p>
            Whether you need a new site, a sharper identity, or a channel that actually grows, we
            bring strategy and craft into one focused collaboration.
          </p>
        </div>
      </div>
    </section>

    <section class="section teasers">
      <div class="container">
        <div class="teasers__head reveal">
          <p class="section__eyebrow">What we do</p>
          <h2 class="section__title">Six ways we help you pivot.</h2>
          <p class="section__lead">
            Explore our capabilities, then tell us where you want to go next.
          </p>
        </div>

        <ul class="teasers__grid">
          <li
            v-for="(item, index) in teasers"
            :key="item.title"
            class="teasers__item reveal"
            :style="{ transitionDelay: `${0.04 * index}s` }"
          >
            <RouterLink :to="`/services#${item.hash}`" class="teasers__link">
              <span class="teasers__icon">
                <ServiceIcon :name="item.icon" />
              </span>
              <span class="teasers__index">{{ String(index + 1).padStart(2, '0') }}</span>
              <span class="teasers__title">{{ item.title }}</span>
              <span class="teasers__blurb">{{ item.blurb }}</span>
              <span class="teasers__arrow" aria-hidden="true">→</span>
            </RouterLink>
          </li>
        </ul>
      </div>
    </section>

    <section class="section cta">
      <div class="container">
        <div class="cta__panel reveal">
          <div class="cta__text">
            <h2 class="cta__title">Ready when you are.</h2>
            <p>Share a bit about your project—we’ll reply with a clear next step.</p>
          </div>
          <a href="mailto:hello@pivotdigitalservices.com" class="btn btn--on-dark">
            hello@pivotdigitalservices.com
            <span aria-hidden="true">↗</span>
          </a>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.hero {
  display: grid;
  min-height: calc(100svh - var(--header-height));
}

.hero__copy {
  display: flex;
  align-items: center;
  background: var(--color-surface);
  padding: var(--space-xl) 1.25rem;
}

.hero__copy-inner {
  width: min(100%, 34rem);
  margin-inline: auto;
  animation: rise 0.65s var(--ease-out) both;
}

.hero__panel {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: var(--space-lg) 1.25rem var(--space-xl);
  background:
    radial-gradient(ellipse 70% 55% at 70% 30%, #1a4638, transparent 60%),
    linear-gradient(160deg, var(--color-panel-mid), var(--color-panel));
  overflow: hidden;
  animation: rise 0.65s var(--ease-out) 0.08s both;
}

.hero__panel-glow {
  position: absolute;
  width: 18rem;
  height: 18rem;
  border-radius: 50%;
  background: rgba(143, 214, 184, 0.12);
  top: 10%;
  right: 5%;
  pointer-events: none;
}

.hero__panel :deep(.hero-art) {
  position: relative;
  z-index: 1;
  width: min(100%, 28rem);
}

@keyframes rise {
  from {
    opacity: 0;
    transform: translateY(0.85rem);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.hero__brand {
  font-family: var(--font-display);
  font-size: clamp(3.5rem, 11vw, 6.5rem);
  font-weight: 800;
  letter-spacing: -0.045em;
  line-height: 0.9;
  margin-bottom: var(--space-md);
  color: var(--color-ink);
}

.hero__headline {
  font-size: clamp(1.45rem, 3vw, 2rem);
  font-weight: 700;
  max-width: 14ch;
  margin-bottom: var(--space-sm);
}

.hero__support {
  color: var(--color-ink-muted);
  max-width: 30rem;
  margin-bottom: var(--space-lg);
}

.hero__actions {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}

.intro {
  background: var(--color-bg);
}

.intro__grid {
  display: grid;
  gap: var(--space-lg);
}

.intro__mark {
  margin-top: var(--space-md);
}

.intro__copy {
  display: flex;
  flex-direction: column;
  gap: var(--space-md);
  color: var(--color-ink-muted);
  font-size: 1.05rem;
}

.teasers {
  background: var(--color-surface);
  border-block: 1px solid var(--color-line);
}

.teasers__head {
  margin-bottom: var(--space-lg);
}

.teasers__grid {
  display: grid;
  gap: 1rem;
}

.teasers__link {
  display: grid;
  grid-template-columns: auto 1fr auto;
  grid-template-areas:
    'icon index arrow'
    'icon title arrow'
    'icon blurb arrow';
  gap: 0.15rem 1rem;
  align-items: center;
  padding: 1.15rem 1.1rem;
  border: 1px solid var(--color-line);
  border-radius: 0.75rem;
  background: var(--color-bg);
  transition:
    border-color 0.25s ease,
    background 0.25s ease,
    transform 0.25s var(--ease-out);
}

.teasers__link:hover {
  border-color: var(--color-accent);
  background: var(--color-surface);
  transform: translateY(-2px);
}

.teasers__icon {
  grid-area: icon;
  width: 3rem;
  height: 3rem;
  padding: 0.55rem;
  border-radius: 0.65rem;
  background: var(--color-panel);
  color: #8fd6b8;
}

.teasers__index {
  grid-area: index;
  font-size: 0.7rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  color: var(--color-accent);
}

.teasers__title {
  grid-area: title;
  font-family: var(--font-display);
  font-size: 1.15rem;
  font-weight: 700;
  letter-spacing: -0.02em;
}

.teasers__blurb {
  grid-area: blurb;
  font-size: 0.9rem;
  color: var(--color-ink-muted);
}

.teasers__arrow {
  grid-area: arrow;
  font-size: 1.2rem;
  color: var(--color-ink-muted);
  transition:
    transform 0.25s var(--ease-out),
    color 0.25s ease;
}

.teasers__link:hover .teasers__arrow {
  transform: translateX(4px);
  color: var(--color-accent);
}

.cta__panel {
  display: flex;
  flex-direction: column;
  gap: var(--space-md);
  align-items: flex-start;
  padding: var(--space-xl) var(--space-md);
  border-radius: 1rem;
  background:
    radial-gradient(ellipse 60% 80% at 100% 0%, #1a4638, transparent 55%),
    linear-gradient(145deg, var(--color-panel-mid), var(--color-panel));
  color: var(--color-white);
}

.cta__title {
  font-size: clamp(1.75rem, 4vw, 2.6rem);
  margin-bottom: 0.5rem;
}

.cta__text p {
  color: rgba(255, 255, 255, 0.72);
  max-width: 28rem;
}

@media (min-width: 900px) {
  .hero {
    grid-template-columns: 1.05fr 0.95fr;
  }

  .hero__copy {
    padding: var(--space-2xl) 2rem var(--space-2xl) max(2rem, calc((100vw - var(--max-width)) / 2));
  }

  .hero__copy-inner {
    margin-inline: 0;
    margin-left: auto;
    padding-right: 2rem;
    width: min(100%, 36rem);
  }

  .hero__panel {
    padding: 2rem;
  }

  .intro__grid {
    grid-template-columns: 1fr 1fr;
    gap: var(--space-xl);
    align-items: start;
  }

  .teasers__grid {
    grid-template-columns: 1fr 1fr;
  }

  .cta__panel {
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    padding: 3rem;
  }
}

@media (prefers-reduced-motion: reduce) {
  .hero__copy-inner,
  .hero__panel {
    animation: none;
  }

  .teasers__link:hover {
    transform: none;
  }
}
</style>
