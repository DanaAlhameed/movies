<template>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
<div class="web">
<header>
<router-link to="/">
<h1> Movie <span>Live</span></h1>
<div class="menu">
                <ul>
                   <li> <a href="#"> Movies </a></li>
                    <li><a href="#"> Family </a></li>
                    <li><a href="#"> Kids </a></li>
                    <li><a href="#"> Live </a></li>
                    <li><a href="#"> Shows </a></li>
                </ul>
            </div>
</router-link>
</header>
<main>
  <router-view />
  </main>
  <footer>

<div class="social">
  <a href="#" class="fa fa-facebook"></a>
  <a href="#" class="fa fa-twitter"></a>
  <a href="#" class="fa fa-linkedin"></a>
  <a href="#" class="fa fa-youtube"></a>
  <a href="#" class="fa fa-instagram"></a>
</div>
  </footer>
  </div>
</template>

<style lang="scss">
* {
  .web {
    display: flex;
    flex-direction: row ;
    font-family: 'Fira Sans', sans-serif;
    background-color: #efedec;

    a {
  text-decoration: none;
  color: black;
  font-size: 20px;
  }
   a:hover, a:active {
  background-color: wheat;
  color: red;
   }
   .fa {
  padding: 10px;
  font-size: 30px;
  width: 30px;
  text-align: center;
  text-decoration: none;
  margin: 5px 2px;
}

.fa:hover {
    opacity: 0.7;
}
li {
  list-style: none;
  padding: 10px;
}
h1 {
  color: black;
  span {
    color: red;
  }
}
  }
  header {
    background-color: white;
    .menu {
      color: black;
      width: 100px;
    }
  }
    .contact-bar {
      width: 180px;
      border-radius: 20px; 
      background-color: white;
     img{
      margin: 5px;
     } 
    }

  footer {

    
  }
}
</style>