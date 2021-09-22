<template>
  <ul>
    <AchatItem v-for="item in items" :key="item.name" :item="item" />
  </ul>
</template>

<script>
export default {
  props: ["items"],
};
</script>

<style></style>
