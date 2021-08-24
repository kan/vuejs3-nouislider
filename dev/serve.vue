<template>
  <div id="app">
    <nouislider ref="slider" :options="options" v-model="value" />
    <div class="value">{{ value }}</div>
    <button @click="setPips()">Pips</button>
    <button @click="$refs.slider.noUiSlider.destroy()">Destroy</button>
  </div>
</template>

<style scoped>
.value {
  display: inline-block;
  margin: 50px 10px;
  padding: 5px;
  border: 1px solid gray;
}
</style>

<script>
import { ref } from 'vue';
import Nouislider from '@/nouislider.vue';

export default {
  name: 'ServeDev',
  components: {
    Nouislider
  },
  setup() {
    const options = ref({
      start: [20, 80],
      connect: true,
      range: {
        min: 0,
        max: 100,
      }
    });
    const value = ref([]);

    const setPips = () => {
      options.value.pips = {
        mode: 'range',
        density: 3,
      };
    };

    const slider = ref(null);

    return { options, value, setPips, slider };
  }
};
</script>
