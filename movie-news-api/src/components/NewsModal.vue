<template>
    <div class="modal-bg">
        <div class="news-container">
          <span class="close-button" @click="closeModal">x</span>
          <div class="thumbnail-container">
              <img :src="modal_prop.urlToImage" alt="" class="thumbnail">
          </div>
          <div class="text-container">
              <h2>{{ modal_prop.title }}</h2>
              <h3>Author: {{ modal_prop.author }}</h3>
              <h3>Date: {{ modal_prop.publishedAt }}</h3>
              <p>{{ modal_prop.content }}</p>
              <a :href="modal_prop.url" target="_blank">Visit source to read full article</a> 
          </div>
      </div>
    </div>    
</template>

<style scoped>

.modal-bg{
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 100;
}

.news-container{
  border: 1px solid #f2f2f2;
  border-radius: 6px;
  padding: 1.5em;
  margin: 1em;
  background-color: #1D1A48;
  position: relative;
  max-width: 900px;
}

.thumbnail-container{
  text-align: center;
  padding-top: 1em;
}

.thumbnail{
  width: 300px;
  object-fit: cover;
  border-radius: 6px;
  filter: drop-shadow(6px 0 6px #8C0343);
}

h2{
  text-decoration: underline;
}

a{
  color:#f2f2f2;
  font-family: 'Varela', sans-serif;
}

.close-button {
  position: absolute;
  top: 0.4rem;
  right: 0.3rem;
  background-color: #f2f2f238;
  border-radius: 50%;
  font-family: 'Varela', sans-serif;
  font-size: 1.5rem;
  width: 30px;
  height: 30px;
  color: #f2f2f2;
  cursor: pointer;
  padding: 0.1em;
  text-align: center;
  align-items: center;
}
</style>

<script setup>
import { ref } from 'vue';

const closeModal = () => {
  const modalVisible = ref(true);
  modalVisible.value = false;
};

  defineProps({
      modal_prop:{
      type: Object,
      required: true
      }
      });
</script>