<template>

<div class="card">
  <div class="card-image">
    <figure >
      <img :src="currentimg"
       alt="Placeholder image">
    </figure>
  </div>
  <div class="card-content">
    <div class="media">
    
      <div class="media-content">
        <p class="title is-4">{{name}}</p>
        <p class="subtitle is-6">{{pokemon.type}}</p>
      </div>
    </div>
<div class="container">
<button class="button is-medium is-fullwidth" 
@click="mudarSprint">
Mudar sprite
</button>
</div>
   
  </div>
</div>
</template>

<script>
import axios from 'axios'
export default {
  created: function(){
    axios.get(this.url).then(res=>{
      this.pokemon.type=res.data.types[0].type.name;
      this.pokemon.front=res.data.sprites.front_default;
      this.pokemon.back=res.data.sprites.back_default;
  //console.log(this.pokemon)
      this.currentimg=this.pokemon.front
    })
  },
    data(){
      return{
        isFront:true,
        currentimg:'',
        pokemon:{
          type:'',
          front:'',
          back:''
        }
      }
  },
  props:{
    num:Number,
    name:String,
    url:String
  },
  methods:{
    mudarSprint: function(){
      if(this.isFront){
        this.isFront=false;
        this.currentimg=this.pokemon.back;
      }else{
        this.isFront=true;
        this.currentimg=this.pokemon.front
      }
    }
  }
}
</script>
<style scoped>

h1{
  color:blue;
  margin:5px;
}
</style>