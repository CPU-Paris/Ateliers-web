<template>
  <ul>
    <li v-for="item of items" :key="item.name">
        <input type="number" v-model="item.qte" min="0" :max="item.stock"> / {{item.stock}}
        <span>{{item.name}} ({{item.prix}}€ l'unité)</span>
        <span v-if="item.qte >= item.stock"> - Plus de stock</span>
    </li>
  </ul>
</template>

<script>
export default {
    props: ["items"]
}
</script>

<style>

</style>