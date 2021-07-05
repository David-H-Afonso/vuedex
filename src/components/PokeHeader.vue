<template>
    <header class="pokemon-main-title">
      <a href="https://github.com/David-H-Afonso"
        ><img
          class="pokemon-main-title-image"
          src="https://i.imgur.com/scrcyJ3.png"
          alt="Vuedex"
        />
        <p>Vue<span id="another_color">Dex</span></p></a
      >
    </header>
</template>

<script>
export default {
  name: 'PokeHeader',
}
</script>


<style scoped>
    @import url("https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap");

    .pokemon-main-title {
      padding-top: 15px;
      display: flex;
      justify-content: center;
    }
    .pokemon-main-title-image {
      width: 130px;
      height: 100px;
      margin-left: 30px;
    }
    .pokemon-main-title a {
      font-family: "Press Start 2P", cursive;
      text-decoration: none;
      color: #41b883;
    }
    .pokemon-main-title a #another_color {
      color: #34495e;
    }
</style>