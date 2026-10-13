<script setup>
const columns = [
  [{ label: '客房与套房', href: '#stay' }, { label: '酒店体验', href: '#experience' }, { label: '逻辑手记', href: '#journal' }],
  [{ label: '联系我们', href: '#footer' }, { label: '常见问题', href: '#footer' }, { label: '隐私政策', href: '#footer' }],
]
</script>

<template>
  <footer class="footer" id="footer">
    <div class="footer-main">
      <div>
        <a class="brand" href="#top"><span class="brand-mark">逻</span><span><span class="footer-title">逻辑酒店</span><span class="brand-en">LOGIC HOTEL</span></span></a>
        <p class="footer-desc">在自然里，找到生活原本的样子。<br />浙江省湖州市德清县莫干山镇 · 逻辑度假酒店</p>
      </div>
      <div class="footer-links"><div v-for="(column, index) in columns" :key="index"><a v-for="link in column" :key="link.label" :href="link.href">{{ link.label }}</a></div></div>
    </div>
    <div class="footer-bottom"><span>© 2025 逻辑酒店 LOGIC HOTEL</span><span>浙ICP备 20250108 号</span></div>
  </footer>
</template>
