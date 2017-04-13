<template>
  <div>
    <h1>{{ titulo }}</h1>
    
      <ul>
        <li v-for="foto of fotos">
          <img :src="foto.url" :alt="foto.titulo">
        </li>
      </ul>
    
  </div>
</template>

<script>
export default {

    data() {
      return {
        fotos: []
      }
    },

    created() {
      let promise = this.$http.get('http://localhost:3000/v1/fotos')
      .then(res => res.json())
      .then(fotos => this.fotos = fotos, err => console.err(err));
    }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
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
</style>
