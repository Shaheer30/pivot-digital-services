<script setup lang="ts">
import { ref } from 'vue'
import { useReveal } from '../composables/useReveal'
import ServiceIcon from '../components/ServiceIcon.vue'
import HeroArt from '../components/HeroArt.vue'

const page = ref<HTMLElement | null>(null)
useReveal(page)

const activeId = ref<string | null>(null)

function setActive(id: string | null) {
  activeId.value = id
}

const services = [
  {
    id: 'web-development',
    title: 'Web development',
    icon: 'web' as const,
    description:
      'Custom websites and web applications built for speed, accessibility, and long-term maintainability.',
    points: [
      'Marketing sites and product platforms',
      'Responsive, performant front ends',
      'Integrations, CMS, and ongoing support',
    ],
  },
  {
    id: 'ui-ux-design',
    title: 'UI/UX design',
    icon: 'uiux' as const,
    description:
      'Research-led interfaces that reduce friction and elevate how your product feels day to day.',
    points: [
      'User flows, wireframes, and prototypes',
      'Design systems and component libraries',
      'Usability reviews and iterative polish',
    ],
  },
  {
    id: 'branding-identity',
    title: 'Branding & identity',
    icon: 'brand' as const,
    description:
      'Cohesive visual identity that holds up across screens, touchpoints, and growth stages.',
    points: [
      'Logo and visual language',
      'Typography, color, and brand guidelines',
      'Digital brand applications',
    ],
  },
  {
    id: 'seo-marketing',
    title: 'SEO / digital marketing',
    icon: 'seo' as const,
    description:
      'Search and content strategies that help the right people find you—and stay engaged.',
    points: [
      'Technical and on-page SEO foundations',
      'Content planning and landing pages',
      'Campaign support and performance tracking',
    ],
  },
  {
    id: 'mobile-apps',
    title: 'Mobile apps',
    icon: 'mobile' as const,
    description:
      'Focused mobile experiences that feel native, reliable, and aligned with your brand.',
    points: [
      'iOS and Android product design',
      'Cross-platform development',
      'Launch support and iteration',
    ],
  },
  {
    id: 'e-commerce',
    title: 'E-commerce',
    icon: 'commerce' as const,
    description:
      'Online stores shaped for clarity, trust, and conversion—from catalog to checkout.',
    points: [
      'Storefront design and UX',
      'Shopify and custom commerce builds',
      'Optimization for mobile checkout',
    ],
  },
]
</script>

<template>
  <div ref="page" class="services-page">
    <section class="services-hero">
      <div class="container services-hero__grid">
        <div class="services-hero__copy reveal">
          <p class="section__eyebrow">Services</p>
          <h1 class="services-hero__title">Everything you need to show up well online.</h1>
          <p class="section__lead">
            Six focused offerings—delivered with the same calm craft, whether you need one piece or
            the full stack.
          </p>
        </div>
        <div class="services-hero__art reveal" aria-hidden="true" style="transition-delay: 0.06s">
          <div class="services-hero__frame">
            <HeroArt />
          </div>
        </div>
      </div>
    </section>

    <section class="services-list">
      <article
        v-for="(service, index) in services"
        :id="service.id"
        :key="service.id"
        class="service reveal"
        :class="{ 'service--active': activeId === service.id }"
        :style="{ transitionDelay: `${0.03 * index}s` }"
        @mouseenter="setActive(service.id)"
        @mouseleave="setActive(null)"
      >
        <div class="container service__inner">
          <div class="service__meta">
            <span class="service__icon">
              <ServiceIcon :name="service.icon" />
            </span>
            <span class="service__index">{{ String(index + 1).padStart(2, '0') }}</span>
          </div>
          <div class="service__body">
            <h2 class="service__title">{{ service.title }}</h2>
            <p class="service__desc">{{ service.description }}</p>
            <ul class="service__points">
              <li v-for="point in service.points" :key="point">{{ point }}</li>
            </ul>
            <a href="mailto:hello@pivotdigitalservices.com" class="service__cta">
              Discuss this service
              <span aria-hidden="true">↗</span>
            </a>
          </div>
        </div>
      </article>
    </section>

    <section class="section cta">
      <div class="container">
        <div class="cta__panel reveal">
          <div>
            <h2 class="cta__title">Let’s talk about your next move.</h2>
            <p class="cta__text">
              Tell us what you’re building—we’ll help you map the smartest path forward.
            </p>
          </div>
          <a href="mailto:hello@pivotdigitalservices.com" class="btn btn--on-dark">
            Get in touch
            <span aria-hidden="true">↗</span>
          </a>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.services-hero {
  padding-block: var(--space-xl) var(--space-lg);
  background: var(--color-surface);
  border-bottom: 1px solid var(--color-line);
}

.services-hero__grid {
  display: grid;
  gap: var(--space-lg);
  align-items: center;
}

.services-hero__title {
  font-size: clamp(2.1rem, 5vw, 3.4rem);
  max-width: 14ch;
  margin-bottom: var(--space-sm);
}

.services-hero__frame {
  background: linear-gradient(160deg, var(--color-panel-mid), var(--color-panel));
  border-radius: 1.25rem;
  padding: 1.25rem;
}

.services-hero__art {
  width: min(100%, 24rem);
  justify-self: center;
}

.service {
  padding-block: var(--space-lg);
  border-bottom: 1px solid var(--color-line);
  scroll-margin-top: calc(var(--header-height) + 1rem);
  background: var(--color-bg);
  transition: background 0.25s ease;
}

.service--active {
  background: var(--color-surface);
}

.service__inner {
  display: grid;
  gap: var(--space-md);
}

.service__meta {
  display: flex;
  align-items: center;
  gap: 0.85rem;
}

.service__icon {
  width: 3.25rem;
  height: 3.25rem;
  padding: 0.6rem;
  border-radius: 0.75rem;
  background: var(--color-panel);
  color: #8fd6b8;
}

.service__index {
  font-size: 0.75rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  color: var(--color-accent);
}

.service__title {
  font-size: clamp(1.45rem, 3vw, 1.95rem);
  margin-bottom: var(--space-xs);
}

.service--active .service__title {
  color: var(--color-accent);
}

.service__desc {
  color: var(--color-ink-muted);
  max-width: 36rem;
  margin-bottom: var(--space-md);
}

.service__points {
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
  margin-bottom: var(--space-md);
}

.service__points li {
  position: relative;
  padding-left: 1rem;
  font-size: 0.975rem;
}

.service__points li::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0.65em;
  width: 0.45rem;
  height: 2px;
  background: var(--color-accent);
}

.service__cta {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  font-size: 0.875rem;
  font-weight: 600;
  color: var(--color-accent);
}

.service__cta span {
  transition: transform 0.25s var(--ease-out);
}

.service__cta:hover span {
  transform: translate(2px, -2px);
}

.cta__panel {
  display: flex;
  flex-direction: column;
  gap: var(--space-md);
  padding: var(--space-xl) var(--space-md);
  border-radius: 1rem;
  background:
    radial-gradient(ellipse 60% 80% at 100% 0%, #1a4638, transparent 55%),
    linear-gradient(145deg, var(--color-panel-mid), var(--color-panel));
  color: var(--color-white);
}

.cta__title {
  font-size: clamp(1.75rem, 4vw, 2.5rem);
  margin-bottom: 0.5rem;
}

.cta__text {
  color: rgba(255, 255, 255, 0.72);
  max-width: 30rem;
}

@media (min-width: 768px) {
  .service__inner {
    grid-template-columns: 5.5rem 1fr;
    gap: var(--space-lg);
  }

  .service {
    padding-block: var(--space-xl);
  }

  .service__meta {
    flex-direction: column;
    align-items: flex-start;
  }

  .service__points {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 0.85rem;
  }
}

@media (min-width: 900px) {
  .services-hero__grid {
    grid-template-columns: 1.15fr 0.85fr;
    gap: var(--space-xl);
  }

  .services-hero__art {
    width: 100%;
    max-width: 28rem;
    justify-self: end;
  }

  .cta__panel {
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    padding: 3rem;
  }
}

@media (min-width: 1024px) {
  .services-list {
    display: grid;
    grid-template-columns: 1fr 1fr;
  }

  .service {
    border-right: 1px solid var(--color-line);
  }

  .service:nth-child(2n) {
    border-right: none;
  }

  .service__points {
    grid-template-columns: 1fr;
  }
}
</style>
