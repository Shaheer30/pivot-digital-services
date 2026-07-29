<script setup lang="ts">
const year = new Date().getFullYear()
</script>

<template>
  <footer id="contact" class="footer">
    <div class="footer__inner container">
      <div class="footer__brand">
        <p class="footer__mark">Pivot</p>
        <p class="footer__tagline">Digital craft for brands ready to move forward.</p>
      </div>

      <nav class="footer__nav" aria-label="Footer">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/services">Services</RouterLink>
        <a href="mailto:hello@pivotdigitalservices.com">hello@pivotdigitalservices.com</a>
      </nav>

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

.footer__mark {
  font-family: var(--font-display);
  font-size: 1.6rem;
  font-weight: 700;
  letter-spacing: -0.03em;
  margin-bottom: var(--space-xs);
}

.footer__tagline {
  color: rgba(255, 255, 255, 0.65);
  max-width: 22rem;
  font-size: 0.95rem;
}

.footer__nav {
  display: flex;
  flex-direction: column;
  gap: var(--space-sm);
  font-size: 0.95rem;
}

.footer__nav a {
  color: rgba(255, 255, 255, 0.7);
  width: fit-content;
  transition: color 0.2s ease;
}

.footer__nav a:hover {
  color: #8fd6b8;
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

  .footer__nav {
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: flex-end;
    gap: var(--space-md);
  }

  .footer__copy {
    grid-column: 1 / -1;
  }
}
</style>
