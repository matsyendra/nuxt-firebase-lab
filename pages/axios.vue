<template>
  <ul>
    <li v-for="(usuario, key) in usuarios" :key="key">
      <div>{{ usuario.displayName }} {{ usuario.phone }}</div>
      {{key}}
      <ol>
        <li v-for="(viaje, key, i) in usuario.viajes" :key="key">
          <div>viaje.km_sal: {{viaje.km_sal}}</div>
          <div>key: {{key}}, i:{{i}}</div>
        </li>
      </ol>
    </li>
  </ul>
</template>

<script>
import fetch from 'isomorphic-fetch';
import axios from 'axios';
export default {
  async asyncData() {
    const response = await axios.get(
      "https://milab-519f4.firebaseapp.com/usuarios.json"
    );
    console.log(response.data);
    return {usuarios: response.data}
  }
};
</script>

<style scoped>
</style>

