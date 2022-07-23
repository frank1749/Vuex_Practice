<template>
  <div class="hello">
    <h1>{{ $store.getters.mensaje }}</h1>
    <h4>{{ $store.getters.nombreCompleto }}</h4>
    <h2>Amigos</h2>
    <input type="text" v-model="amigo">
    <button @click="addAmigo">Agregar</button>

    <ul>
      <li
        v-for="(amigo, index) in $store.state.amigos"
        :key="index">
        {{ amigo }}
        <button @click="$store.dispatch('delAmigoAction', index)">Aliminar</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      amigo: ''
    }
  },
  methods: {
    addAmigo (){
      if(this.amigo == ''){
        return false;
      }
      this.$store.dispatch('addAmigoAction', this.amigo);
      this.amigo = '';
    }
  }
  // props: {
  //   msg: String
  // }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
a {
  color: #42b983;
}
</style>
