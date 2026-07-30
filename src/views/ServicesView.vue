<script setup lang="ts">
import { ref } from 'vue'
import { useReveal } from '../composables/useReveal'
import ServiceIcon from '../components/ServiceIcon.vue'

const page = ref<HTMLElement | null>(null)
useReveal(page)

const contactEmail = 'pivotdigitalservices@gmail.com'
const contactPhone = '+92 346 7887225'
const contactPhoneHref = 'tel:+923467887225'

const activeId = ref<string | null>(null)

function setActive(id: string | null) {
  activeId.value = id
}

const services = [
  {
    id: 'dispatch',
    title: '24/7 Taxi & Limousine Dispatch Operations',
    icon: 'dispatch' as const,
    description:
      'Round-the-clock dispatch support that keeps your fleet responsive, organized, and ready for every trip.',
    points: [
      'Always-on dispatch coverage',
      'Aligned with your operating workflow',
      'Built for taxi and limousine fleets',
    ],
  },
  {
    id: 'support',
    title: 'Live Customer Support & Reservation Management',
    icon: 'support' as const,
    description:
      'Professional passenger support and booking handling that protects your reputation and revenue.',
    points: [
      'Live reservation management',
      'Fast, clear customer communication',
      'Fewer missed calls and booking gaps',
    ],
  },
  {
    id: 'website',
    title: 'Website Design & Development',
    icon: 'website' as const,
    description:
      'Modern, mobile-ready websites that help riders find you, trust you, and book with confidence.',
    points: [
      'Booking-focused site design',
      'Mobile-first experiences',
      'Ongoing updates and support',
    ],
  },
  {
    id: 'seo',
    title: 'Search Engine Optimization (SEO)',
    icon: 'seo' as const,
    description:
      'Local and industry-focused SEO so customers searching for rides can find your business first.',
    points: [
      'Local search visibility',
      'On-page and technical foundations',
      'Content that supports bookings',
    ],
  },
  {
    id: 'ppc',
    title: 'Google Ads (PPC) Campaign Management',
    icon: 'ppc' as const,
    description:
      'Paid search campaigns managed for transportation intent—turning searches into booked trips.',
    points: [
      'Campaign setup and optimization',
      'Budget-conscious targeting',
      'Performance tracking and reporting',
    ],
  },
  {
    id: 'social',
    title: 'Social Media Management',
    icon: 'social' as const,
    description:
      'Consistent social presence that keeps your brand visible and your service top of mind.',
    points: [
      'Content planning and posting',
      'Community engagement support',
      'Brand-aligned messaging',
    ],
  },
  {
    id: 'fleet',
    title: 'Driver & Fleet Coordination',
    icon: 'fleet' as const,
    description:
      'Coordination support that helps drivers, vehicles, and schedules stay aligned day to day.',
    points: [
      'Driver communication support',
      'Fleet scheduling assistance',
      'Operational continuity',
    ],
  },
  {
    id: 'admin',
    title: 'Administrative and Back-Office Support',
    icon: 'admin' as const,
    description:
      'Reliable back-office help so your team can stay focused on passengers and growth.',
    points: [
      'Day-to-day admin support',
      'Process documentation help',
      'Operational follow-through',
    ],
  },
  {
    id: 'process',
    title: 'Business Process Optimization',
    icon: 'process' as const,
    description:
      'Practical improvements to your workflows that reduce friction and improve efficiency.',
    points: [
      'Workflow review and refinement',
      'Clearer handoffs and ownership',
      'Efficiency without disruption',
    ],
  },
  {
    id: 'consulting',
    title: 'Technology & Operations Consulting',
    icon: 'consulting' as const,
    description:
      'Guidance on tools and operations so your technology supports—not slows—your business.',
    points: [
      'Ops and tech recommendations',
      'Implementation planning',
      'Long-term partnership support',
    ],
  },
]
</script>

<template>
  <div ref="page" class="services-page">
    <section class="services-hero">
      <div class="container services-hero__grid">
        <div class="services-hero__copy reveal">
          <p class="section__eyebrow">Services we provide</p>
          <h1 class="services-hero__title">Complete business support for transportation companies.</h1>
          <p class="section__lead">
            Whether you need a single service or a full operational solution, we deliver customized
            strategies that support efficiency, customer satisfaction, and sustainable growth.
          </p>
        </div>
        <div class="services-hero__art reveal" aria-hidden="true" style="transition-delay: 0.06s">
          <div class="services-hero__frame">
            <img
              class="services-hero__image"
              src="/hero-bg.jpeg"
              alt=""
              width="1200"
              height="1200"
            />
          </div>
        </div>
      </div>
    </section>

    <section class="services-list">
      <article
        v-for="service in services"
        :id="service.id"
        :key="service.id"
        class="service"
        :class="{ 'service--active': activeId === service.id }"
        @mouseenter="setActive(service.id)"
        @mouseleave="setActive(null)"
      >
        <div class="container service__inner">
          <div class="service__meta">
            <span class="service__icon">
              <ServiceIcon :name="service.icon" />
            </span>
          </div>
          <div class="service__body">
            <h2 class="service__title">{{ service.title }}</h2>
            <p class="service__desc">{{ service.description }}</p>
            <ul class="service__points">
              <li v-for="point in service.points" :key="point">{{ point }}</li>
            </ul>
            <a :href="`mailto:${contactEmail}`" class="service__cta">
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
            <h2 class="cta__title">Ready to strengthen your operations?</h2>
            <p class="cta__text">
              Reach out today and discover how our team can become a valuable extension of yours.
            </p>
            <div class="cta__contacts">
              <a :href="`mailto:${contactEmail}`">{{ contactEmail }}</a>
              <a :href="contactPhoneHref">{{ contactPhone }}</a>
            </div>
          </div>
          <a :href="`mailto:${contactEmail}`" class="btn btn--on-dark">
            Contact us
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
  font-size: clamp(2rem, 5vw, 3.1rem);
  max-width: 16ch;
  margin-bottom: var(--space-sm);
}

.services-hero__frame {
  background: var(--color-panel);
  border-radius: 1.25rem;
  overflow: hidden;
  aspect-ratio: 1;
  width: 100%;
}

.services-hero__image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  display: block;
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
  opacity: 1;
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
  color: var(--color-accent-light);
}

.service__title {
  font-size: clamp(1.35rem, 2.8vw, 1.85rem);
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
    radial-gradient(ellipse 60% 80% at 100% 0%, rgba(241, 89, 11, 0.35), transparent 55%),
    radial-gradient(ellipse 50% 60% at 0% 100%, rgba(23, 122, 207, 0.25), transparent 50%),
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

.cta__contacts {
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
  margin-top: var(--space-md);
}

.cta__contacts a {
  color: var(--color-accent-light);
  font-weight: 600;
  width: fit-content;
}

.cta__contacts a:hover {
  color: var(--color-white);
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

  .cta__contacts {
    flex-direction: row;
    gap: 1.5rem;
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
