<template>
  <div id="app">
      
    <div class="card">
      <div class="hero-text"></div>
      <div class="flex-icons">
      
        
      </div>

      
    </div>
      <h1>{{name}}</h1>  
        <div class="image-wrapper">
          <img src="./assets/aveion.jpg" alt="">
        </div>
          <ul >
            <li> <a :href="`https://twitter.com/${twitter}`"><i class="fab fa-twitter-square"></i></a></li>
            <li><a :href="`https://www.instagram.com/${instagram}`"><i class="fab fa-instagram-square"></i></a></li>
            <li><a :href="`https://www.snapchat.com/${snapchat}`"><i class="fab fa-snapchat-square"></i></a></li>
            <li><a :href="`mailto:${email}`" ><i class="fa fa-envelope" aria-hidden="true"></i></a></li>
          </ul>
         

      <div class="links">
        <a href="*">HOME</a>
        <a href="*">ABOUT</a>
        <a href="*"> <img src="./assets/aquila.jpg" alt=""></a>
        <a href="*">GALLERY</a>
        <a href="*">CONTACT</a>
      </div>
    </div>
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import axios from "axios"

export default {
  name: 'App',
  data (){
    return{
      name:"",
      email:"",
      instagram:"",
      snapchat:"",
      twitter:"",
    }
  },
  methods:{
    async fetchData() {
      try {
        const res = await axios.get("https://hirng-x2021.glitch.me/api");
        console.log(res.data)
        this.name = res.data.name,
        this.email= res.data.social_media.email,
        this.instagram= res.data.social_media.instagram,
        this.snapchat= res.data.social_media.snapchat,
        this.twitter= res.data.social_media.twitter
        
      } catch (error) {
        console.log(error);
      }
  }
  },
  created(){
    this.fetchData()
  }
  
}  
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.card{
  display: flex;
  justify-content: space-between;
}
.hero-text{
  background: #ce2c5a;
  padding-top: -2rem;
  width: 50%;
  height: 850px;
}
.flex-icons{
  background: #c74f71;
  width: 50%;
  height: 850px;
  
}

.image-wrapper{
  position: absolute;
  top: 210px;
  left: 410px;
  width: 500px;
  /* box-shadow:  10px 2px 5px  grey; */
  
}
.image-wrapper img{
  width: 100%;
  
}
.links{
  position: absolute;
  top: 760px;
  left: 245px;
}
a img{
  width: 80px;
  border-radius: 50%;
}
a{
  padding: 5px;
  margin: 2.4rem;
  color: white;
  text-decoration: none;
  font-size: 20px;
}
h1{
  text-align: center;
  position: absolute;
  top: 50px;
  left: 500px;
  word-spacing: 1rem;
  font-size: 40px;
  color: rgb(255, 240, 240);
  
}
ul{
  position: absolute;
  right: 30px;
  top: 380px;
  list-style-type: none;
}
ul li{
  padding: 1rem;
}

</style>
