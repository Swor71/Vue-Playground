<template>
  <div id="app" class="container-fluid">
    <h3>{{title}}</h3>
    <div class="row">
      <Character 
        v-for="(id, index) in initial_ids"
        :id="id"
        :key="index"
      />
    </div>
  </div>
</template>

<script>
import Character from './components/Character.vue';

export default {
  name: 'app',
  data() {
    return {
      title: 'Generate the team',
      initial_ids: [1, 13, 14]
    };
  },
  components: {
    Character
  }
};
</script>

<style>
</style>
