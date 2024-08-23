<script setup>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import Footer from './components/Footer.vue';
import { Icon } from '@iconify/vue';

</script>

<template>
  <div>
    <Header />

    <div class="welcome">
      <p>Welcome!</p>
      <p>Here you will find the latest news about the movies you want to watch.</p>
    </div>

    <h1>Search movie news</h1>
    <div class="search-section">
        <input type="text" class="search-input" v-model="search_query" placeholder="Enter movie topic">
        <span class="search-button" @click="news_fetch" :class="{noClick:!search_query.length}"><img class="search-icon" src="./assets/images/search.png" alt=""></span>
    </div>

    <h1>Filter news by genre</h1>

    <div class="genre-container">    
        <div class="genre" v-for="genres in movie_genres" @click="search_query=genres.genre;news_fetch();">
            <img :src="genres.img" alt="">
            <h3>{{genres.genre}}</h3>   
        </div>
    </div>

    <h1>Latest News</h1>
    <Main :news_articles_array='news_array' />

    <div class="back-to-top" v-show="showBackToTop" @click="scrollToTop">
      <Icon icon="material-symbols:arrow-circle-up-outline-rounded" class="back-to-top-icon" />
    </div>
    
    <Footer />
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Varela+Round&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Varela&display=swap');

.welcome{
    text-align: center;
    padding: 1em;
    padding-bottom: 0;
  }

.search-section{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;       
  }

.search-input{
    font-family: 'Varela', sans-serif;
    font-size: 16px;
    border-radius: 6px;
  }

.search-button{
    text-align: center;
    background-color: #8C0343;
    border-radius: 50%;
    max-width: 30px;
    max-height: 30px;
    cursor: pointer;
  }

.search-button:hover{
    transform: scale(1.1);
  }

.search-icon{
    max-width: 20px;
    max-height: 20px;
    padding: 0.3em;
  } 
  
.genre{
    border: 1px solid #f2f2f2;
    border-radius: 6px;
    padding: 0.3em 1em;
    margin: 0.5em;
    text-align: center;
    max-width: 70px;
    cursor: pointer;
  }

  .genre:hover{
    transform: scale(1.1);
  }

.genre-container{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    max-width: 400px;
    margin: 0.5em auto;
    text-align: center;
  }
    
.genre img{
    max-width: 50px;
  }

h3{
    margin: 0;
}  

.back-to-top-icon {
  font-size: 28px; 
}

.back-to-top {
  position: fixed;
  bottom: 100px;
  right: 10px;
  z-index: 999;
  background: #8C0343;
  color: #fff;
  border: none;
  padding: 10px;
  border-radius: 50%;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
}

.back-to-top:focus {
  outline: none;
}

.back-to-top:hover {
  background: #1D1A48;
}

@media screen and (min-width: 1000px) {
  .back-to-top {
    right: calc((100% - 1000px) / 2 + 30px);
  }
}

</style>

<script>
export default {
  components: {
		Icon,
	},
  data(){ //data start
    return{
      news_array:[],
      movie_genres:[
        {
          genre:"Horror",
          img:"https://i.ibb.co/FqSHDB4/horror.png"
        },
        {
          genre:"Sci-fi",
          img:"https://i.ibb.co/hMFTCrG/scifi.png"
        },
        {
          genre:"Fantasy",
          img:"https://i.ibb.co/Vt2Dssp/fantasy.png"
        },
        {
          genre:"Comedy",
          img:"https://i.ibb.co/pXWBm61/comedy.png"
        },
        {
          genre:"Drama",
          img:"https://i.ibb.co/CKD5G2R/drama.png"
        },
        {
          genre:"Adventure",
          img:"https://i.ibb.co/vkW6dTh/adventure.png"
        },
        {
          genre:"Action",
          img:"https://i.ibb.co/0Bc9YCQ/action.png"
        },
        {
          genre:"Mystery",
          img:"https://i.ibb.co/3hRdf2D/mystery.png"
        },
        {
          genre:"Historical",
          img:"https://i.ibb.co/dPWs3ds/historical.png"
        },
        {
          genre:"Animation",
          img:"https://i.ibb.co/6t2tM8X/animation.png"
        },
        {
          genre:"Romance",
          img:"https://i.ibb.co/p4943HT/romance.png"
        }    
      ],
      search_query:'',
      showBackToTop: false,        
  }   
}, //data end

  methods:{
    async news_fetch(){
      const searchWords = this.search_query.trim().split(' ');
      const query = searchWords.map((word) => `"${word}"`).join(' ');
      const response = await fetch(
        `https://newsapi.org/v2/everything?q=${query} movies&apiKey=4d85dee1eea24f48abac2151c9f4196a`
      );
      const received_news = await response.json();
      this.news_array = received_news.articles;
    },
    scrollToTop() {
      window.scrollTo({
        top: 0,
        behavior: 'smooth',
      });
    },
    handleScroll() {
      this.showBackToTop = window.scrollY > 500;
    }
  }, // methods end

  created(){
    this.news_fetch();
    window.addEventListener('scroll', this.handleScroll);    
  },
  // remove scroll event
  destroyed() {
    window.removeEventListener('scroll', this.handleScroll);
  },
}
</script>
