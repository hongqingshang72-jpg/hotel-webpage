<script setup>
import { ref } from 'vue'
import SiteHeader from './components/SiteHeader.vue'
import BookingForm from './components/BookingForm.vue'
import RoomsSection from './components/RoomsSection.vue'
import ExperienceSection from './components/ExperienceSection.vue'
import JournalSection from './components/JournalSection.vue'
import SiteFooter from './components/SiteFooter.vue'

const toastMessage = ref('')
let toastTimer

function showToast(message) {
  toastMessage.value = message
  window.clearTimeout(toastTimer)
  toastTimer = window.setTimeout(() => {
    toastMessage.value = ''
  }, 2800)
}
</script>

<template>
  <div class="topbar">山海之间，留一晚给自己 <span>· 会员预订享专属礼遇</span></div>
  <SiteHeader @notify="showToast" />

  <main id="top">
    <section class="hero" aria-label="栖岸酒店海景">
      <img class="hero-img" src="https://images.unsplash.com/photo-1470770841072-f978cf4d019e?auto=format&fit=crop&w=2200&q=88" alt="湖畔山间的静谧度假风景" />
      <div class="hero-content">
        <div class="eyebrow">A SLOWER KIND OF LUXURY</div>
        <h1>把日子住成<br />风景</h1>
        <p>面朝山海，住进从容的每一刻。</p>
        <a class="hero-link" href="#experience">探索栖岸 <b>→</b></a>
      </div>
      <div class="hero-count"><strong>01</strong><span>/</span>03</div>
    </section>

    <BookingForm @notify="showToast" />
    <RoomsSection />
    <ExperienceSection />
    <JournalSection />
  </main>

  <SiteFooter />
  <Transition name="toast">
    <div v-if="toastMessage" class="toast" role="status" aria-live="polite">{{ toastMessage }}</div>
  </Transition>
</template>
