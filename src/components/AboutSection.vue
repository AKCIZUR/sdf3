<script setup>
defineProps({
  items: { type: Array, required: true },
})
</script>

<template>
  <section id="o-mne" class="about">
    <div class="container">
      <div class="section-label">FILOZOFIE</div>
      <h2 class="section-title">DESIGN JE O ŘEŠENÍ<br />PROBLÉMŮ PLYNULÉ INTERAKCE</h2>
      <div class="about-grid">
        <div v-for="item in items" :key="item.title" class="about-item">
          <div class="icon">
            <img :src="item.icon" :alt="item.alt" width="40" height="40" />
          </div>
          <h3>{{ item.title }}</h3>
          <p>{{ item.text }}</p>
        </div>
      </div>
    </div>
  </section>
</template>
