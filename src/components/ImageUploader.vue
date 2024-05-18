<template>
  <div>
    <image-input @submit-image="forwardImage"></image-input>
    <div>
      <h3>LIST</h3>
      <slot name="image-list"></slot>
    </div>
  </div>
</template>

<script>
import ImageInput from './ImageInput.vue';

export default {
  components: {
    ImageInput
  },
  methods: {
    forwardImage(image) {
      this.$emit('upload-image', image);
    }
  }
};
</script>
