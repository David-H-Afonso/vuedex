<template>
  <div id="app" :style="{ background: backImg }">
    <PokeHeader></PokeHeader>
    <div id="pokedex-content">
    <section class="app-pokemon-main card">
      <img alt="pokemon" :src="image" />
      <p class="pokemon-name">{{ name }}</p>
      <button class="button" @click.prevent="makeRequest">SEARCH</button>
    </section>
    <section class="app-pokemon-stats">
      <poke-stats
        :pokeWeight="weight"
        :pokeHeight="height"
        :pokeType="type"
      ></poke-stats>
      <div class="app-pokemon-stats-abilities card">
        <p id="abilities">ABILITIES</p>
        <ul>
          <li
            v-for="el in abilities"
            :key="el"
            style="text-transform: capitalize"
          >
            {{ el.ability.name }}
          </li>
        </ul>
      </div>
    </section>
  </div>  
  <PokeFooter></PokeFooter>
  </div>
</template>

<script>
import PokeStats from "./components/PokeStats.vue";
import PokeHeader from "./components/PokeHeader.vue";
import PokeFooter from "./components/PokeFooter.vue";
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      name: "name",
      image: "",
      type: "",
      weight: 0,
      height: 0,
      abilities: [],
      data: {},
    };
  },
  computed: {
    backImg: function () {
      return `var(--${this.type}-back)`;
    },
  },
  components: {
    PokeStats,
    PokeHeader,
    PokeFooter
  },
  methods: {
    async makeRequest() {
      let randomSearch = await Math.floor(Math.random() * 807 + 1);
      try {
        const response = await axios.get(
          `https://pokeapi.co/api/v2/pokemon/${randomSearch}`
        );
        const data = response.data;
        this.name = data.name;
        this.weight = data.weight;
        this.height = data.height;
        this.abilities = data.abilities;
        this.image = data.sprites.front_default;
        this.type = data.types[0].type.name;
        return response;
      } catch (error) {
        console.log(error);
      }
    },
  },
  async created() {
    await this.makeRequest();
  },
};
</script>

<style scooped>
@import url("https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap");
* {
  font-family: "Press Start 2P", cursive;
}
:root {
  border: 0;
  --general-card-background: white;
  --normal-image-height: 50vh;
  --general-font-size: 2em;
  --grass-back: #2dcd45;
  --fire-back: #f08030;
  --water-back: #149eff;
  --bug-back: #a8b820;
  --normal-back: #a8a878;
  --ground-back: #e0c068;
  --poison-back: #883688;
  --electric-back: #f8d030;
  --flying-back: #a890f0;
  --fairy-back: #ee99ac;
  --fighting-back: #94352d;
  --psychic-back: #ff6996;
  --rock-back: #b8a038;
  --steel-back: #b8b8d0;
  --ice-back: #98d8d8;
  --ghost-back: #614c83;
  --dragon-back: #700aee;
  --dark-back: #705848;
}

#pokedex-content {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 78vh;
  display: grid;
  grid-template-columns: 2fr 1fr;
  text-align: center;
  color: #2c3e50;
}

img {
  height: var(--normal-image-height);
}

button {
  margin-top: 20px;
  color: #ffffff;
  width: 110px;
  height: 40px;
  outline: none;
  cursor: pointer;
  background-color: #0e8dbc;
  transition: 50ms;
}

.button:active {
  transform: scale(1.1, 1.1);
  color: #ffffff;
  text-shadow: 4px 3px 0px #084961;;
}

p {
  font-size: var(--general-font-size);
  margin: 2%;
}

.pokemon-name {
  text-transform: capitalize;
  background-color: white;
  width: 380px;
  height: 80px;
  padding-top: 20px;
  -webkit-box-shadow: 5px 5px 0px 0px #289fed, 10px 10px 0px 0px #5fb8ff,
    15px 15px 0px 0px #a1d8ff, 20px 20px 0px 0px #cae6ff,
    25px 25px 0px 0px #e1eeff, 5px 5px 15px 5px rgba(0, 0, 0, 0);
  box-shadow: 5px 5px 0px 0px #289fed, 10px 10px 0px 0px #5fb8ff,
    15px 15px 0px 0px #a1d8ff, 20px 20px 0px 0px #cae6ff,
    25px 25px 0px 0px #e1eeff, 5px 5px 15px 5px rgba(0, 0, 0, 0);
}
.app-pokemon-main.card {
  margin-top: -3px;
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.app-pokemon-stats {
  display: flex;
  align-items: center;
  justify-content: space-around;
  flex-direction: column;
}

.app-pokemon-stats-abilities.card {
  background-color: var(--general-card-background);
  width: 350px;
  height: 150px;
  display: flex;
  text-align: left;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  -webkit-box-shadow: 5px 5px 0px 0px #289fed, 10px 10px 0px 0px #5fb8ff,
    15px 15px 0px 0px #a1d8ff, 20px 20px 0px 0px #cae6ff,
    25px 25px 0px 0px #e1eeff, 5px 5px 15px 5px rgba(0, 0, 0, 0);
  box-shadow: 5px 5px 0px 0px #289fed, 10px 10px 0px 0px #5fb8ff,
    15px 15px 0px 0px #a1d8ff, 20px 20px 0px 0px #cae6ff,
    25px 25px 0px 0px #e1eeff, 5px 5px 15px 5px rgba(0, 0, 0, 0);
}
</style>
