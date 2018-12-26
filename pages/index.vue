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
export default {
  async asyncData() {
    const response = await fetch(
      "https://milab-519f4.firebaseapp.com/usuarios.json"
    );
    const usuarios = await response.json();
    //console.log(usuarios);
    return { usuarios };
  }
};
</script>

<style scoped>
</style>

