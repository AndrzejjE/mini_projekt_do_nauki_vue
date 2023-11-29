<template>
  <div>
    <FilterComponent :items="data" @filterChange="handleFilterChange" />
    <div v-if="filteredItems.length === 0">
      Nic nie ma
    </div>
    <ul v-show="filteredItems.length > 0">
      <li v-for="item in filteredItems" :key="item.id" @click="handleItemClick(item)">{{item.id + " - " + item.name}}</li>
    </ul>
  </div>
</template>

<script>
import FilterComponent from "@/components/FilterComponent.vue";

export default {
  components: {
    FilterComponent,
  },
  data() {
    return {
      data: [
        {id:1 ,name: "PC1"},
        {id:2 ,name: "PC2"},
        {id:3 ,name: "Telefon1"},
        {id:4 ,name: "Inne"}],
      filter: "",
    };
  },
  computed: {
    filteredItems() {
      return this.data.filter((item) =>
          item.name.toLowerCase().includes(this.filter.toLowerCase())
      );
    },
  },
  methods: {
    handleFilterChange(newFilter) {
      this.filter = newFilter;
    },
    handleItemClick(item) {
      alert(`Kliknełeś na: ${item.name}`)
    },
    editItem(item) {
      // Tutaj możesz dodać kod do edycji elementu
      const newName = prompt("Podaj nową nazwę:", item.name);
      if (newName !== null) {
        item.name = newName;
      }
    },
  },
};
</script>
<style scoped>
div {
  text-align: left;
}


</style>
