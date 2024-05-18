<template>
  <div>
    <input v-model="title" type="text" placeholder="Image Title">
    <input v-model="description" type="text" placeholder="Image Description">
    <input type="file" @change="onFileChange">
    <button @click="submitImage">Submit Image</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: '',
      description: '',
      imageUrl: ''
    };
  },
  methods: {
    onFileChange(e) {
      const file = e.target.files[0];
      const reader = new FileReader();

      reader.onload = (event) => {
        this.imageUrl = event.target.result;
      };

      reader.readAsDataURL(file);
    },
    submitImage() {
      if (this.title && this.description && this.imageUrl) {
        const image = {
          title: this.title,
          description: this.description,
          url: this.imageUrl
        };
        this.$emit('submit-image', image);
        this.title = '';
        this.description = '';
        this.imageUrl = '';
      } else {
        alert('Choose Picture');
      }
    }
  }
};
</script>
