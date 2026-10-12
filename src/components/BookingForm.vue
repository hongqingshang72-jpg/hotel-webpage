<script setup>
import { computed, ref } from 'vue'

const emit = defineEmits(['notify'])
const today = new Date()
const addDays = (date, days) => {
  const result = new Date(date)
  result.setDate(result.getDate() + days)
  return result
}
const formatDate = (date) => {
  const year = date.getFullYear()
  const month = String(date.getMonth() + 1).padStart(2, '0')
  const day = String(date.getDate()).padStart(2, '0')
  return `${year}-${month}-${day}`
}

const checkIn = ref(formatDate(addDays(today, 1)))
const checkOut = ref(formatDate(addDays(today, 2)))
const minDate = formatDate(today)
const minCheckOut = computed(() => formatDate(addDays(new Date(`${checkIn.value}T12:00:00`), 1)))
const destination = ref('浙江 · 莫干山')
const guests = ref('2 位成人')

function updateCheckIn() {
  if (checkOut.value <= checkIn.value) checkOut.value = minCheckOut.value
}

function searchRooms() {
  if (checkOut.value <= checkIn.value) {
    emit('notify', '退房日期需晚于入住日期')
    return
  }
  emit('notify', `正在为你查找 ${checkIn.value} 至 ${checkOut.value} 的可订房间`)
}
</script>

<template>
  <form id="booking" class="booking" @submit.prevent="searchRooms">
    <div class="field"><label for="destination">目的地</label><input id="destination" v-model="destination" aria-label="目的地" /></div>
    <div class="field"><label for="checkin">入住日期</label><input id="checkin" v-model="checkIn" type="date" :min="minDate" @change="updateCheckIn" /></div>
    <div class="field"><label for="checkout">退房日期</label><input id="checkout" v-model="checkOut" type="date" :min="minCheckOut" /></div>
    <div class="field">
      <label for="guests">入住人数</label>
      <select id="guests" v-model="guests">
        <option>2 位成人</option><option>1 位成人</option><option>2 位成人 · 1 位儿童</option><option>2 位成人 · 2 位儿童</option>
      </select>
    </div>
    <button class="search-btn" type="submit">查找房间　→</button>
  </form>
</template>
