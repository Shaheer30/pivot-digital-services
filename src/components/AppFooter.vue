<script setup lang="ts">
const year = new Date().getFullYear()
const contactEmail = 'pivotdigitalservices@gmail.com'
const contactPhone = '+92 346 7887225'
const contactPhoneHref = 'tel:+923467887225'
</script>

<template>
  <footer class="footer">
    <div class="footer__inner container">
      <div class="footer__brand">
        <img
          class="footer__logo"
          src="/pivot-logo.png?v=3"
          alt="Pivot Digital Services"
          width="200"
          height="80"
        />
        <p class="footer__tagline">
          Operations and digital support for taxi, limousine, and transportation companies.
        </p>
      </div>

      <div class="footer__meta">
        <nav class="footer__nav" aria-label="Footer">
          <RouterLink to="/">Home</RouterLink>
          <RouterLink to="/services">Services</RouterLink>
        </nav>
        <div class="footer__contact">
          <a :href="`mailto:${contactEmail}`">{{ contactEmail }}</a>
          <a :href="contactPhoneHref">{{ contactPhone }}</a>
        </div>
      </div>

      <p class="footer__copy">&copy; {{ year }} Pivot Digital Services</p>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  border-top: 1px solid var(--color-line);
  background: var(--color-panel);
  color: var(--color-white);
  padding-block: var(--space-xl);
}

.footer__inner {
  display: grid;
  gap: var(--space-lg);
}

.footer__logo {
  display: block;
  height: 3.5rem;
  width: auto;
  margin-bottom: var(--space-sm);
  border-radius: 0.4rem;
}

.footer__tagline {
  color: rgba(255, 255, 255, 0.65);
  max-width: 26rem;
  font-size: 0.95rem;
}

.footer__meta {
  display: flex;
  flex-direction: column;
  gap: var(--space-md);
}

.footer__nav,
.footer__contact {
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
  font-size: 0.95rem;
}

.footer__nav a,
.footer__contact a {
  color: rgba(255, 255, 255, 0.7);
  width: fit-content;
  transition: color 0.2s ease;
}

.footer__nav a:hover,
.footer__contact a:hover {
  color: var(--color-accent-light);
}

.footer__copy {
  font-size: 0.8125rem;
  color: rgba(255, 255, 255, 0.45);
  padding-top: var(--space-sm);
  border-top: 1px solid rgba(255, 255, 255, 0.12);
}

@media (min-width: 768px) {
  .footer__inner {
    grid-template-columns: 1.4fr 1fr;
  }

  .footer__meta {
    align-items: flex-end;
    text-align: right;
  }

  .footer__nav {
    flex-direction: row;
    gap: var(--space-md);
    justify-content: flex-end;
  }

  .footer__contact {
    align-items: flex-end;
    padding-top: var(--space-xs);
    border-top: 1px solid rgba(255, 255, 255, 0.12);
  }

  .footer__copy {
    grid-column: 1 / -1;
  }
}
</style>
