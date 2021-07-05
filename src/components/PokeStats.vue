<template>
  <div class="component">
    <table class="stats-table">
      <tr>
        <th>HEIGHT</th>
        <th>WEIGHT</th>
        <th>MAIN TYPE</th>
      </tr>
      <tr>
        <td id="height">{{ pokeHeight / 10 }}m</td>
        <td id="weight">{{ pokeWeight / 10 }}kg</td>
        <td id="type">{{ pokeType }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "PokeStats",
  props: {
    pokeWeight: Number,
    pokeHeight: Number,
    pokeType: String,
    pokeType2: String,
  },
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.stats-table {
  background: white;
  font-size: 13px;
  width: 350px;
  height: 60px;
    -webkit-box-shadow: 5px 5px 0px 0px #289fed, 10px 10px 0px 0px #5fb8ff,
    15px 15px 0px 0px #a1d8ff, 20px 20px 0px 0px #cae6ff,
    25px 25px 0px 0px #e1eeff, 5px 5px 15px 5px rgba(0, 0, 0, 0);
  box-shadow: 5px 5px 0px 0px #289fed, 10px 10px 0px 0px #5fb8ff,
    15px 15px 0px 0px #a1d8ff, 20px 20px 0px 0px #cae6ff,
    25px 25px 0px 0px #e1eeff, 5px 5px 15px 5px rgba(0, 0, 0, 0);
}
</style>
