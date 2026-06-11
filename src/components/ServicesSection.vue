<script setup>
defineProps({
  items: { type: Array, required: true },
})
</script>

<template>
  <section id="sluzby" class="services">
    <div class="container">
      <div class="section-label">CO NABÍZÍM</div>
      <h2 class="section-title">SLUŽBY</h2>
      <div class="services-list">
        <div v-for="item in items" :key="item.number" class="service-item">
          <div class="service-number">{{ item.number }}</div>
          <h3>{{ item.title }}</h3>
          <p>{{ item.text }}</p>
        </div>
      </div>
    </div>
  </section>
</template>
