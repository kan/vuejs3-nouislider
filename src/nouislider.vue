<template>
  <div ref="slider"></div>
</template>

<script>
import { ref, onMounted } from 'vue';
import NoUiSlider from "nouislider";

import "nouislider/dist/nouislider.min.css";

export default /*#__PURE__*/{
  name: 'Nouislider',
  props: {
    config: {
      type: Object,
      required: true,
    },
    modelValue: Array
  },
  emits: ['update:modelValue'],
  setup(props, { emit }) {
    const slider = ref(null);

    onMounted(() => {
      NoUiSlider.create(slider.value, props.config);
      slider.value.noUiSlider.on('change', (values) => {
        emit('update:modelValue', values);
      });
      emit('update:modelValue', slider.value.noUiSlider.get());
    });

    return { slider };
  }
};
</script>
