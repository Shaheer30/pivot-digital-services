<script setup lang="ts">
import { ref } from 'vue'
import { useReveal } from '../composables/useReveal'
import HeroArt from '../components/HeroArt.vue'
import StudioMark from '../components/StudioMark.vue'
import WhyMark from '../components/WhyMark.vue'
import ServiceIcon from '../components/ServiceIcon.vue'

const page = ref<HTMLElement | null>(null)
useReveal(page)

const contactEmail = 'pivotdigitalservices@gmail.com'
const contactPhone = '+92 346 7887225'
const contactPhoneHref = 'tel:+923467887225'

const teasers = [
  {
    title: '24/7 Dispatch Operations',
    blurb: 'Round-the-clock taxi and limousine dispatch that keeps your fleet moving.',
    hash: 'dispatch',
    icon: 'mobile' as const,
  },
  {
    title: 'Live Customer Support',
    blurb: 'Reservation management and passenger support that protects your reputation.',
    hash: 'support',
    icon: 'uiux' as const,
  },
  {
    title: 'Website Design & Development',
    blurb: 'Professional sites built for bookings, trust, and mobile riders.',
    hash: 'website',
    icon: 'web' as const,
  },
  {
    title: 'SEO',
    blurb: 'Get found by local customers searching for rides in your market.',
    hash: 'seo',
    icon: 'seo' as const,
  },
  {
    title: 'Google Ads (PPC)',
    blurb: 'Targeted campaigns that turn search intent into booked trips.',
    hash: 'ppc',
    icon: 'commerce' as const,
  },
  {
    title: 'Fleet & Back-Office Support',
    blurb: 'Driver coordination, admin work, and process support behind the scenes.',
    hash: 'fleet',
    icon: 'brand' as const,
  },
]

const clients = [
  'Liberty Transit',
  'Two Way Limousine',
  'Fairfield Taxi',
  'Vacaville Taxi',
  'Vallejo Cabs',
  'MTM Transportation',
  '94 Cabs',
]
</script>

<template>
  <div ref="page" class="home">
    <section class="hero">
      <div class="hero__copy">
        <div class="hero__copy-inner">
          <img
            class="hero__brand"
            src="/pivot-logo.png?v=3"
            alt="Pivot Digital Services"
            width="420"
            height="168"
          />
          <h1 class="hero__headline">Operations and digital support for transportation companies.</h1>
          <p class="hero__support">
            We become an extension of your taxi, limousine, and transit business—so you can focus on
            growth while we run the operations behind the scenes.
          </p>
          <div class="hero__actions">
            <RouterLink to="/services" class="btn btn--primary">
              View services
              <span aria-hidden="true">→</span>
            </RouterLink>
            <a :href="`mailto:${contactEmail}`" class="btn btn--ghost">Contact us</a>
          </div>
        </div>
      </div>
      <div class="hero__panel" aria-hidden="true">
        <div class="hero__panel-glow" />
        <HeroArt />
      </div>
    </section>

    <section id="who-we-are" class="section intro">
      <div class="container intro__grid">
        <div class="reveal">
          <p class="section__eyebrow">Who we are</p>
          <h2 class="section__title">A trusted partner for transportation businesses.</h2>
          <div class="intro__mark">
            <StudioMark />
          </div>
        </div>
        <div class="reveal intro__copy" style="transition-delay: 0.08s">
          <p>
            Pivot Digital Services is a trusted operations and digital solutions partner for taxi,
            limousine, and transportation companies. We don’t simply provide services—we become an
            extension of your business.
          </p>
          <p>
            Whether it’s handling your dispatch operations, strengthening your online presence, or
            supporting your day-to-day administrative tasks, our goal is to help transportation
            businesses operate more efficiently while delivering an exceptional experience to their
            customers.
          </p>
          <p>
            Our approach is built on reliability, accountability, and long-term partnerships. Every
            solution we provide is designed around the unique needs of your business, allowing you
            to focus on growth while we take care of the operations behind the scenes.
          </p>
        </div>
      </div>
    </section>

    <section id="why-us" class="section why">
      <div class="container why__grid">
        <div class="reveal why__copy">
          <p>
            At Pivot Digital Services, we understand how the transportation industry works because we
            work with it every day. We know that every missed call, delayed dispatch, or outdated
            website can impact your reputation and revenue.
          </p>
          <p>
            That’s why we focus on delivering dependable support, fast communication, and solutions
            that keep your business running smoothly. We adapt to your workflow instead of forcing
            you to adapt to ours—providing personalized service, transparent communication, and a
            dedicated team that treats your business as its own.
          </p>
          <p>
            When you work with us, you gain a reliable partner committed to your long-term
            success—not just another service provider.
          </p>
        </div>
        <div class="reveal why__heading" style="transition-delay: 0.08s">
          <p class="section__eyebrow">Why choose us</p>
          <h2 class="section__title">Trust, consistency, and results—not just cost.</h2>
          <div class="why__mark">
            <WhyMark />
          </div>
        </div>
      </div>
    </section>

    <section class="section teasers">
      <div class="container">
        <div class="teasers__head reveal">
          <p class="section__eyebrow">Services we provide</p>
          <h2 class="section__title">Complete support built for transportation.</h2>
          <p class="section__lead">
            From dispatch to digital marketing—customized strategies for efficiency, customer
            satisfaction, and sustainable growth.
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
              <span class="teasers__text">
                <span class="teasers__title">{{ item.title }}</span>
                <span class="teasers__blurb">{{ item.blurb }}</span>
              </span>
              <span class="teasers__arrow" aria-hidden="true">→</span>
            </RouterLink>
          </li>
        </ul>

        <div class="teasers__more reveal">
          <RouterLink to="/services" class="btn btn--primary">
            See all services
            <span aria-hidden="true">→</span>
          </RouterLink>
        </div>
      </div>
    </section>

    <section id="clients" class="section clients">
      <div class="container">
        <div class="clients__head reveal">
          <p class="section__eyebrow">Our clients</p>
          <h2 class="section__title">Proud to support operators across North America.</h2>
          <p class="section__lead">
            Dependable operational and digital services for transportation companies that need a
            partner they can count on.
          </p>
        </div>
        <ul class="clients__list reveal">
          <li v-for="client in clients" :key="client" class="clients__item">{{ client }}</li>
        </ul>
      </div>
    </section>

    <section id="contact" class="section cta">
      <div class="container">
        <div class="cta__panel reveal">
          <div class="cta__text">
            <h2 class="cta__title">Let’s build a stronger transportation business together.</h2>
            <p>
              Improve dispatch, grow your online presence, or streamline daily workflow—we’re ready
              to help. Reach out and discover how our team can become a valuable extension of yours.
            </p>
            <div class="cta__contacts">
              <a :href="`mailto:${contactEmail}`">{{ contactEmail }}</a>
              <a :href="contactPhoneHref">{{ contactPhone }}</a>
            </div>
          </div>
          <a :href="`mailto:${contactEmail}`" class="btn btn--on-dark">
            Email us
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
    radial-gradient(ellipse 70% 55% at 70% 30%, rgba(79, 161, 35, 0.35), transparent 60%),
    radial-gradient(ellipse 40% 35% at 20% 80%, rgba(23, 122, 207, 0.2), transparent 50%),
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
  display: block;
  width: min(100%, 14rem);
  height: auto;
  margin-bottom: var(--space-md);
  border-radius: 0.65rem;
}

.hero__headline {
  font-size: clamp(1.45rem, 3vw, 2rem);
  font-weight: 700;
  max-width: 18ch;
  margin-bottom: var(--space-sm);
}

.hero__support {
  color: var(--color-ink-muted);
  max-width: 32rem;
  margin-bottom: var(--space-lg);
}

.hero__actions {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}

.intro,
.why {
  background: var(--color-bg);
}

.why {
  border-top: 1px solid var(--color-line);
}

.intro__grid,
.why__grid {
  display: grid;
  gap: var(--space-lg);
}

.why__heading {
  order: -1;
}

.intro__mark {
  margin-top: var(--space-md);
}

.why__mark {
  margin-top: var(--space-md);
}

.intro__copy,
.why__copy {
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

.teasers__more {
  margin-top: var(--space-lg);
}

.teasers__link {
  display: grid;
  grid-template-columns: auto 1fr auto;
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
  width: 3rem;
  height: 3rem;
  padding: 0.55rem;
  border-radius: 0.65rem;
  background: var(--color-panel);
  color: var(--color-accent-light);
}

.teasers__text {
  display: grid;
  gap: 0.2rem;
  min-width: 0;
}

.teasers__title {
  font-family: var(--font-display);
  font-size: 1.15rem;
  font-weight: 700;
  letter-spacing: -0.02em;
}

.teasers__blurb {
  font-size: 0.9rem;
  color: var(--color-ink-muted);
}

.teasers__arrow {
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

.clients {
  background: var(--color-bg);
}

.clients__head {
  margin-bottom: var(--space-lg);
}

.clients__list {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem 1rem;
}

.clients__item {
  font-family: var(--font-display);
  font-weight: 600;
  font-size: 1.05rem;
  letter-spacing: -0.02em;
  padding: 0.65rem 1rem;
  border-bottom: 2px solid var(--color-accent);
  color: var(--color-ink);
}

.cta__panel {
  display: flex;
  flex-direction: column;
  gap: var(--space-md);
  align-items: flex-start;
  padding: var(--space-xl) var(--space-md);
  border-radius: 1rem;
  background:
    radial-gradient(ellipse 60% 80% at 100% 0%, rgba(241, 89, 11, 0.35), transparent 55%),
    radial-gradient(ellipse 50% 60% at 0% 100%, rgba(23, 122, 207, 0.25), transparent 50%),
    linear-gradient(145deg, var(--color-panel-mid), var(--color-panel));
  color: var(--color-white);
}

.cta__title {
  font-size: clamp(1.75rem, 4vw, 2.4rem);
  margin-bottom: 0.5rem;
  max-width: 18ch;
}

.cta__text p {
  color: rgba(255, 255, 255, 0.72);
  max-width: 36rem;
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

  .hero__brand {
    width: min(100%, 16rem);
  }

  .hero__panel {
    padding: 2rem;
  }

  .intro__grid,
  .why__grid {
    grid-template-columns: 1fr 1fr;
    gap: var(--space-xl);
    align-items: start;
  }

  .why__heading {
    order: 0;
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

  .cta__contacts {
    flex-direction: row;
    gap: 1.5rem;
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
