<template>
  <div class="home">
  <div class="top-bar">
      <form @submit.prevent="SearchMovies()" class="search-box">
      <input type="text" placeholder="what are you looking for?" v-model="search"/>
      <input type="submit" value="Search"/>
      </form>
      <div class="review-content">
      <button class="review">
       <i class="fa fa-save" aria-hidden="true"></i> </button>
       <button class="review">
       <i class="fa fa-heart" aria-hidden="true"></i></button>
       <button class="review">
       <i class="fa fa-star" aria-hidden="true"></i></button>
      </div>
      </div>
    <div class="feature-card">
      <router-link to="/movie/tt0409591‏">
      <img src="https://images.unsplash.com/photo-1513384312027-9fa69a360337?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=751&q=80‏" alt="" class="feature-img" />
       <div class="detail">
         </div>
       </router-link>
      </div> 

      <div class="movies-list">
        <div class="movie" v-for="movie in movies" :key="movie.imdbID">
         <router-link :to="'/movie/' + movie.imdbID" class="movie-link">
        <div class="product-image">
          <img :src="movie.Poster" alt="Movie Poster" />
          <div class="type">{{movie.Type }}</div>
        </div>
        <div class="detail">
         <p class="year">{{ movie.Year }}</p> 
        <h3>{{ movie.Title }}</h3>
        </div>
        </router-link>
        </div>
      </div>
  </div>
</template>

<script>
import { onMounted, ref } from 'vue';
import env from '@/env.js';
export default {
  setup () {
const search=ref("The Lego Batman");
const movies=ref([]);
const SearchMovies= () => {
  if(search.value !=""){
    fetch(`http://www.omdbapi.com/?&apikey=${env.apikey}&s=${search.value}`)
    .then(response => response.json())
    .then(data =>{
movies.value=data.Search;
search.value="";
console.log(movies.value);
    });
  }
}
onMounted(() =>{
  SearchMovies();
});
return {
  search,
  movies,
  SearchMovies
}
  }
}
</script>
<style lang="scss">
.home {
  background-color: rgb(65, 92, 65);
   border-radius: 50px;
   font-family: 'Fira Sans', sans-serif;


   .movies-list {
    display: flex;
    flex-wrap: wrap;
    -ms-flex-direction: row;

    .movie {
        max-width: 50%;
        flex: 1 1 50%;
        padding: 16px 8px;
        .movie-link {
          display: flex;
          flex-direction: column;
          height: 100%;
          .product-image {
            display: block;
            img {
              display: block;
              width: 100%;
              height: 275px;
              object-fit: cover;
            }
            .type {
              position: absolute;
              padding: 8px 16px;
              color: white;
              bottom: 16px;
              left: 0px;
              text-transform: capitalize;
            }
          }
          .detail {
            background-color: blueviolet ;
            padding: 16px 8px;
            flex: 1 1 100%;
            border-radius: 0px 0px 8px 8px;
          }
          .year {
            color: white;
            font-size: 14px;
          }
          h3 {
            color: white;
            font-weight: 600;
            font-size: 18px;
          }
        }
      }
    }

  .feature-card {
    img {
      width: 50%px;
      display: block;
      object-fit: cover;
      border-radius: 50px;
      margin: 20px;
    }
  }
  .top-bar {
   display: flex;
   flex-direction: row;
  .review-content {
    display: flex;
    flex-direction: row;
    .review {
    height: 60px;
    font-size: 18px;
    align-items: right;
    margin: 10px;
    color: white;
    border: none;
    outline: none;   
    border-radius: 30px;
    background-color: rgb(65, 92, 65);
     box-shadow: 0 10px 10px -8px #efedec;
    }
  }
  .search-box {
   padding: 20px;
    display: flex;
    flex-direction: row;
     input {
    outline: none;   
    border-radius: 30px;
     &[type="text"]{
          width: 300px;
          height: 25px;
          color:black;
          background-color: #efedec;
          font-size: 15px;
          padding: 10px 16px;
          border-radius: 8px;
          margin-bottom: 15px;
          transition: 0.4s;
     }
     &[type="submit"]{
            width: 100px;
                      height: 50px;

            background-color: red;
            padding: 16px;
            border-radius: 8px;
            color: white;
            font-size: 15px;
            text-transform: uppercase;
            transition: 0.4s;
            
          }
     }
 }
 }
  
  }


</style>