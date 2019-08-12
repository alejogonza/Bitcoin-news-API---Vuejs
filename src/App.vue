<template>
  <div id="app">
    <br>

     <h1 class="title" style="text-align:center;">News bitcoin app</h1>
    
    <br>

    <div style="text-align:center;">
    
      <button v-on:click="fetch" style="border: none;
    background: none;
"><img src="/static/img/bitcoin.png" style="    width: 90px;
    height: 80px;"></button>
    
   
    </div>
    <br>
     <center>
         <div>
      <p><span data-reactid="59">Made with </span><span style="color: #e31c3f">❤</span><span> for Alejandro Gonzalez Serna</span></p>
          <p>My github <a href="https://github.com/alejogonza" style="color: #e31c3f">alejogonza</a></p>
          </div>
    </center>
<br>
 
<center>
      <div v-for="articles in news" v-bind:key="articles.id" style="text-align:center;margin-left: 210px;">
        <div class="column">
          <h2>{{ articles.title }}</h2>
         
          <img v-bind:src="articles.urlToImage" style="border-radius: 14px;
    box-shadow: 2px 2px 20px 1px #7176d66b;    margin-top: 10px;    margin-bottom: 25px;" />
        <br>
          
    
          
  <a class="button2" v-bind:href="articles.url">See details</a>


        </div>
    </div>

</center>
  </div>


</template>

<script>

import axios from "axios";

export default {
  name: "App",
  data: 
  function() {
    return {
      news: [],
    };
  },
  methods: {
   
    async fetch() {
      try {
        let res = await fetch("https://newsapi.org/v2/everything?q=bitcoin&apiKey=7a337837845c4858a00ebe49ee58a003")
        let data = await res.json()
        this.news = data.articles;
        
      } catch (err) {
        console.log(err);
      }
    }
  }
};


</script>

<style>
.column {
      border-radius: 20px;
    box-shadow: 2px 2px 20px 1px #7176d66b;
    padding: 40px;
  border: solid;
  width: 30%;
  height: 400px;
  margin: 19px;
  float: left;
}

footer{
      position: absolute;
    left: 0;
    bottom: 0;
    width: 100%;
    background-color: #ffffff;
    color: #585f5f;
    box-shadow: 0 0 0 4px #ffffff;
    text-align: center;

}

img {
    width: 255px;
    height: 150px;
}

@media screen and (max-width: 720px) {
  .column {
    border: solid;
    width: 89%;
    height: 400px;
    margin: 5%;
  }
}

body {
      color: #7176D6;
    background: #141534;
    font-family: 'Comfortaa', cursive;
}

.button2{
  text-decoration: none;
      margin-top: 15px;
    border-radius: 11px;
    padding: 10px;
    box-shadow: rgba(113, 118, 214, 0.42) 2px 2px 20px 1px;
    color: white;
    background: #757bec;
    font-family: 'Comfortaa', cursive;
    border-color: #2e307bc4;
    font-size: 15px;
}
</style>
