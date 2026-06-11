<script setup>
import { onMounted, nextTick, ref, watch } from 'vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

import SiteNav from './components/SiteNav.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import ServicesSection from './components/ServicesSection.vue'
import PortfolioSection from './components/PortfolioSection.vue'
import ContactSection from './components/ContactSection.vue'
import SiteFooter from './components/SiteFooter.vue'

import { navLinks, aboutItems, services, portfolioItems } from './content/siteContent.js'

gsap.registerPlugin(ScrollTrigger)

const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}

watch(isMenuOpen, (value) => {
  document.body.classList.toggle('menu-open', value)
})

onMounted(async () => {
  await nextTick()

  gsap.to('.hero h1', {
    opacity: 1,
    x: 0,
    duration: 1,
    delay: 0.3,
  })

  gsap.to('.hero-number', {
    opacity: 0.1,
    x: 4,
    duration: 10,
    delay: 0.4,
  })

  gsap.to('.hero p', {
    opacity: 1,
    y: 0,
    duration: 1.8,
    delay: 0.5,
  })

  gsap.to('.cta-buttons', {
    opacity: 1,
    y: 0,
    duration: 0.8,
    delay: 2,
  })

  gsap.utils.toArray('.about-item').forEach((item, i) => {
    gsap.to(item, {
      scrollTrigger: {
        trigger: item,
        start: 'top 80%',
        toggleActions: 'play none none reverse',
      },
      opacity: 1,
      y: 0,
      duration: 0.8,
      delay: i * 0.1,
    })
  })

  gsap.utils.toArray('.service-item').forEach((item, i) => {
    gsap.to(item, {
      scrollTrigger: {
        trigger: item,
        start: 'top 80%',
        toggleActions: 'play none none reverse',
      },
      opacity: 1,
      x: 0,
      duration: 0.8,
      delay: i * 0.1,
    })
  })

  gsap.utils.toArray('.portfolio-item').forEach((item, i) => {
    gsap.to(item, {
      scrollTrigger: {
        trigger: item,
        start: 'top 80%',
        toggleActions: 'play none none reverse',
      },
      opacity: 1,
      scale: 1,
      duration: 0.8,
      delay: i * 0.1,
    })
  })

  gsap.to('.contact-email', {
    scrollTrigger: {
      trigger: '.contact-email',
      start: 'top 80%',
      toggleActions: 'play none none reverse',
    },
    opacity: 1,
    y: 0,
    duration: 0.8,
  })
})
</script>

<template>
  <SiteNav
    :links="navLinks"
    :is-open="isMenuOpen"
    @toggle-menu="toggleMenu"
    @navigate="closeMenu"
  />
  <HeroSection />
  <AboutSection :items="aboutItems" />
  <ServicesSection :items="services" />
  <PortfolioSection :items="portfolioItems" />
  <ContactSection />
  <SiteFooter />
</template>
