
<template>
<div class="column is-half is-offset-one-quarter">
  <div v-for="(poke, index) in pokemons" :key="index">
    <Pokemon 
    :name="poke.name" 
    :url="poke.url"
     :num="poke.id"/>
  </div>
</div>
</template>

<script >
import axios from 'axios';
import Pokemon from   './components/Pokemon.vue'

export default{
name: 'App',
data(){
return{
pokemons:[]
}
},

created:function(){

axios.get("https://pokeapi.co/api/v2/pokemon?limit=100&offset=0").then(res=>{

this.pokemons=res.data.results

})

},
components:{
  Pokemon
}

}
</script>


