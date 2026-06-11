<script setup>
defineProps({
  items: { type: Array, required: true },
})
</script>

<template>
  <section id="portfolio" class="portfolio">
    <div class="container">
      <div class="section-label">VYBRANÉ PROJEKTY</div>
      <h2 class="section-title">PORTFOLIO</h2>
      <div class="portfolio-grid">
        <div v-for="item in items" :key="item.number" class="portfolio-item">
          <div class="portfolio-bg"></div>
          <div class="portfolio-content">
            <div class="portfolio-number">{{ item.number }}</div>
            <h3>
              <span v-for="(line, index) in item.title.split('\n')" :key="`${item.number}-${index}`">
                {{ line }}<br v-if="index < item.title.split('\n').length - 1" />
              </span>
            </h3>
            <p>{{ item.text }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
