<template>
  <li>
    <input type="number" v-model="item.qte" min="0" :max="item.stock" /> /
    {{ item.stock }}
    <span>{{ item.name }} ({{ item.prix }}€ l'unité)</span>
    <span v-if="item.qte >= item.stock"> - Plus de stock</span>
  </li>
</template>

<script>
export default {
  props: ["item"],
};
</script>

<style></style>
