<template>
  <sticky-header />
  <main>
    <hero-section></hero-section>
    <generic-section></generic-section>
    <about-section></about-section>
    <contact-section></contact-section>
    <color-palette></color-palette>
  </main>
  <footer>
    <p>Copyrights © Alpire 2021 | All rights reserved</p>
  </footer>
</template>

<script setup>
import StickyHeader from './components/StickyHeader.vue'
import HeroSection from './components/HeroSection.vue'
import GenericSection from './components/GenericSection.vue'
import ColorPalette from './components/ColorPalette.vue'
</script>