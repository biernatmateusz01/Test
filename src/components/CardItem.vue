<template>
  <li class="expense__item">
    <div class="name"><span>name:</span>{{ item.name }}</div>
    <div class="price">
      <span class="price__amount"><span>price:</span>{{ item.price }} PLN</span>
    </div>
    <div class="category"><span>category:</span>{{ item.category }}</div>
    <div class="data"><span>date:</span>{{ item.date }}</div>
  </li>
</template>


<script setup>
import { defineProps } from 'vue'
defineProps({
    item: Object
})
</script>

<style scoped>

.expense__item {
  padding: 30px;
  background: white;
  color: #00ddc2;
  font-size: 16px;
  border: 1px solid #00ddc2;
  -webkit-box-shadow: -5px 3px 10px -6px rgba(0, 221, 194, 1);
  -moz-box-shadow: -5px 3px 10px -6px rgba(0, 221, 194, 1);
  box-shadow: -5px 3px 10px -6px rgba(0, 221, 194, 1);
  /* box-shadow: 0 10px 16px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19); */
}
.expense__item:hover {
  padding: 30px;
  background: #00ddc2;
  color: white;
  border: 1px solid white;

  /* box-shadow: 0 10px 16px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19); */
}
.data,
.name,
.price__amount,
.category {
  display: flex;
  justify-content: space-between;
}
</style>