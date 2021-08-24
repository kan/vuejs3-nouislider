<template>
  <div id="app">
    <nouislider :config="config" v-model="value" />
    {{ value }}
  </div>
</template>

<script>
import { ref } from 'vue';
import Nouislider from '@/nouislider.vue';

export default {
  name: 'ServeDev',
  components: {
    Nouislider
  },
  setup() {
    const config = ref({
      start: [20, 80],
      connect: true,
      range: {
        min: 0,
        max: 100,
      }
    });
    const value = ref([]);

    return { config, value };
  }
};
</script>
