<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'

const currentDate = ref(new Date())

// Форматированная дата
const formattedDate = computed(() => {
  return currentDate.value.toLocaleDateString('ru-RU', {
    day: 'numeric',
    month: 'long',
    year: 'numeric',
    weekday: 'long'
  })
})

// Форматированное время
const formattedTime = computed(() => {
  return currentDate.value.toLocaleTimeString('ru-RU')
})

// Обновляем время каждую секунду
let intervalId = null

onMounted(() => {
  intervalId = setInterval(() => {
    currentDate.value = new Date() // Изменяем ref - это триггерит обновление computed
  }, 1000)
})

onUnmounted(() => {
  if (intervalId) clearInterval(intervalId)
})
</script>

<template>
  <div class="block">
    <div class="header">Текущая дата и время:</div>
    <div class="data">Дата: {{ formattedDate }}</div>
    <div class="time">Время: {{ formattedTime }}</div>
  </div>
</template>

<style scoped>
.block {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  /* height: 100vh; */
  text-align: center;
}
.header {
  font-size: 4rem;
  font-weight: bold;
}

.data {
  font-size: 2rem;
  padding-top: 80px;
}

.time {
  font-size: 2rem;
  padding-top: 40px;
}

</style>