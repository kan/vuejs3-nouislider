<template>
  <div ref="slider"></div>
</template>

<script>
import { ref, computed, watch, onMounted } from 'vue';
import NoUiSlider from "nouislider";

import "nouislider/dist/nouislider.min.css";

export default /*#__PURE__*/{
  name: 'Nouislider',
  props: {
    options: {
      type: Object,
      required: true,
    },
    modelValue: Array
  },
  emits: ['update:modelValue'],
  setup(props, { emit }) {
    const slider = ref(null);

    onMounted(() => {
      NoUiSlider.create(slider.value, props.options);
      slider.value.noUiSlider.on('change', (values) => {
        emit('update:modelValue', values);
      });
      emit('update:modelValue', slider.value.noUiSlider.get());
    });

    watch(() => props.options, () => {
      slider.value.noUiSlider.updateOptions(props.options, true);
    }, { deep: true });

    const noUiSlider = computed(() => {
      return slider.value.noUiSlider;
    })

    return { slider, noUiSlider };
  }
};
</script>
