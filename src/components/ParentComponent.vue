<template>
  <div class="container">
    <div class="konten">
      <h1>Image Showcase</h1>
      <image-uploader @upload-image="addImage">
        <template v-slot:image-list>
          <ul>
            <li v-for="(image, index) in images" :key="index">
              <img :src="image.url" alt="Image Thumbnail" width="150">
              <div>
                <strong>{{ image.title }}</strong> - {{ image.description }}
              </div>
            </li>
          </ul>
        </template>
      </image-uploader>
    </div>
  </div>
  </template>
  
  <script>
  import ImageUploader from './ImageUploader.vue';
  
  export default {
    components: {
      ImageUploader
    },
    data() {
      return {
        images: [
          {
            title: 'Gunung Es',
            description: 'gunung ini terletak di La Plagne-Tarentaise, Francen dan foto ini diambil pada 29 mei 2022',
            url: 'https://images.unsplash.com/photo-1653832920174-1f333e009b62?q=80&w=2670&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
          },
          {
            title: 'Jepang',
            description: 'Foto ini saya ambil di Streets of Kurashiki, Japan. pada bulan oktober 2023.',
            url: 'https://images.unsplash.com/photo-1715608855578-94f1176cc417?q=80&w=2670&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
          }
        ]
      };
    },
    methods: {
      addImage(image) {
        this.images.push(image);
      }
    }
  };
  </script>
  
  <style>
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
  }
  
  img {
    margin-right: 10px;
  }
  </style>
  