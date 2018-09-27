<template>
  <div class="col-md-4" @click="switchItem">
    <div class="item-card">
      <div class="card-block p-3">
        <h4 class="card-title">{{item.name}}</h4>
        <div v-for="(value, key, index) in item" :key="index">
          <div v-if="index < 5">
            <strong>{{key}}</strong>: {{value}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      item: {}
    };
  },
  props: ['passed_item', 'type'],
  methods: {
    switchItem(type) {
      const random_id = Math.floor(Math.random() * 63) + 1;
      const URL = `https://swapi.co/api/${this.type}/${random_id}/`;
      fetch(URL, { method: 'GET' })
        .then(res => res.json())
        .then(json => (this.item = json));
    }
  },
  created() {
    this.item = this.passed_item;
  }
};
</script>
