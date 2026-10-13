<script setup>
const rooms = [
  { name: '山景庭院套房', image: 'photo-1611892440504-42a792e24d32', alt: '山景套房温暖雅致的卧室', tag: '人气之选', details: '72㎡　·　独立庭院', guests: '2 人入住', price: '8,848', featured: true },
  { name: '林间大床房', image: 'photo-1618221195710-dd6b41faaea6', alt: '自然木色的客房空间', tag: '静谧私享', details: '48㎡　·　森林露台', guests: '2 人入住', price: '1,588' },
  { name: '云端家庭套房', image: 'photo-1600210492486-724fe5c67fb0', alt: '宽敞明亮的家庭套房', tag: '亲子友好', details: '96㎡　·　双卧室', guests: '4 人入住', price: '2,688' },
]
</script>

<template>
  <section class="section" id="stay">
    <div class="wrap">
      <div class="section-head">
        <div><div class="kicker">STAY WITH US</div><h2 class="section-title">为好好休息而设计</h2><p class="section-sub">每一间客房，都是与自然相处的一种方式。</p></div>
        <a class="text-link" href="#booking">查看全部房型　→</a>
      </div>
      <div class="room-grid">
        <article v-for="room in rooms" :key="room.name" class="room-card" :class="{ 'room-card-featured': room.featured }">
          <div class="room-photo"><img :src="`https://images.unsplash.com/${room.image}?auto=format&fit=crop&w=1000&q=85`" :alt="room.alt" /><span class="room-tag">{{ room.tag }}</span></div>
          <div class="room-info"><h3>{{ room.name }}</h3><div class="room-meta"><span>{{ room.details }}</span><span>{{ room.guests }}</span></div><div class="room-bottom"><div class="price">¥ {{ room.price }}<small>/ 晚起</small></div><a class="room-arrow" href="#booking" :aria-label="`预订${room.name}`">↗</a></div></div>
        </article>
      </div>
    </div>
  </section>
</template>
