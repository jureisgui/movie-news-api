<template>

    <div class="news-container">
      <div class="thumbnail-container">
        <img :src="news_article.urlToImage" alt="" class="thumbnail">
      </div>
      <div class="text-container">
        <h2>{{ news_article.title }}</h2>
        <h3>{{ news_article.author }}</h3>
        <p>{{ news_article.description }}</p>
      </div>
    </div>
      
    </template>
  
    <style scoped>
    .news-container{
      border: 1px solid #f2f2f2;
      border-radius: 6px;
      padding: 0.3em 1.5em;
      margin: 1em;
      cursor: pointer;
      
      }
  
    .text-container{
      text-align: center; 
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
  </style>
  
    
  <script setup>  
    defineProps({
        news_article:{
        type: Object,
        required: true
        }
        });  
  </script>