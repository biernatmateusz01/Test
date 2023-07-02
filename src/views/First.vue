<template>
  <div class="container">
    <BaseNav />
    <form @submit.prevent>
      <div style="display: flex; gap: 4px">
        <div style="flex">
          <label>
            <div class="date">
              <span>Period</span
              ><span class="range"> <input type="date" /><span>-</span> <input type="date" /></span>
            </div>
          </label>
          <label>
            <div class="date">
              <span @click="filteredData">Category</span>
              <select v-model="selectOption">
                <option value="food">food</option>
                <option value="car">car</option>
              </select>
            </div>
          </label>
          <label>
            <div class="date">
              <span>Name</span>
              <input type="text" />
            </div>
          </label>
        </div>
      </div>
    </form>

    <ul class="expense__container">
      <CardItem v-for="item in paginatedItems" :key="item.id" :item="item" />
    </ul>
    <div class="pagination_container">
      <button @click="changePage(currentPage - 1)">previous page</button>
      <span>Page {{ currentPage }}</span>
      <button @click="changePage(currentPage + 1)">next page</button>
    </div>
  </div>
</template>

<script setup>
import BaseNav from '../components/BaseNav.vue'
import CardItem from '../components/CardItem.vue'
import { ref, computed } from 'vue'

const selectOption = ref('')

const items = [
  { id: 1, name: 'coffee', price: 40, category: 'food', date: '2022-07-16' },
  { id: 2, name: 'bread', price: 8, category: 'food', date: '2022-08-03' },
  { id: 3, name: 'cheese', price: 21, category: 'food', date: '2022-08-03' },
  { id: 4, name: 'fuel', price: 320, category: 'car', date: '2022-08-14' },
  { id: 5, name: 'bread', price: 8, category: 'food', date: '2022-09-01' },
  { id: 6, name: 'ham', price: 14, category: 'food', date: '2022-09-01' },
  { id: 7, name: 'butter', price: 6, category: 'food', date: '2022-09-10' },
  { id: 8, name: 'fuel', price: 320, category: 'car', date: '2022-09-10' },
  { id: 9, name: 'car wash', price: 60, category: 'car', date: '2022-09-10' }
]

const currentPage = ref(1)
const itemsPerPage = ref(5)

const paginatedItems = computed(() => {
  const startIndex = (currentPage.value - 1) * itemsPerPage.value
  const endIndex = startIndex + itemsPerPage.value
  return items.slice(startIndex, endIndex)
})

const totalPages = computed(() => {
  return Math.ceil(items.value.length / itemsPerPage.value)
})

const changePage = (pageNumber) => {
  currentPage.value = pageNumber
}
</script>

<style scoped>
li {
  list-style: none;
}
button {
  background: none;
  border: 1px solid #00ddc2;
  padding: 4px;
}
.date {
  display: flex;
  flex-direction: column;
}
input,
select {
  padding: 6px;
  border: 1px solid #00ddc2;
}
input:focus {
  outline: none;
}
.container {
  max-width: 1200px;
  display: block;
  margin: auto;
  padding: 16px;
}
.expense__container {
  display: grid;
  /* grid-template-rows: 1fr 1fr 1fr; */
  grid-template-columns: 1fr;
  padding: 10px;
  gap: 12px;
  padding: 48px 0;
}
.pagination_container {
  display: flex;
  gap: 12px;
  justify-content: center;
  align-items: center;
  width: 100%;
  color: #00ddc2;
}
.pagination_container > button {
  color: #00ddc2;
}

@media (min-width: 1000px) {
  .expense__container {
    grid-template-columns: 1fr 1fr;
  }
}
@media (min-width: 650px) {
  .expense__container {
    grid-template-columns: 1fr 1fr 1fr;
  }
}
</style>
