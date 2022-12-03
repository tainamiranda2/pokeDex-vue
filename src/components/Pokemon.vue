<template>

<div class="card">
  <div class="card-image">
    <figure class="image is-4by3">
      <img src="https://bulma.io/images/placeholders/1280x960.png" alt="Placeholder image">
    </figure>
  </div>
  <div class="card-content">
    <div class="media">
    
      <div class="media-content">
        <p class="title is-4">{{name}}</p>
        <p class="subtitle is-6">{{url}}</p>
      </div>
    </div>
<div class="container"></div>
   
  </div>
</div>
</template>

<script>
import axios from 'axios'
export default {
  created: function(){
    axios.get(this.url).then(res=>{
      this.pokemon.type=res.data.types[0].type.name
      this.pokemon.type=res.data.sprites.front_default
      this.pokemon.type=res.data.sprites.back_default

    })
  },
    data(){
      return{
        pokemon:{}
      }
  },
  props:{
    num:Number,
    name:String,
    url:String
  }
}
</script>
<style scoped>

h1{
  color:blue;
  margin:5px;
}
</style>