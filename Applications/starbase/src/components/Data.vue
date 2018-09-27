<template>
  <div class="row">
    <Item 
      v-for="(item, index) in items"
      :key="index"
      :passed_item='item'
      :type='type'
    />
  </div>
</template>

<script>
import Item from './Item';

export default {
  data() {
    return {
      type: this.$route.params.type,
      items: []
    };
  },
  watch: {
    $route: 'fetchItems'
  },
  methods: {
    fetchItems() {
      this.items = [];
      this.type = this.$route.params.type;
      let initial_ids = [1, 5, 14];

      for (let i in initial_ids) {
        const id = initial_ids[i];

        const URL = `https://swapi.co/api/${this.type}/${id}/`;

        fetch(URL, { method: 'GET' })
          .then(response => response.json())
          .then(json => this.items.push(json));
      }
    }
  },
  created() {
    this.fetchItems();
  },
  components: {
    Item
  }
};
</script>

<style>
</style>
