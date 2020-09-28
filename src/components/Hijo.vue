<template>
<div class="container">
    <img src="src/img/poke.jpg" alt="">
    <h1>Pokeguia</h1>
    <form action="">

        <label for="">Ingresa Nombre Pokemón</label>
        <input type="text" v-model="pokemon.name">
        <input type="submit" value="buscar" @click.prevent="fetchCharacter"> 
        
        <img :src="image" alt="">
        <h2 :src="nombre"></h2>
        <h2>movimientos</h2>
        <ul>
        <li v-for="(move, index) in movimientos" :key="index">{{move.move.name}}</li>
        </ul>
        <h2>habilidades</h2>
        <ul>
        <li v-for="(habilidad, index) in habilidades" :key="index">{{habilidad.ability.name}}</li>
        </ul>


    </form>
</div>
</template>

<script>

export default {
    name: 'hijo-component',
    // props: {},
    data: function(){
        return {
            pokemon: {
                name: "pikachu",
                sprites: {
                    front_default: ""
                },
                movimientos: [],
                abilities: []
        },
        };
    },
    computed: {
        image() {
            return this.pokemon.sprites.front_default;
        },
        nombre(){
            return this.pokemon.name;
        },
        habilidades(){
            return this.pokemon.abilities;
        },
        movimientos(){
            return this.pokemon.moves;
        }
    },

  
  
    methods: {
        fetchCharacter(){
            fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemon.name}`)
            .then(response => response.json())
            .then(json => {
                this.pokemon = json;
                console.log(json);
            })
            .catch (error => (
                console.log(error)
            ))
        }
    },
    // components: {},
      created(){
        this.fetchpokemon();
    },
}
</script>

<style scoped>
    body{
        margin: 0%;
        width: 10%;
    }
    .container{
        margin: 30px;
        width: 430px;
        
    }
    img{
        width: 350px;
        display: flex;
    }

</style>