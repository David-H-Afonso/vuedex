<template>
  <footer>
    <p>
      Created by David Hormiga Afonso &copy; 2021 - Contacto
      <a rel="noopener" target="_blank" href="https://github.com/David-H-Afonso">GitHub / </a
      ><a rel="noopener" target="_blank" href="https://www.linkedin.com/in/david-hormiga-afonso/">LinkedIn / </a
      ><a rel="noopener" target="_blank" href="https://twitter.com/RikkuESP">Twitter</a>
    </p>
  </footer>
</template>

<script>
export default {
  name: "PokeFooter",
};
</script>

<style scoped>
* {
  padding: 1px;
  padding-left: 0px;
}
footer {
  margin-top: 15px;
}
footer p {
  font-size: 20px;
}
footer a {
  font-size: 15px;
  text-decoration: none;
  color: #ffffff;
}
footer a:hover {
  color: #0e8dbc;
}
</style>
