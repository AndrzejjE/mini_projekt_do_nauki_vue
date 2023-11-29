<template>
  <div>
    <h2>Filtr:</h2>
    <input v-model="filter" />
  </div>
</template>

<script>
export default {
  props: { items: Array },
  data() {
    return { filter: '' };
  },
  watch: {
    filter(newFilter) {
      this.$emit('filterChange', newFilter);
    },
  },
};
</script>
<style scoped>

</style>