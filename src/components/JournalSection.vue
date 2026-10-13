<script setup>
const articles = [
  { image: 'photo-1448375240586-882707db888b', alt: '山间竹林与晨雾', date: '2025.04.18　 ·　 山间漫游', title: '沿着晨雾，走进莫干山的春天', summary: '一条不赶时间的徒步路线，和山里刚刚好的风。' },
  { image: 'photo-1490645935967-10de6ba17061', alt: '以当季食材烹制的山野料理', date: '2025.03.26　 ·　 逻辑风味', title: '把四季端上餐桌的山野滋味', summary: '从附近田野到餐桌，让时令食材讲述这里的风土。' },
  { image: 'photo-1518837695005-2083093ee35b', alt: '海浪轻拍沙滩的宁静时刻', date: '2025.02.09　 ·　 慢下来', title: '留白，是旅行里最好的安排', summary: '不必去很多地方，只要在喜欢的地方多待一会儿。' },
]
</script>

<template>
  <section class="journal" id="journal">
    <div class="wrap">
      <div class="section-head"><div><div class="kicker">NOTES FROM LOGIC HOTEL</div><h2 class="section-title">逻辑手记</h2><p class="section-sub">关于山居、风物，和一些值得慢下来的日常。</p></div><a class="text-link" href="#journal">阅读更多　→</a></div>
      <div class="journal-grid">
        <article v-for="article in articles" :key="article.title" class="journal-card">
          <img :src="`https://images.unsplash.com/${article.image}?auto=format&fit=crop&w=800&q=80`" :alt="article.alt" />
          <div class="date">{{ article.date }}</div><h3>{{ article.title }}</h3><p>{{ article.summary }}</p>
        </article>
      </div>
    </div>
  </section>
</template>
