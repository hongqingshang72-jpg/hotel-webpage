<script setup>
import { ref } from 'vue'

defineEmits(['notify'])
const menuOpen = ref(false)
const links = [
  { label: '住在栖岸', href: '#stay' },
  { label: '酒店体验', href: '#experience' },
  { label: '栖岸手记', href: '#journal' },
  { label: '关于我们', href: '#footer' },
]

function closeMenu() {
  menuOpen.value = false
}

function scrollToBooking() {
  closeMenu()
  document.querySelector('#booking')?.scrollIntoView({ behavior: 'smooth' })
}
</script>

<template>
  <header class="nav">
    <a class="brand" href="#top" aria-label="栖岸酒店首页" @click="closeMenu">
      <span class="brand-mark">栖</span>
      <span><span class="brand-name">栖岸酒店</span><span class="brand-en">SHORELINE RETREAT</span></span>
    </a>
    <nav class="nav-links" :class="{ 'nav-links-open': menuOpen }" aria-label="主导航">
      <a v-for="link in links" :key="link.href" :href="link.href" @click="closeMenu">{{ link.label }}</a>
    </nav>
    <div class="nav-right">
      <a class="login" href="#" @click.prevent="$emit('notify', '会员中心即将为你开放，敬请期待')">会员登录</a>
      <button class="nav-cta" type="button" @click="scrollToBooking">预订房间</button>
      <button class="menu" type="button" :aria-expanded="menuOpen" aria-label="切换导航菜单" @click="menuOpen = !menuOpen">{{ menuOpen ? '×' : '☰' }}</button>
    </div>
  </header>
</template>
